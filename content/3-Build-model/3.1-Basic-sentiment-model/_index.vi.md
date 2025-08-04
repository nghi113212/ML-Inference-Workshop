---
title : "Mô hình cảm xúc đơn giản"
date : "2025-07-28" 
weight : 1 
chapter : false
pre : " <b> 3.1. </b> "
---

Mô hình cảm xúc (sentiment model) là một loại mô hình học máy có thể phân tích một đoạn văn bản và xác định cảm xúc đằng sau nó—liệu nó là **tích cực**, **tiêu cực**, hay **trung tính**. Những mô hình này thường được sử dụng trong các lĩnh vực như: **Phân tích phản hồi khách hàng**, **Giám sát mạng xã hội**, **Phân loại đánh giá sản phẩm**,...

Trong phần này, chúng ta sẽ đi qua cách thu thập dữ liệu, tiền xử lý văn bản, huấn luyện mô hình học máy, và đưa ra dự đoán bằng Python. Cuối phiên này, bạn sẽ có một công cụ phân tích cảm xúc hoạt động mà bạn có thể thử nghiệm hoặc thậm chí cải thiện thêm.

---

## Hãy bắt đầu
#### Tạo môi trường để phát triển mô hình
1. Tạo môi trường ảo python
 - Tạo một thư mục mới và mở nó bằng VS Code rồi gõ `python -m venv <tên của môi trường ảo>` trong terminal.
 ![](/images/3.Build-model/3.1-vir-env.png)

 - Tạo file `create_sentiment_model.py`
 ![](/images/3.Build-model/3.1-py.png)

2. Thu thập dữ liệu
 -  Trong workshop này, thay vì thu thập dữ liệu thô thủ công, chúng ta sẽ sử dụng một bộ dữ liệu có sẵn để phân tích cảm xúc. Trong hướng dẫn này, chúng ta sẽ sử dụng bộ dữ liệu **đánh giá phim IMDb** và **dữ liệu đánh giá Yelp**.
 - **Đầu tiên**, chúng ta sẽ kích hoạt môi trường ảo đã tạo trước đó, gõ `<tên của venv>/Scripts/activate`. 
 ![](/images/3.Build-model/3.1-activate.png)
 - **Tiếp theo**, cài đặt thư viện dataset để sử dụng bộ dữ liệu có sẵn.
 `pip install datasets`
 ![](/images/3.Build-model/3.1-dataset1.png)
 - Bây giờ, hãy xem có gì bên trong những bộ dữ liệu này. (Bạn không cần phải làm theo bước này. Bước này chỉ nhằm mục đích để bạn có cái nhìn cụ thể về thư viện này)
 ![](/images/3.Build-model/3.1-dataset-example.png)

 #### Bắt đầu xây dựng
 1. Chuẩn bị dữ liệu huấn luyện và dữ liệu kiểm tra (Vì dữ liệu trong mỗi bộ dữ liệu khá nhỏ nên tác giả quyết định kết hợp chúng lại với nhau. Nếu dữ liệu chuẩn bị của bạn đủ lớn, bạn không cần phải làm như vậy)
 ![](/images/3.Build-model/3.1-combine-data.png)

 2. Tiền xử lý dữ liệu
- Cài đặt thư viện scikit-learn để tạo mô hình `pip install scikit-learn`
 ![](/images/3.Build-model/3.1-pre-data.png)
{{%notice note%}}
Mục đích của bước này:
Chuyển đổi dữ liệu văn bản thành định dạng số bằng TF-IDF (Term Frequency - Inverse Document Frequency) để mô hình học máy có thể hiểu và xử lý đầu vào.
Bước này giúp biểu diễn mỗi tài liệu dưới dạng vector dựa trên tầm quan trọng của từ, làm cho nó phù hợp cho việc huấn luyện và dự đoán.
{{%/notice%}}

 3. Tạo mô hình
 ![](/images/3.Build-model/3.1-create-model.png)

 4. Đánh giá mô hình
 ![](/images/3.Build-model/3.1-evaluate.png)

 5. Lưu mô hình và vectorizer
 ![](/images/3.Build-model/3.1-save.png)

 - Mã nguồn:

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

6. Huấn luyện mô hình
    - Chạy lệnh `python create_sentiment_model.py`
    - Bước này sẽ **mất thời gian** do nó dựa vào sức mạnh CPU của bạn vì scikit-learn không chạy trên GPU.
    - Kết quả:
        - Bạn sẽ thấy độ chính xác sau khi huấn luyện
        - Hai file `.pkl` được tạo 

    ![](/images/3.Build-model/3.1-results.png)


#### Chúc mừng!
Bạn đã xây dựng thành công một mô hình cảm xúc với độ chính xác 90,7%. Bây giờ hãy thử tối ưu hóa nó để có độ chính xác tốt hơn.

