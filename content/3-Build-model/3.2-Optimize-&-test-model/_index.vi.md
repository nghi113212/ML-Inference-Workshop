---
title : "Tối ưu và kiểm thử mô hình"
date : "2025-07-28" 
weight : 2 
chapter : false
pre : " <b> 3.2. </b> "
---

### Tối ưu hóa
1. Tinh chỉnh/tối ưu hóa tham số cho vectorizer
    - Trong file **create_sentiment_model.py** thêm vào `TfidfVectorizer()` một số tham số như sau: 
    ```
    vectorizer = TfidfVectorizer(
        stop_words='english', 
        ngram_range=(1,2),
        max_features=80000,
        max_df=0.9, 
        min_df=2 
    )
    ```
    Ý nghĩa:
    - **stop_words='english'** - Loại bỏ các từ dừng tiếng Anh (the, and, is, in, ...)
    - **ngram_range=(1,2)** - Sử dụng cả từ đơn (unigrams) và cụm từ 2 từ (bigrams)
    - **max_features=80000** - Giới hạn chỉ giữ lại 80,000 đặc trưng quan trọng nhất
    - **max_df=0.9** - Loại bỏ từ xuất hiện trong >90% tài liệu (quá phổ biến)
    - **min_df=2** - Loại bỏ từ xuất hiện trong <2 tài liệu (quá hiếm)

    ![](/images/3.Build-model/3.2-optimize-vector.png)

2. Tối ưu hóa tham số mô hình LogisticRegression
    - Trong file **create_sentiment_model.py** thêm vào `LogisticRegression()` một số tham số như sau:
    ```
    model = LogisticRegression(
        max_iter=250,
        C=2.0,                
        solver='saga'
    )
    ```
    Ý nghĩa: 
    - **max_iter=250**: Số lần lặp tối đa để thuật toán hội tụ (mặc định thường là 100) - Tăng lên để đảm bảo mô hình có đủ thời gian học hết dữ liệu
    - **C=2.0**: Tham số regularization - Cho phép mô hình "học" nhiều chi tiết hơn từ dữ liệu
    - **solver='saga'**: Thuật toán tối ưu hóa - Hỗ trợ tốt cho L1, L2 và Elastic Net regularization

    ![](/images/3.Build-model/3.2-optimize-model.png)

3. Huấn luyện lại mô hình để xem độ chính xác mới
    - Chạy `python create_sentiment_model.py`
    - Điều này sẽ mất thời gian, hãy đợi!
    - Kết quả: 

    ![](/images/3.Build-model/3.2-pretrain.png)
Chúc mừng! Bạn đã tối ưu hóa thành công mô hình từ **90,7%** lên **91,3%** độ chính xác.
{{%notice note%}}
Bạn có thể **thay đổi giá trị của những tham số trên** hoặc **thêm một số tham số** khác để xem sự khác biệt
{{%/notice%}}

### Kiểm thử mô hình
1. Tạo file `test.py` trong cùng thư mục

2. Sử dụng đoạn code này để kiểm tra mô hình có thể dự đoán một câu là tiêu cực hay tích cực
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
    - Chạy `python test.py`

    ![](/images/3.Build-model/3.2-test.png)

    - Hãy thử một câu tiêu cực

    ![](/images/3.Build-model/3.2-test2.png)

    Vậy là chúng ta đã hoàn thành bước đầu tiên của chủ đề là có một mô hình suy luận. Bây giờ, hãy chuyển sang bước tiếp theo của dự án.

