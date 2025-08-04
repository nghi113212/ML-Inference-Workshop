---
title : "Optimize and test model"
date : "2025-07-28"
weight : 2
chapter : false
pre : " <b> 3.2. </b> "
---
### Optimization
1. Parameter tuning/optimization for vectorizer
    - In file **create_sentiment_model.py** add to `TfidfVectorizer()` some parameters shown as follow: 
    ```
    vectorizer = TfidfVectorizer(
        stop_words='english', 
        ngram_range=(1,2),
        max_features=80000,
        max_df=0.9, 
        min_df=2 
    )
    ```
    Meaning:
    - **stop_words='english'** - Remove English stop words (the, and, is, in, ...)
    - **ngram_range=(1,2)** - Use both unigrams (single words) and bigrams (2-word phrases)
    - **max_features=80000** - Limit to keep only the 80,000 most important features
    - **max_df=0.9** - Remove words that appear in >90% of documents (too common)
    - **min_df=2** - Remove words that appear in <2 documents (too rare)

    ![](/images/3.Build-model/3.2-optimize-vector.png)

2. Optimizing LogisticRegression model parameters
    - In file **create_sentiment_model.py** add to `LogisticRegression()` some parameters shown as follow:
    ```
    model = LogisticRegression(
        max_iter=250,
        C=2.0,                
        solver='saga'
    )
    ```
    Meaning: 
    - **max_iter=250**: Maximum number of iterations for algorithm convergence (default is usually 100) - Increased to ensure model has enough time to learn all data
    - **C=2.0**: Regularization parameter - Allows model to "learn" more details from the data
    - **solver='saga'**: Optimization algorithm - Good support for L1, L2 and Elastic Net regularization

    ![](/images/3.Build-model/3.2-optimize-model.png)

3. Pre-train the model to see the new accuracy
    - Run `python create_sentiment_model.py`
    - This will take time just wait!
    - Result: 

    ![](/images/3.Build-model/3.2-pretrain.png)
Congratulation! You have successfully optimize model from **90,7%** to **91,3%** of accuracy.
{{%notice note%}}
You can **change value of those parameters above** or **add some parameters** yourself to see the differences
{{%/notice%}}

### Test the model
1. Create file `test.py` in the same directory

2. Using this code to test that model can predict a sentence if it is negative or positive
    ```
    import pickle

    # Load model và vectorizer
    with open('sentiment_model.pkl', 'rb') as f:
        model = pickle.load(f)
    with open('tfidf_vectorizer.pkl', 'rb') as f:
        vectorizer = pickle.load(f)

    # Hàm dự đoán sentiment
    def predict_sentiment(text):
        vec = vectorizer.transform([text])
        pred = model.predict(vec)[0]
        return "Positive" if pred == 1 else "Negative"

    # Test
    print(predict_sentiment("I love this movie, it was fantastic!"))
    ```
    - Run `python test.py`

    ![](/images/3.Build-model/3.2-test.png)

    - Let's try a negative sentence

    ![](/images/3.Build-model/3.2-test2.png)

    So we have completed the first step of our topic is to have a inference model. Now, let's move to the next step of our project.