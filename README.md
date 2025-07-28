# Image Captioning with Flickr8k Dataset

## Tổng quan
Dự án này xây dựng một hệ thống Image Captioning sử dụng tập dữ liệu Flickr8k trên Google Colab. Mục tiêu là tạo ra mô hình có khả năng sinh mô tả tự động cho ảnh bằng tiếng Anh, ứng dụng các kỹ thuật deep learning hiện đại.

## Các bước thực hiện

1. **Kết nối Google Drive và chuẩn bị dữ liệu**
   - Kết nối Google Drive để lưu trữ và truy xuất dữ liệu.
   - Tải và giải nén bộ dữ liệu Flickr8k từ Kaggle.
   - Chuyển dữ liệu vào thư mục trên Google Drive.

2. **Tiền xử lý dữ liệu**
   - Đọc và làm sạch caption (mô tả ảnh).
   - Chuẩn hóa văn bản, loại bỏ ký tự đặc biệt, số, khoảng trắng thừa.
   - Thêm token 'start' và 'end' cho mỗi caption.
   - Tokenize caption và xây dựng từ điển (tokenizer).
   - Chia tập dữ liệu thành train, validation, test.

3. **Trích xuất đặc trưng ảnh**
   - Sử dụng mô hình InceptionV3 pretrained để trích xuất đặc trưng từ ảnh.
   - Lưu đặc trưng ảnh vào file .pkl để sử dụng cho huấn luyện và dự đoán.

4. **Xây dựng mô hình Image Captioning**
   - Thiết kế mô hình encoder-decoder:
     - Encoder: Nhận đặc trưng ảnh từ InceptionV3.
     - Decoder: Nhận chuỗi caption đã được tokenize.
     - Kết hợp hai nhánh và sinh ra caption mới.
   - Sử dụng các lớp Dense, LSTM, Embedding, BatchNormalization.
   - Biên dịch mô hình với optimizer Adam và loss categorical_crossentropy.

5. **Huấn luyện mô hình**
   - Sử dụng generator để tạo batch dữ liệu huấn luyện và validation.
   - Callback EarlyStopping và LearningRateScheduler để tối ưu quá trình huấn luyện.
   - Lưu mô hình sau khi huấn luyện.

6. **Dự đoán và đánh giá**
   - Hàm generate_caption sinh caption cho ảnh mới.
   - Hàm visualize_test_predictions trực quan hóa kết quả dự đoán trên tập test.
   - Đánh giá mô hình bằng BLEU score.

## Thư viện sử dụng
- TensorFlow, Keras
- NumPy, Pandas, Matplotlib, Seaborn, Plotly
- scikit-learn
- NLTK (BLEU score)
- PIL, tqdm

## Hướng dẫn sử dụng
1. Chạy lần lượt các cell trong notebook để tải dữ liệu, tiền xử lý, trích xuất đặc trưng, xây dựng và huấn luyện mô hình.
2. Có thể thay đổi đường dẫn ảnh để thử nghiệm caption cho ảnh mới.
3. Kết quả caption và BLEU score sẽ được hiển thị trực tiếp trong notebook.

## Đóng góp
Tác giả: Lê Hoàng Phúc - 21114851

## Liên hệ
- Email: [liên hệ cá nhân]
- Github: [link github nếu có]
