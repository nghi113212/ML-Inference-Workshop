---
title : "Push ML image to ECR"
date : "2025-07-28" 
weight : 2
chapter : false
pre : " <b> 6.2 </b> "
---

1. Back to **VS Code Editor**
    - Create a new folder name `my-workshop-ecr`
    - Move two **.pkl** files into this folder
    ![](/images/6.ECR/5.png)

2. In **my-workshop-ecr** folder
    - Create file `lambda_function.py` with the content as given:
    ```
    import pickle
    import json
    import botocore.session
    from botocore.model import ServiceId
    from botocore.signers import RequestSigner
    from urllib.parse import urlencode, urlunparse, ParseResult
    import redis

    # ==== Load model và vectorizer (chỉ chạy 1 lần khi cold start) ====
    with open('sentiment_model.pkl', 'rb') as f:
        model = pickle.load(f)

    with open('tfidf_vectorizer.pkl', 'rb') as f:
        vectorizer = pickle.load(f)

    # ==== Generate IAM auth token (function) ====
    def generate_iam_token(username, cache_name, region="us-east-1"):
        session = botocore.session.get_session()
        request_signer = RequestSigner(
            ServiceId("elasticache"),
            region,
            "elasticache",
            "v4",
            session.get_credentials(),
            session.get_component("event_emitter"),
        )

        query_params = {"Action": "connect", "User": username, "ResourceType": "ServerlessCache"}
        url = urlunparse(
            ParseResult(
                scheme="https",
                netloc=cache_name,
                path="/",
                query=urlencode(query_params),
                params="",
                fragment="",
            )
        )

        signed_url = request_signer.generate_presigned_url(
            {"method": "GET", "url": url, "body": {}, "headers": {}, "context": {}},
            operation_name="connect",
            expires_in=900,
            region_name=region,
        )

        return signed_url.removeprefix("https://")

    # ==== Setup Redis client (IAM auth) ====
    username = "iam-user-01"  # Thay bằng IAM user của bạn
    cache_name = "my-workshop-cache"   # Thay bằng cache name
    elasticache_endpoint = "my-workshop-cache-e8trvn.serverless.apse1.cache.amazonaws.com"  # Endpoint cache thực tế
    region = "ap-southeast-1" #Your cache region

    auth_token = generate_iam_token(username, cache_name, region)

    redis_client = redis.Redis(
        host=elasticache_endpoint,
        port=6379,
        username=username,
        password=auth_token,
        ssl=True,
        ssl_cert_reqs="none"
    )

    # ==== Lambda handler ====
    def lambda_handler(event, context):
        try:
            # Parse input
            if 'body' in event:
                body = json.loads(event['body'])
            else:
                body = event

            text = body.get('text')
            if not text:
                return {
                    'statusCode': 400,
                    'body': json.dumps({'error': 'Missing "text" in request'})
                }

            # Check cache first
            cached_value = redis_client.get(text)
            if cached_value:
                prediction, sentiment = json.loads(cached_value)
            else:
                # Predict if not cached
                X_input = vectorizer.transform([text])
                prediction = model.predict(X_input)[0]
                sentiment = "Positive" if prediction == 1 else "Negative"

                # Save to cache
                redis_client.setex(text, 3600, json.dumps((int(prediction), sentiment)))

            # Return result
            return {
                'statusCode': 200,
                'body': json.dumps({
                    'text': text,
                    'prediction': int(prediction),
                    'sentiment': sentiment
                })
            }

        except Exception as e:
            return {
                'statusCode': 500,
                'body': json.dumps({'error': str(e)})
            }

    ```
    - Replace some parameter with your own Info
    - **Watch out:** Remember to **remove** the port number at the end of Cache Endpoint 

![](/images/6.ECR/6.png)

3. In **my-workshop-ecr** folder
    - Create **Dockerfile**
    - With the content as given:
    ```
    FROM public.ecr.aws/lambda/python:3.12

    # Copy code
    COPY lambda_function.py ${LAMBDA_TASK_ROOT}
    COPY sentiment_model.pkl ${LAMBDA_TASK_ROOT}
    COPY tfidf_vectorizer.pkl ${LAMBDA_TASK_ROOT}

    # Install requirements
    RUN pip install scikit-learn --target ${LAMBDA_TASK_ROOT}
    RUN pip install redis --target ${LAMBDA_TASK_ROOT}
    RUN pip install botocore --target ${LAMBDA_TASK_ROOT}
    RUN pip install cachetools --target ${LAMBDA_TASK_ROOT}

    # Command to run Lambda
    CMD ["lambda_function.lambda_handler"]

    ```

4. Now we will use **AWS CLI** to handle this
    - If you don't have AWS CLI you can get back to chapter 2 section 2.4 for installation.
    - Make sure your account has **Access keys**
        - You can create **Access keys** by following these steps:
            - Access **IAM Service**, select **User**, choose **Create access key**

    ![](/images/6.ECR/7.png)
    ![](/images/6.ECR/8.png)
    ![](/images/6.ECR/9.png)

5. In **VS Code Editor**
    - In terminal, type: `cd my-workshop-ecr`
    - Next, type: `aws configure`
    - Type your **Access key**
    ![](/images/6.ECR/10.png)

6. Back to **Elastic Container Registry**
    - Click **my-workshop-ecr**
    ![](/images/6.ECR/11.png)
    - Click **View push command**
    ![](/images/6.ECR/12.png)

7. Start your **docker engine**
    - ![](/images/6.ECR/13.png)

8. Copy the first command and type it in terminal
    ![](/images/6.ECR/14.png)
    ![](/images/6.ECR/15.png)
    - Copy the second command and type it in terminal. **Make sure** your are in the **my-workshop-ecr** directory
    ![](/images/6.ECR/16.png)
    ![](/images/6.ECR/17.png)
    - Type the third command in your terminal
    ![](/images/6.ECR/18.png)
    - Type the fourth command in terminal
    ![](/images/6.ECR/19.png)
    - After finish, go back to **AWS ECR** you will see your images
    ![](/images/6.ECR/20.png)