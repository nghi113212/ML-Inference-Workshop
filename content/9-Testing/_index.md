---
title : "Testing"
date : "2025-07-28" 
weight : 9
chapter : false
pre : " <b> 9. </b> "
---

#### Test with Postman
1. Open Postman
    - If you don’t have Postman you can get back to chapter 2 section 2.2 for installation.
    - Create your own workspace
    ![](/images/9.Testing/1.png)
2. In Postman
    - Click **+**, for creating new request
    ![](/images/9.Testing/2.png)
    - Select **POST**
    - Paste the **Invoke URL** next to it and add `/predict` at the end of the URL
    ![](/images/9.Testing/3.png)
    - Choose **Body** Tab (under the URL)
    - Next, choose **raw** 
    - Then type:
    ```
    {
        "text": "This movie is awsome"
    }
    ```
    ![](/images/9.Testing/4.png)
    - Click **Send** and view the result
    ![](/images/9.Testing/5.png)

#### Test with Locust
<!-- For more information about this tool, you can access this site: https://locust.io/ -->
3. Back to VS Code Editor
    - Install Locust library `pip install locust`
    - Create a new file name `locust.py` with the content as given:
    ```
    from locust import HttpUser, task, between
    import json
    import random

    class SentimentLoadTest(HttpUser):
        wait_time = between(0, 1)  # mỗi user gửi request sau 1-2s

        @task
        def test_sentiment_api(self):
            # Data mẫu, chỉnh theo input model của bạn
            example_texts = [
                "I love this product!",
                "This is terrible, I hate it.",
                "It's okay, not too bad but not great.",
                "Absolutely wonderful experience.",
                "Worst purchase ever made.",
                "I'm very happy with my purchase.",
                "The service was horrible.",
                "I will definitely buy this again.",
                "I regret buying this.",
                "This made my day so much better.",
                "The quality is disappointing.",
                "I feel amazing after using this.",
                "Never buying from here again.",
                "This is just perfect for my needs.",
                "It doesn't work as expected.",
                "Highly recommend this to everyone.",
                "Such a waste of money.",
                "It's fine, does the job.",
                "Exceeded my expectations.",
                "I want a refund immediately.",
                "Fantastic experience overall.",
                "Completely useless product.",
                "Satisfied with what I got.",
                "Terrible customer service.",
                "Superb quality and fast delivery.",
                "Not worth the price at all.",
                "Works like a charm!",
                "Disappointed with this purchase.",
                "Everything was great.",
                "The item arrived broken.",
                "Loved it so much!",
                "Poor packaging and bad quality.",
                "I am so pleased with this.",
                "Doesn't match the description.",
                "Exactly what I was looking for.",
                "Extremely dissatisfied.",
                "Couldn't be happier.",
                "I hate it so much.",
                "This is awesome!",
                "Worst experience ever.",
                "Very good product for the price.",
                "It broke after one use.",
                "This is my favorite purchase.",
                "Very low quality material.",
                "Best thing I've bought this year.",
                "Completely not what I expected.",
                "I'm extremely happy with it.",
                "Such an awful experience.",
                "Five stars from me.",
                "Would not recommend to anyone.",
                "It works perfectly.",
                "Terrible choice I made.",
                "Beyond my expectations.",
                "Do not waste your money.",
                "This is the best!",
                "I'm so mad about this.",
                "Loved everything about it.",
                "I wish I never bought this.",
                "Absolutely loved it.",
                "Broke within days.",
                "I'm very satisfied.",
                "Worst product on the market.",
                "Super happy with my purchase.",
                "I can't stand this product.",
                "Will buy again for sure.",
                "Not as described at all.",
                "Amazing quality and service.",
                "Terribly disappointed.",
                "Very impressed with this.",
                "Save your money for something better.",
                "This made me so happy.",
                "It's a complete disaster.",
                "I really like this product.",
                "I don't recommend this.",
                "It feels amazing to use.",
                "Completely failed my expectations.",
                "I would buy it again.",
                "Horrible experience overall.",
                "Works as advertised.",
                "Do not buy this.",
                "It makes me feel great.",
                "I'm never using this again.",
                "Best purchase I've made recently.",
                "Worst customer experience ever.",
                "It does what it says.",
                "Absolutely not worth it.",
                "I'm so glad I bought this.",
                "This is the worst thing ever.",
                "It's exactly as shown.",
                "Disgusting product.",
                "Very happy with my order.",
                "I am so disappointed.",
                "This is fantastic.",
                "Terrible, just terrible.",
                "It's brilliant.",
                "Does not work at all.",
                "Such great value for money.",
                "Awful quality.",
                "Perfect in every way.",
                "Completely unusable."
            ]

            input_text = random.choice(example_texts)

            payload = {
                "text": input_text  # thay đổi key này nếu API của bạn cần key khác
            }

            headers = {
                "Content-Type": "application/json"
            }

            with self.client.post("/predict", data=json.dumps(payload), headers=headers, catch_response=True) as response:
                if response.status_code == 200:
                    response.success()
                else:
                    response.failure(f"Failed with status code {response.status_code}, body: {response.text}")
    ```
    ![](/images/9.Testing/6.png)

    - Run `locust -f locust.py --host <Your Invoke URL>`
    ![](/images/9.Testing/7.png)
    - Open your browser access `http://localhost:8089/`
    - For **number of user** enter the number you want
    - For **Ramp up** enter `1`
    - Click **START**
    ![](/images/9.Testing/8.png)
    - Wait one minute then click **STOP**
    - Result:
    ![](/images/9.Testing/9.png)
    - Most satisfies the requirement (<100ms). However, with **99%ile** is 130ms so it is not satisfy the requirement (<100ms)

10. Click **CHARTS** Tab to see specifically
    ![](/images/9.Testing/10.png)
