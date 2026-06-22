# 🌸 CNN Nhận Diện Hoa — Báo Cáo Môn Mạng Nơ-ron

> **Trường Đại học Công nghiệp Hà Nội (HaUI)**
> Môn học: Mạng Nơ-ron Nhân Tạo

---

## 📋 Tổng Quan

Dự án xây dựng mô hình **Mạng Nơ-ron Tích Chập (Convolutional Neural Network — CNN)** để nhận diện và phân loại **4 loại hoa** từ ảnh đầu vào. Dự án được thực hiện theo hai giai đoạn:

- **Giai đoạn 1 (`main.ipynb`)** — Xây dựng mô hình CNN cơ bản, huấn luyện và phân tích hiện tượng Overfitting. Đây là nội dung **chính của bài báo cáo**.
- **Giai đoạn 2 (`CNN_final.ipynb`)** — Phiên bản nâng cấp, áp dụng kỹ thuật **Data Augmentation** để khắc phục Overfitting và cải thiện khả năng tổng quát hóa của mô hình.

---

## 📁 Cấu Trúc Dự Án

```
CNN_HAUI/
│
├── main.ipynb        # Notebook báo cáo chính: CNN cơ bản + phân tích Overfitting
├── deploy.ipynb             # Triển khai model đã convert (.h5)
├── CNN_final.ipynb          # Notebook nâng cấp: thêm Data Augmentation
├── CNN_NhandienHoa.h5       # File lưu trọng số mô hình đã huấn luyện (phiên bản nâng cấp)
├── datasetv1.rar            # Bộ dữ liệu hoa (train / valid / test)
└── README.md
```

---

## 🗂️ Bộ Dữ Liệu

Bộ dữ liệu (`datasetv1`) gồm ảnh của **4 loại hoa**, được chia thành 3 tập:

| Tập dữ liệu | Mục đích |
|---|---|
| `train/` | Huấn luyện mô hình |
| `valid/` | Theo dõi quá trình huấn luyện, tránh Overfitting |
| `test/` | Đánh giá cuối cùng trên dữ liệu chưa từng thấy |

- Kích thước ảnh đầu vào: **224 × 224 px**, 3 kênh màu RGB
- Chuẩn hóa giá trị điểm ảnh về khoảng `[0, 1]`

---

## 🧠 Kiến Trúc Mô Hình CNN

Mô hình được xây dựng theo kiến trúc tuần tự (Sequential) gồm **5 khối CNN** và **2 tầng phân loại**:

```
Input (224×224×3)
    │
    ├─ Conv2D(32)  → MaxPooling → 112×112
    ├─ Conv2D(64)  → MaxPooling → 56×56
    ├─ Conv2D(128) → MaxPooling → 28×28 → Dropout(0.25)
    ├─ Conv2D(256) → MaxPooling → 14×14
    ├─ Conv2D(512) → MaxPooling → 7×7   → Dropout(0.25)
    │
    ├─ GlobalAveragePooling2D() → vector 512 chiều
    ├─ Dense(256, relu) → Dropout(0.5)
    └─ Dense(4, softmax) → Output (4 loại hoa)
```

| Thành phần | Giá trị |
|---|---|
| Optimizer | Adam (lr = 0.001) |
| Loss function | Categorical Crossentropy |
| Metric | Accuracy |
| Batch size | 64 |

---

## 📊 Giai Đoạn 1: Phân Tích Overfitting (`Overfitting.ipynb`)

### Mục tiêu
Huấn luyện mô hình CNN cơ bản (**50 epochs**) và quan sát hiện tượng **Overfitting** — khi mô hình học quá tốt trên tập train nhưng kém tổng quát hóa trên tập validation.

### Quy trình

1. **Khai báo thư viện** — TensorFlow, Keras, Matplotlib, NumPy
2. **Giải nén dataset** từ `datasetv1.rar`
3. **Tiền xử lý dữ liệu** — rescale ảnh, nạp qua `ImageDataGenerator`
4. **Xây dựng kiến trúc CNN** — 5 khối Conv + 2 lớp Dense
5. **Huấn luyện 50 epochs** — không dùng Data Augmentation
6. **Trực quan hóa** — đồ thị Accuracy & Loss của train vs. validation
7. **Đánh giá** trên tập test
8. **Dự đoán** ảnh thực tế tải lên từ máy tính

