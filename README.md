# DS304 - Thiết kế và phân tích thực nghiệm
## Giới thiệu:
Bài toán này tập trung vào nhiệm vụ phân loại cảm xúc theo từng khía cạnh trong một bình luận. Hệ thống được xây dựng để nhận diện các khía cạnh liên quan và xác định thái độ của người dùng đối với từng khía cạnh, qua đó ước lượng mức độ hài lòng một cách chi tiết và chính xác hơn.
## Bộ dữ liệu:
- Thu thập dữ liệu: 5323 mẫu của các bình luận trích từ Kaggle, sau đó dữ liệu được gán nhãn khía cạnh và cảm xúc.
- Khía cạnh: 
  Tên	          Mô tả
  Price	        Nhận xét liên quan đến giá cả, chi phí
  Quality	      Nhận xét về chất lượng món ăn, hương vị, số lượng
  Environment	  Không gian, nội thất, vị trí, không khí
  Service	      Thái độ phục vụ, nhân viên, tốc độ phục vụ
  Other	        Trường hợp chung, không thuộc các nhóm trên
- Cảm xúc: Positive - Tích cực, Negative - Tiêu cực, Neutral - Trung tính
- Gán nhãn dữ liệu: gán nhãn trên 1,123 mẫu cho tới khi độ đồng thuận > 0.7
![image](https://github.com/user-attachments/assets/0328d280-ffe5-40d1-b1a4-a103b57c6024)
## Tiền xử lý dữ liệu:
![image](https://github.com/user-attachments/assets/71067227-fea9-46fe-8078-4a070da0c964)
## Mô hình:
Thư mục Model gồm:
- aspect_labels.csv: đầu vào cho bài toán Aspect Regconition
- aspect_sentiments.csv: đầu vào cho bài toán Aspect-based Sentiment Analysis
- model.ipynb: source code
![image](https://github.com/user-attachments/assets/fb69490d-3794-45d9-a9fe-b7de9e2484e5)
2 đầu vào được sử dụng nhằm giúp đánh giá riêng biệt độ chính xác của mỗi bài toán, khi thực hiện thực nghiệm, input cho bài toán 2 là output của bài toán 1.
