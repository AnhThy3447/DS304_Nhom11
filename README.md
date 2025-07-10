_DS304 - Thiết kế và phân tích thực nghiệm_
# Dự Đoán Mức Độ Hài Lòng Của Khách Hàng Từ Các Bình Luận Tại Nhà Hàng
## I. Giới thiệu:
•	**Bài toán lớn (Generalized Problem):** Phân Tích Phản Hồi Khách Hàng Theo Khía Cạnh Cho Nhà Hàng
<img width="1748" height="297" alt="image" src="https://github.com/user-attachments/assets/bf9890f1-3394-486e-ac5b-0d0526d368fc" />

•	**Bài toán nhỏ (Specialized Problem):** Phân Tích Cảm xúc Bình Luận của Khách Hàng Dựa Trên Khía Cạnh, với hai nhiệm vụ chính:
- _Nhiệm vụ 1:_ Phát hiện khía cạnh
- _Nhiệm vụ 2:_ Phân loại cảm xúc dựa trên khía cạnh
<img width="1732" height="290" alt="image" src="https://github.com/user-attachments/assets/364147df-1af5-4395-b73d-9cce06af8de4" />

## II. Bộ dữ liệu:
- [Bộ dữ liệu](raw_data.csv): 5323 mẫu của các bình luận trích từ Kaggle, sau đó dữ liệu được gán nhãn khía cạnh và cảm xúc.

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

### Quy trình:
<img width="1059" height="305" alt="image" src="https://github.com/user-attachments/assets/db5c98da-058a-4f49-8084-2240f5ed637b" />

## III. Huấn luyện mô hình
- Thư mục [Dictionaries](Dictionaries/): phục vụ cho quá trình tiền xử lý
- File tiền xử lý ...
- Quá trình thực nghiệm sẽ được trình bày trong source code cho bài toán nhỏ, sẽ được nhắc tới bên dưới.
<img width="1349" height="300" alt="image" src="https://github.com/user-attachments/assets/ce84db5f-401f-4956-95eb-72447a7047a1" />

- Thư mục Model gồm:
  - data:
    - [data_after_preprocessing.csv](Model/data/data_after_preprocessing.csv): là đầu vào cho bài toán nhỏ.
    - [restaurants.csv](Model/data/restaurants.csv): là đầu vào cho bài toán lớn, mô phỏng bài toán lớn trên dữ liệu của 2 nhà hàng khác nhau.
  - notebook:
    - [Generalized_problem.ipynb](Model/data/Generalized_problem.ipynb)
    - [Specialized_problem_Aspect_Regconition.ipynb](Model/data/Specialized_problem_Aspect_Regconition.ipynb)
    - [Specialized_problem_ABSA.ipynb](Model/data/Specialized_problem_ABSA.ipynb)
<img width="1229" height="235" alt="image" src="https://github.com/user-attachments/assets/ee761251-bc9c-41a4-8620-47c24fdbcc0b" />

## IV. Kết quả
- Trình bày tại: [Slide](ds304_slide.pdf)
- Phân tích chi tiết: [Paper](ds304_paper.pdf)

## V. Thành viên:
| Họ và tên              | MSSV       |
|------------------------|------------|
| Võ Ngọc Anh Thy        | 23521565   |
| Đinh Bảo Thy           | 23521563   |
| Trần Đức Thiện         | 23521488   |
