_DS304 - Thiết kế và phân tích thực nghiệm_
# Dự Đoán Mức Độ Hài Lòng Của Khách Hàng Từ Các Bình Luận Tại Nhà Hàng

# Mục lục
1. [Giới thiệu](#i-giới-thiệu)
2. [Bộ dữ liệu](#ii-bộ-dữ-liệu)
3. [Huấn luyện mô hình](#iii-huấn-luyện-mô-hình)
4. [Tổng kết](#iv-tổng-kết)
5. [Thành viên](#v-thành-viên)
   
## 1. Giới thiệu:
•	**Bài toán lớn (Generalized Problem):** Phân Tích Phản Hồi Khách Hàng Theo Khía Cạnh Cho Nhà Hàng
<img width="1748" height="297" alt="image" src="https://github.com/user-attachments/assets/bf9890f1-3394-486e-ac5b-0d0526d368fc" />

•	**Bài toán nhỏ (Specialized Problem):** Phân Tích Cảm xúc Bình Luận của Khách Hàng Dựa Trên Khía Cạnh, với hai nhiệm vụ chính:
- _Nhiệm vụ 1:_ Phát hiện khía cạnh
- _Nhiệm vụ 2:_ Phân loại cảm xúc dựa trên khía cạnh
<img width="1732" height="290" alt="image" src="https://github.com/user-attachments/assets/364147df-1af5-4395-b73d-9cce06af8de4" />

## 2. Bộ dữ liệu:
### Bộ dữ liệu: 
5323 mẫu của các bình luận trích từ Kaggle, sau đó dữ liệu được gán nhãn khía cạnh và cảm xúc.

### Khía cạnh:
  
| Tên         | Mô tả                                                 |
|-------------|--------------------------------------------------------|
| Price       | Nhận xét liên quan đến giá cả, chi phí                |
| Quality     | Nhận xét về chất lượng món ăn, hương vị, số lượng     |
| Environment | Không gian, nội thất, vị trí, không khí               |
| Service     | Thái độ phục vụ, nhân viên, tốc độ phục vụ            |
| Other       | Trường hợp chung, không thuộc các nhóm trên          |

### Cảm xúc:
- Positive - Tích cực
- Negative - Tiêu cực
- Neutral - Trung tính

### Quy trình gán nhãn:
<img width="1059" height="305" alt="image" src="https://github.com/user-attachments/assets/db5c98da-058a-4f49-8084-2240f5ed637b" />

Bộ dataset sau khi gán nhãn được lưu thành raw_data.csv

## 3. Huấn luyện mô hình
## Tiền xử lý:
Thư mục Preprocessing bao gồm:
- Thư mục [Dictionaries](Dictionaries/): phục vụ cho quá trình tiền xử lý
- [Preprocessing.ipynb](Preprocessing/Preprocessing.ipynb):
  - Loại bỏ dấu câu (Punctuation Removal)
  - Chuyển đổi chữ hoa thành chữ thường (Case Conversion)
  - Chuẩn hóa từ ngữ (Normalization)
  - Rút trích đặc trưng (Embeddings): nhóm thực hiện thực nghiệm thống kê nhằm chọn ra phương pháp embedding phù hợp nhất
- [raw_data.csv](Preprocessing/raw_data.csv)
- [test_restaurants.csv](Preprocessing/test_restaurants.csv)

## Thực nghiệm:
- Các mô hình rút trích đặc trưng, bao gồm: TF-IDF, FastText, USE sẽ được thực nghiệm với bài toán nhỏ (Specialized Problem)

<img width="1349" height="300" alt="image" src="https://github.com/user-attachments/assets/ce84db5f-401f-4956-95eb-72447a7047a1" />

### Nhiệm vụ 1: 
Đánh giá trên chỉ số Recall vì cần đảm bảo không bỏ sót các khía cạnh có trong câu
<img width="1439" height="301" alt="image" src="https://github.com/user-attachments/assets/e3c792a6-579f-49ea-8ec0-bde34cadb39e" />

### Nhiệm vụ 2: 
Sử dụng Precision vì ưu tiên dự đoán đúng cảm xúc một khi đã xác định khía cạnh
<img width="1509" height="313" alt="image" src="https://github.com/user-attachments/assets/06bda4e9-eb64-4208-925d-ba67684a0e2a" />

### Kết luận: 
Từ kết quả mỗi nhiệm vụ, ta thấy sự khác biệt có ý nghĩa thống kê và phương pháp embedding USE là lựa chọn tối ưu. 

## 4. Huấn luyện mô hình:
<img width="1229" height="235" alt="image" src="https://github.com/user-attachments/assets/ee761251-bc9c-41a4-8620-47c24fdbcc0b" />

### Bài toán nhỏ:
- Các thuật toán học máy được sử dụng trong mô hình bao gồm:
  - Logistic Regression
  - Random Forest
  - SVM
  - XGBoost
- _Note_: Quá trình thực thi được nhóm biểu diễn chi tiết tại thư mục Model.

<img width="1144" height="408" alt="image" src="https://github.com/user-attachments/assets/aa9e4dfc-e72a-4299-bd5b-df3e0def57ca" />

Ta thấy trong cả hai nhiệm vụ, mô hình hồi quy Logistic Regression cho ra kết quả cao nhất nên mô hình này được sử dụng cho bài toán lớn.

### Bài toán lớn:
Một tập dữ liệu các câu bình luận từ 2 nhà hàng được thu thập, tiền xử lý và trả kết quả như sau:  
<img width="1494" height="312" alt="image" src="https://github.com/user-attachments/assets/1f0af1aa-890e-4b97-9b4d-10bae4841c9a" />

Để xác định cảm xúc chung cho từng khía cạnh, nhóm áp dụng ngưỡng so sánh cho tỷ lệ giữa hai nhãn Positive và Negative như sau:
- **Công thức:** `r_aspect = (Số lượng nhãn Positive) / (Số lượng nhãn Negative)`
- **Quy tắc gán cảm xúc:**

| Giá trị `r_aspect`       | Cảm xúc gán cho khía cạnh |
|--------------------------|----------------------------|
| `r_aspect` ≤ 1           | Negative                   |
| 1 < `r_aspect` ≤ 1.5     | Neutral                    |
| `r_aspect` > 1.5         | Positive                   |

<img width="1090" height="189" alt="image" src="https://github.com/user-attachments/assets/9d542868-b587-4cd9-8bf4-7afd07e067c4" />

### Cấu trúc mô hình:
- Thư mục Model gồm:
  - data:
    - [data_after_preprocessing.csv](Model/data/data_after_preprocessing.csv): là đầu vào cho bài toán nhỏ.
    - [restaurants.csv](Model/data/restaurants.csv): là đầu vào cho bài toán lớn, mô phỏng bài toán lớn trên dữ liệu của 2 nhà hàng khác nhau.
  - notebook:
    - [Generalized_problem.ipynb](Model/data/Generalized_problem.ipynb): giải quyết bài toán lớn
    - [Specialized_problem_Aspect_Regconition.ipynb](Model/data/Specialized_problem_Aspect_Regconition.ipynb): giải quyết bài toán nhỏ - nhiệm vụ 1
    - [Specialized_problem_ABSA.ipynb](Model/data/Specialized_problem_ABSA.ipynb): giải quyết bài toán nhỏ - nhiệm vụ 2
      
## 5. Tổng kết
- Trình bày tại: [Slide](slide.pdf)
- Phân tích chi tiết: [Paper](paper.pdf)

## V. Thành viên:
| Họ và tên              | MSSV       |
|------------------------|------------|
| Võ Ngọc Anh Thy        | 23521565   |
| Đinh Bảo Thy           | 23521563   |
| Trần Đức Thiện         | 23521488   |
