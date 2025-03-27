
# Phân loại Văn bản Nhị phân - Fine-tuning DistilBERT trên Yelp Polarity

## 1. Giới thiệu
Dự án này fine-tune mô hình DistilBERT để phân loại đánh giá văn bản thành hai lớp: tích cực và tiêu cực. Chúng tôi sử dụng tập con của Yelp Polarity (1,000 mẫu training, 100-500 mẫu test) nhằm giảm thời gian huấn luyện và đánh giá.

## 2. Dữ liệu
- **Dataset**: Yelp Polarity  
  - Đầy đủ: 560,000 mẫu training, 38,000 mẫu test  
  - Dự án sử dụng: 1,000 mẫu training và 100-500 mẫu test

## 3. Mô hình và Cấu hình Huấn luyện
- **Mô hình cơ sở**: DistilBERT (uncased)  
- **Tokenizer**: DistilBertTokenizer  
- **Tham số huấn luyện**:
  - Learning rate: 2e-5
  - Batch size: 16
  - Epochs: 1
  - Weight decay: 0.01

## 4. Fine-tuning & Đánh giá
- Fine-tuning được thực hiện với Hugging Face Trainer.
- Kết quả đánh giá (trên 100 mẫu test):  
  - Accuracy: 0.86  
  - Các chỉ số khác: Precision ~0.91, Recall ~0.81, F1-Score ~0.86  
- Hiển thị ma trận nhầm lẫn và báo cáo các chỉ số đánh giá.

## 5. Lưu mô hình & Hàm Dự đoán
- Mô hình và tokenizer đã được lưu lại để sử dụng cho dự đoán sau này.
- Hàm `predict_sentiment(text)` được định nghĩa để dự đoán cảm xúc (Positive/Negative) của văn bản mới.

## 6. Giao diện Demo với Gradio
- Sử dụng Gradio để tạo giao diện demo cho dự đoán cảm xúc.
- Người dùng nhập đánh giá và nhận kết quả dự đoán ngay lập tức.
- Demo chạy trên Colab với chia sẻ công khai qua Gradio.

## 7. Hướng dẫn Chạy Dự án
1. Cài đặt thư viện cần thiết:
   ```bash
   pip install transformers datasets torch gradio
   ```
2. Tải mô hình DistilBERT và Yelp Polarity dataset.
3. Tiền xử lý dữ liệu và tokenization.
4. Fine-tune mô hình với Trainer trên tập con dữ liệu.
5. Đánh giá mô hình và lưu mô hình cùng tokenizer.
6. Dùng hàm `predict_sentiment(text)` để dự đoán văn bản mới.
7. Chạy giao diện demo với Gradio.

## 8. Tài liệu Tham khảo
- [Transformers Documentation](https://huggingface.co/transformers/)
- [Yelp Polarity Dataset](https://huggingface.co/datasets/yelp_polarity)
- [Gradio Documentation](https://gradio.app/)

## 9. Liên hệ
Nếu có bất kỳ thắc mắc hoặc góp ý, vui lòng mở issue trên GitHub hoặc liên hệ qua email: thanh.van19062004@gmail.com
```

---


