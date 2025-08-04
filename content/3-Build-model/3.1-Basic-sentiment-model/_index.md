---
title : "Simple sentiment model"
date : "2025-07-28"
weight : 1
chapter : false
pre : " <b> 3.1. </b> "
---

A sentiment model is a type of machine learning model that can analyze a piece of text and determine the sentiment behind it—whether it's **positive**, **negative**, or **neutral**. These models are commonly used in areas like: **Customer feedback analysis**, **Social media monitoring**, **Product review classification**,...

In this section, we will walk through how to collect data, preprocess text, train a machine learning model, and make predictions using Python. By the end of this session, you'll have a working sentiment analysis tool that you can experiment with or even improve further.

---

## Let's get started
#### Create environment for developing model
1. Create a python virtual environment
 - Create a new folder and open it with VS Code then type `python -m venv <name of your virtual env>` in your terminal.
 ![](/images/3.Build-model/3.1-vir-env.png)

 - Create file `create_sentiment_model.py`
 ![](/images/3.Build-model/3.1-py.png)

2. Collect data
 -  In this workshop, instead of collecting raw data manually, we will use a pre-existing dataset for sentiment analysis. For this tutorial, we will use the **IMDb movie review** and **Yelp data reviewer** dataset.
 - **First**, we will activate the virtual environment that was created before, typing `<name of your venv>/Scripts/activate`. 
 ![](/images/3.Build-model/3.1-activate.png)
 - **Next**, install dataset library to use ready-made dataset.
 `pip install datasets`
 ![](/images/3.Build-model/3.1-dataset1.png)
 - Now, let see what inside these datasets. (You do not have to follow this step. This step just aims to let you have a specific look of this library)
 ![](/images/3.Build-model/3.1-dataset-example.png)

 #### Building time
 1. Prepare train data and test data (Because the data in each dataset is quite small so the author decided to combine them together. If your prepared data is big enough, you do not hava to do this)
 ![](/images/3.Build-model/3.1-combine-data.png)

 2. Data preprocessing
- Install scikit-learn library for create model `pip install scikit-learn`
![](/images/3.Build-model/3.1-pre-data.png)
{{%notice note%}}
Purpose of this step:
To convert text data into numerical format using TF-IDF (Term Frequency - Inverse Document Frequency) so that the machine learning model can understand and process the input.
This step helps represent each document as a vector based on the importance of words, making it suitable for training and prediction.
{{%/notice%}}

 3.  Create model
 ![](/images/3.Build-model/3.1-create-model.png)

 4. Evaluate model
 ![](/images/3.Build-model/3.1-evaluate.png)

 5. Save model and vectorizer
 ![](/images/3.Build-model/3.1-save.png)

 - Source code:

    ```
    from datasets import load_dataset

    # Load the datasets 
    imdb_dataset = load_dataset("imdb")
    yelp_dataset = load_dataset("yelp_polarity")

    # Trích xuất dữ liệu train IMDB
    X_imdb_train = imdb_dataset['train']['text'][:]
    y_imdb_train = imdb_dataset['train']['label'][:]

    # Trích xuất dữ liệu train Yelp
    X_yelp_train = yelp_dataset['train']['text'][:]
    y_yelp_train = yelp_dataset['train']['label'][:]

    # Combine train datasets
    X_train = X_imdb_train + X_yelp_train
    y_train = y_imdb_train + y_yelp_train

    # Trích xuất dữ liệu test IMDB
    X_imdb_test = imdb_dataset['test']['text'][:]
    y_imdb_test = imdb_dataset['test']['label'][:]

    # Trích xuất dữ liệu test Yelp
    X_yelp_test = yelp_dataset['test']['text'][:]
    y_yelp_test = yelp_dataset['test']['label'][:]

    # Combine test datasets
    X_test = X_imdb_test + X_yelp_test
    y_test = y_imdb_test + y_yelp_test

    # Tiền xử lý dữ liệu
    from sklearn.feature_extraction.text import TfidfVectorizer
    vectorizer = TfidfVectorizer()
    X_train_tfidf = vectorizer.fit_transform(X_train)
    X_test_tfidf = vectorizer.transform(X_test)

    # Tạo mô hình
    from sklearn.linear_model import LogisticRegression
    model = LogisticRegression()
    model.fit(X_train_tfidf, y_train)

    # Đánh giá mô hình
    from sklearn.metrics import accuracy_score
    y_pred = model.predict(X_test_tfidf)
    accuracy = accuracy_score(y_test, y_pred)
    print(f"Accuracy: {accuracy:.4f}")


    # Lưu model
    import pickle
    with open('sentiment_model.pkl', 'wb') as f:
        pickle.dump(model, f)

    # Save vectorizer
    with open('tfidf_vectorizer.pkl', 'wb') as f:
        pickle.dump(vectorizer, f)

    ```

6. Train the model
    - Run `python create_sentiment_model.py`
    - This step will **take time** due to the strenght of your CPU since scikit-learn don't run in GPU.
    - Result:
        - You will see the accuracy after training
        - Two files `.pkl` were created 

    ![](/images/3.Build-model/3.1-results.png)


#### Congratulation!
You have successfully built a sentiment model with accuracy of 90,7%. Now let's try to optimize it to have a better accuracy.