# CNN_HAUI

Một dự án Mạng Nơ-ron Tích Chập (CNN) được phát triển cho [HAUI](https://haui.edu.vn/) (Đại học Công Nghiệp Hà Nội).

## 📋 Tổng Quan Dự Án

Dự án này triển khai các Mạng Nơ-ron Tích Chập cho phân loại hình ảnh và nghiên cứu học sâu. Nó bao gồm các kiến trúc CNN khác nhau, kịch bản đào tạo và các chỉ số đánh giá cho các tác vụ thị giác máy tính.

**Ngôn Ngữ Chính**: Jupyter Notebook (Python)

## 🎯 Tính Năng

- ✅ Triển khai nhiều kiến trúc CNN
- ✅ Xử lý trước hình ảnh và tăng cường dữ liệu
- ✅ Đào tạo và đánh giá mô hình
- ✅ Trực quan hóa chỉ số hiệu suất
- ✅ Hướng dẫn Jupyter Notebook
- ✅ Hỗ trợ mô hình được đào tạo trước

## 📂 Cấu Trúc Dự Án

```
CNN_HAUI/
├── README.md                 # Tài liệu dự án
├── notebooks/               # Các Jupyter notebook
│   ├── 01_data_exploration.ipynb
│   ├── 02_model_training.ipynb
│   └── 03_evaluation.ipynb
├── src/                     # Mã nguồn
│   ├── models.py           # Các mô hình CNN
│   ├── utils.py            # Các hàm tiện ích
│   └── train.py            # Kịch bản đào tạo
├── data/                    # Thư mục tập dữ liệu
│   ├── train/
│   ├── test/
│   └── val/
├── models/                  # Các mô hình được đào tạo trước
└── requirements.txt         # Các phụ thuộc Python
```

## 🚀 Bắt Đầu

### Yêu Cầu Trước Tiên

- Python 3.8+
- Jupyter Notebook
- pip hoặc conda

### Cài Đặt

1. **Sao chép kho lưu trữ**
   ```bash
   git clone https://github.com/datnguyentien-dev-AI-Electronic/CNN_HAUI.git
   cd CNN_HAUI
   ```

2. **Tạo môi trường ảo**
   ```bash
   python -m venv venv
   source venv/bin/activate  # Trên Windows: venv\Scripts\activate
   ```

3. **Cài đặt các phụ thuộc**
   ```bash
   pip install -r requirements.txt
   ```

### Cách Sử Dụng

#### Chạy Jupyter Notebooks
```bash
jupyter notebook
```

Điều hướng đến thư mục `notebooks/` và mở bất kỳ tệp `.ipynb` nào để khám phá dự án.

#### Đào Tạo Mô Hình
```bash
python src/train.py --dataset your_dataset --epochs 50 --batch-size 32
```

#### Đánh Giá Mô Hình
```bash
python src/evaluate.py --model-path path/to/model.pth --test-data test/
```

## 📊 Các Kiến Trúc Mô Hình

Dự án này bao gồm các triển khai của:

- **LeNet** - CNN cổ điển cho nhận dạng chữ số
- **AlexNet** - CNN sâu cho phân loại hình ảnh
- **VGG** - Các mạng Visual Geometry Group
- **ResNet** - Các Mạng Thặng Dư
- **CNN Tùy Chỉnh** - Kiến trúc dành riêng cho dự án

## 📈 Kết Quả

| Mô Hình | Độ Chính Xác | Độ Chính Xác | Recall | F1-Score |
|---------|--------------|-------------|--------|----------|
| LeNet | - | - | - | - |
| VGG16 | - | - | - | - |
| ResNet50 | - | - | - | - |

*Các kết quả sẽ được cập nhật khi hoàn thành đào tạo.*

## 📦 Các Phụ Thuộc

Các thư viện chính được sử dụng trong dự án này:

- `tensorflow` / `pytorch` - Các khung học sâu
- `numpy` - Tính toán số
- `pandas` - Thao tác dữ liệu
- `matplotlib` - Trực quan hóa dữ liệu
- `scikit-learn` - Các tiện ích học máy
- `opencv-python` - Thị giác máy tính
- `jupyter` - Các notebook tương tác

Xem `requirements.txt` để có danh sách đầy đủ.

## 📚 Tài Liệu

Để biết thông tin chi tiết về các thành phần cụ thể, hãy tham khảo:
- Các notebook trong thư mục `/notebooks`
- Các nhận xét trong mã inline
- Các chuỗi docstring của hàm

## 🔬 Nghiên Cứu & Tài Liệu Tham Khảo

- [Very Deep Convolutional Networks for Large-Scale Image Recognition](https://arxiv.org/abs/1409.1556) - Bài báo VGG
- [Deep Residual Learning for Image Recognition](https://arxiv.org/abs/1512.03385) - Bài báo ResNet
- [ImageNet Classification with Deep Convolutional Neural Networks](https://papers.nips.cc/paper/2012/hash/c399862d3b9d6b76c8436e924a68c45b-Abstract.html) - Bài báo AlexNet

## 📝 Giấy Phép

Dự án này có nguồn mở và có sẵn theo [Giấy Phép MIT](LICENSE).

## 👨‍💻 Tác Giả

**Đạt Nguyễn Tiến**
- GitHub: [@datnguyentien-dev-AI-Electronic](https://github.com/datnguyentien-dev-AI-Electronic)
- Cơ Sở: Đại học Công Nghiệp Hà Nội (HAUI)

## 🤝 Đóng Góp

Chúng tôi hoan nghênh các đóng góp! Vui lòng thoải mái gửi Pull Request.

### Cách Đóng Góp:
1. Fork kho lưu trữ
2. Tạo nhánh tính năng (`git checkout -b feature/TínhNăngTuyệtVời`)
3. Cam kết các thay đổi của bạn (`git commit -m 'Thêm một số TínhNăngTuyệtVời'`)
4. Đẩy đến nhánh (`git push origin feature/TínhNăngTuyệtVời`)
5. Mở Pull Request

## 📞 Liên Hệ & Hỗ Trợ

Để có câu hỏi hoặc vấn đề, vui lòng:
- Mở một [Issue](https://github.com/datnguyentien-dev-AI-Electronic/CNN_HAUI/issues)
- Liên hệ qua GitHub

## ⭐ Hỗ Trợ Dự Án

Nếu bạn thấy dự án này hữu ích, vui lòng cho nó một ngôi sao! ⭐

---

**Cập Nhật Lần Cuối**: 30 Tháng 5, 2026

**Trạng Thái**: 🚧 Đang Phát Triển
