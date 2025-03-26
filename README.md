
# Dự án Phân loại Rủi ro Tín dụng (German Credit Data)

## 1. Giới thiệu
Dự án này nhằm xây dựng các mô hình phân loại rủi ro tín dụng dựa trên bộ dữ liệu German Credit. Mục tiêu là dự đoán khả năng rủi ro của khách hàng (Risk) dựa trên các thông tin về giới tính, tuổi, tình trạng tài chính và các đặc trưng liên quan khác. Qua đó, chúng ta đánh giá hiệu năng của nhiều mô hình (Logistic Regression, Decision Tree, Random Forest, XGBoost, SVM) trên tập dữ liệu này.

## 2. Dữ liệu
- **Dataset**: `german_credit_data.csv`
- **Thông tin chính**:
  - Các biến đầu vào: `Sex`, `Housing`, `Saving accounts`, `Checking account`, `Purpose`, v.v.
  - Biến mục tiêu: `Risk` (0: khách hàng ít rủi ro, 1: khách hàng có rủi ro)
- **Tiền xử lý**:
  - Loại bỏ cột không cần thiết (ví dụ: `Unnamed: 0`).
  - Xử lý giá trị thiếu: Điền "unknown" cho các cột `Saving accounts` và `Checking account`.
  - Mã hóa biến phân loại bằng LabelEncoder.
  - Tách dữ liệu thành tập huấn luyện (80%) và tập kiểm tra (20%), đảm bảo phân bố lớp (stratify theo `Risk`).
  - Chuẩn hóa dữ liệu bằng StandardScaler.

## 3. Huấn luyện Mô hình
Các mô hình được huấn luyện bao gồm:
- **Logistic Regression**
- **Decision Tree**
- **Random Forest**
- **XGBoost**
- **SVM**

Các mô hình Logistic Regression và SVM được huấn luyện trên dữ liệu đã chuẩn hóa, trong khi các mô hình còn lại sử dụng dữ liệu gốc. Mỗi mô hình được huấn luyện và lưu lại sau đó.

## 4. Đánh giá Mô hình
- **Các chỉ số đánh giá**: Precision, Recall, F1-score, ROC AUC.
- **Ma trận nhầm lẫn** được vẽ cho từng mô hình (sử dụng seaborn heatmap) với nhãn "Bad" và "Good".
- **So sánh hiệu năng**:  
  Ví dụ, Random Forest cho kết quả cân bằng (precision, recall > 0.8, AUC khoảng 0.78) trong khi XGBoost ưu tiên recall với AUC tốt (ví dụ, recall ≈ 0.88, AUC ≈ 0.83). SVM mặc dù có AUC rất cao nhưng recall thấp.
- Các kết quả đánh giá được in ra bằng bảng (sử dụng tabulate) và biểu đồ cột trực quan so sánh hiệu suất giữa các mô hình.

## 5. Kết quả và Nhận xét
- **Nhận xét chung**:
  - Logistic Regression báo quá nhiều false positives.
  - Decision Tree cho hiệu suất không ổn định với AUC thấp.
  - Random Forest được đánh giá là ổn định, dễ giải thích.
  - XGBoost có recall và AUC tốt, phát hiện tốt khách hàng rủi ro nhưng có thể báo nhầm nhiều.
  - SVM có AUC cao nhưng bỏ sót khách hàng rủi ro.
- **Kết luận**:
  - Nếu ưu tiên giảm thiểu rủi ro (không bỏ sót khách hàng rủi ro), XGBoost là lựa chọn tốt.
  - Nếu cần mô hình ổn định và dễ giải thích, Random Forest là lựa chọn an toàn.

## 6. Hướng dẫn Chạy Dự án
1. **Clone Repository**:
   ```bash
   git clone https://github.com/your_username/credit-loans-classification.git
   cd credit-loans-classification
   ```
2. **Cập nhật Đường dẫn**:  
   Đảm bảo đường dẫn đến file `german_credit_data.csv` trong code đã được chỉnh sửa đúng.
3. **Chạy Notebook**:  
   Mở file notebook (ví dụ: `credit_loans_classification.ipynb`) trong Google Colab hoặc Jupyter Notebook và chạy toàn bộ pipeline từ xử lý dữ liệu đến đánh giá mô hình.

## 7. Kết quả Trực quan
- **Ma trận nhầm lẫn**: Heatmap cho từng mô hình cho biết số dự đoán đúng và sai.
- **Biểu đồ so sánh**: Biểu đồ cột so sánh các chỉ số Precision, Recall, F1-score và ROC AUC giữa các mô hình.
- Các nhận xét và kết luận được in ra rõ ràng sau quá trình đánh giá.

## 8. Yêu cầu Cài đặt
- Python 3.7+
- Các thư viện: pandas, numpy, matplotlib, seaborn, scikit-learn, xgboost, imblearn

## 9. Tài liệu Tham khảo
- [Scikit-learn Documentation](https://scikit-learn.org/)
- [XGBoost Documentation](https://xgboost.readthedocs.io/)
- [Imbalanced-learn Documentation](https://imbalanced-learn.org/)
- [German Credit Data – UCI Repository](https://archive.ics.uci.edu/ml/datasets/statlog+(german+credit+data))

## 10. Liên hệ
Nếu có bất kỳ thắc mắc hay góp ý nào, vui lòng mở issue trên GitHub hoặc liên hệ qua email: thanh.van19062004@gmail.com
```

---

### Hướng dẫn sử dụng README này

1. Tạo file `README.md` trong repository của bạn.
2. Sao chép và dán nội dung trên vào file.
3. Điều chỉnh các thông tin (đường dẫn, email, tên repo, v.v.) cho phù hợp với dự án của bạn.
4. Commit và push file `README.md` lên GitHub.