### Dấu hiệu Overfitting cần quan sát
- `Train Accuracy` tăng đều và đạt rất cao
- `Validation Accuracy` tăng chậm, sau đó dao động hoặc giảm
- `Train Loss` giảm liên tục
- `Validation Loss` giảm rồi **tăng trở lại** — đây là dấu hiệu rõ ràng nhất của Overfitting

---

## 🚀 Giai Đoạn 2: Nâng Cấp — Giảm Overfitting (`CNN_final.ipynb`)

### Cải tiến áp dụng

**Data Augmentation** — tăng cường dữ liệu bằng cách biến đổi ngẫu nhiên ảnh trong tập train:

| Kỹ thuật | Thông số |
|---|---|
| Xoay ảnh | ±20° |
| Dịch chuyển ngang | 20% |
| Dịch chuyển dọc | 20% |
| Biến dạng (shear) | 20% |
| Phóng to / thu nhỏ | 20% |
| Lật ảnh ngang | Có |

- Huấn luyện lại với **100 epochs** sử dụng dữ liệu đã augmentation
- Tỷ lệ Dropout điều chỉnh lên **0.35** ở các lớp giữa
- Mô hình sau huấn luyện được lưu thành file `CNN_NhandienHoa.h5`

### Kết quả mong đợi sau cải tiến
- Khoảng cách giữa `Train Accuracy` và `Validation Accuracy` thu hẹp lại
- `Validation Loss` ổn định hơn, không tăng đột biến
- Mô hình tổng quát hóa tốt hơn trên ảnh thực tế

---

## ⚙️ Hướng Dẫn Chạy

### Yêu cầu môi trường

```
Python >= 3.8
TensorFlow >= 2.x
Keras
Matplotlib
NumPy
Pillow
```

### Chạy trên Google Colab (Khuyến nghị)

1. Mở file `.ipynb` tương ứng trên [Google Colab](https://colab.research.google.com/)
2. Tải file `datasetv1.rar` lên Colab hoặc Google Drive(https://drive.google.com/drive/folders/13yyk74C_ljLvXb8DhiVxCcRY-CzMcALF?usp=drive_link)
3. Chạy lần lượt từng cell theo thứ tự từ trên xuống
4. Quan sát đồ thị và kết quả đánh giá ở cuối notebook

### Sử dụng mô hình đã huấn luyện

Nếu không muốn huấn luyện lại, có thể tải trực tiếp file `CNN_NhandienHoa.h5`:

```python
from tensorflow.keras.models import load_model

model = load_model("CNN_NhandienHoa.h5")
model.summary()
```

---

## 🔑 Khái Niệm Chính

**Overfitting** là hiện tượng mô hình học thuộc lòng dữ liệu huấn luyện thay vì học các đặc trưng tổng quát, dẫn đến kết quả tốt trên tập train nhưng kém trên dữ liệu mới.

**Các kỹ thuật chống Overfitting trong dự án:**
- **Dropout** — ngắt ngẫu nhiên một phần nơ-ron trong quá trình huấn luyện
- **Data Augmentation** — mở rộng tập train bằng biến đổi ảnh, giúp mô hình học đa dạng hơn
- **GlobalAveragePooling2D** — thay thế Flatten để giảm số tham số

---

## 📚 Công Nghệ Sử Dụng

![Python](https://img.shields.io/badge/Python-3.8+-blue?logo=python)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange?logo=tensorflow)
![Keras](https://img.shields.io/badge/Keras-red?logo=keras)
![Colab](https://img.shields.io/badge/Google_Colab-F9AB00?logo=googlecolab&logoColor=white)

---

## 👤 Tác Giả

**Nguyễn Tiến Đạt**
Sinh viên — Đại học Công nghiệp Hà Nội (HaUI)
GitHub: [@datnguyentien-dev-AI-Electronic](https://github.com/datnguyentien-dev-AI-Electronic)
