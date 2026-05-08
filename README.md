# Môn: Phát triển ứng dụng với mã nguồn mở-TEE0421
# Lớp: 58KTPM
# Bài tập 02:
# SỬ DỤNG DJANGO ĐỂ TẠO WEB QUẢN LÝ TIỆM CẦM ĐỒ
## deadline : 23h59 ngày 09 tháng 5 năm 2026.
## Ngày làm: 07/05/2026

### 1. TỔ CHỨC CSDL CHO HỆ THỐNG QUẢN LÝ TIỆM CẦM ĐỒ
<img width="1920" height="2560" alt="image" src="https://github.com/user-attachments/assets/6781bac3-1252-4227-81f4-e1c4f046613a" />
### 2. SỬ DỤNG DOCKER TRÊN UBUNTU ĐỂ:
Tạo thư mục dự án
  <img width="1487" height="751" alt="image" src="https://github.com/user-attachments/assets/1338c2d7-1193-43e3-8666-872785b149e5" />
Thêm các dịch vụ vào trong file docker-compose.yml ( sử dụng sudo nano docker-compose.yml):
a. Mariadb : chứa csdl của hệ thống này
b. Phpmyadmin: để soi được csdl 
<img width="1468" height="758" alt="image" src="https://github.com/user-attachments/assets/d32c48d7-28c6-40c8-8a92-31251b145273" />
<img width="1888" height="1018" alt="image" src="https://github.com/user-attachments/assets/2a0f2cdc-9c75-4575-ad40-6dee02ad53c2" />
c. Django: build 1 docker container (dùng Dockerfile): trên nền python, sử dụng django, nhớ mount thư mục để dễ edit, edit dùng: sudo nano ten_file
- Tạo 1 thư mục riêng cho Django:
    <img width="1438" height="72" alt="image" src="https://github.com/user-attachments/assets/b4d29017-108e-47e8-983e-576e806aaea2" />
  Dùng "sudo nano django_app/requirements.txt" để edit file và thêm các thư viện cần thiết
  <img width="1483" height="752" alt="image" src="https://github.com/user-attachments/assets/131e6f31-0971-451a-9435-dfe27672f7f1" />
  Tạo và edit DockerFile thêm các công cụ cần thiết để Django kết tối tới Mariadb:
  <img width="1498" height="752" alt="image" src="https://github.com/user-attachments/assets/298e0fce-b360-464e-95ae-fffaa154b763" />
  Cấu hình build django trong docker-compose.yml và mout thư mục:
<img width="1471" height="762" alt="image" src="https://github.com/user-attachments/assets/8a0639d1-00bd-45e6-9c6b-e47fc1ec5bf4" />
d. Chạy docker compose và cấu hình file setting.py để Django nhận csdl từ mariadb:
<img width="1457" height="122" alt="image" src="https://github.com/user-attachments/assets/521fcca9-2f6a-4184-bd87-e444f3ba4320" />
<img width="1460" height="750" alt="image" src="https://github.com/user-attachments/assets/abfab197-6091-40ab-9b03-4174ebe12c2f" />
- Mô tả các bảng trong model.py
<img width="1475" height="733" alt="image" src="https://github.com/user-attachments/assets/c25116a9-5560-44fa-b0b4-57348afeb492" />
- Cấu hình trang admin:
  <img width="1482" height="748" alt="image" src="https://github.com/user-attachments/assets/5c5d880a-8523-4fc0-9273-b3b180dd08cc" />
- kết hợp ssh để chạy lệnh tác động vào django và sudo nano để edit file:
  ===> KQ được:trang admin, y/c đăng nhập vào trang admin: cho phép thêm sửa xoá dữ liệu các bảng. các trường là khoá ngoại chỉ việc chọn text (mặc dù là csdl tại trường FK đó lưu ID của PK mà nó tham chiếu : sử dụng phpmyadmin để kiểm chứng)
 + Bảng khachhang ban đầu trong php:
   <img width="1138" height="465" alt="image" src="https://github.com/user-attachments/assets/db0166da-0568-451e-81bd-5c0819ddbda1" />
 + Sau khi thực hiện thao tác thêm khách hàng trên Django:
   <img width="1488" height="642" alt="image" src="https://github.com/user-attachments/assets/dc76933b-2839-4130-8001-5adb9cf7c27f" />
<img width="1315" height="725" alt="image" src="https://github.com/user-attachments/assets/94ef8bea-5e2b-4339-b01d-65bc4bd34324" />
===> Django đã liên kết được tới Mariadb và thực hiện được các thao tác trực quan hóa trên Django
e. Sử dụng template (file html, sử dụng cú pháp jinja2), lấy context từ 1 view home_page, để tạo trang liệt kê các con nợ đến hạn mà chưa trả tiền!
 1. Cấu hình file setting.py:
    <img width="1476" height="735" alt="image" src="https://github.com/user-attachments/assets/9cb35636-8681-4916-b17d-dc48eab6739d" />
2. Cấu hình file view.py:
   <img width="1462" height="736" alt="image" src="https://github.com/user-attachments/assets/000a846b-ceac-4be1-8666-d7ed019c069e" />

3. Tạo thư mục để chứa file html:
   <img width="902" height="18" alt="image" src="https://github.com/user-attachments/assets/e23d0a93-72e7-42ff-89a9-6503b38703d8" />
  <img width="1445" height="667" alt="image" src="https://github.com/user-attachments/assets/c92a599e-456b-4323-9ba2-909c5bb96529" />

4. Cấu hình file urls.py để định tuyến đường dẫn
   <img width="1459" height="732" alt="image" src="https://github.com/user-attachments/assets/459c332a-a7f3-4084-be17-d2edb075b413" />
==Kết quả truy cập trang danh sách các con nợ trên local:
<img width="1767" height="692" alt="image" src="https://github.com/user-attachments/assets/04440ebc-764c-4a6e-bd1b-38c7dc07b8e9" />
f. Sử dụng cloudflare tunnel để public kết quả lên 1 sub-domain:
<img width="1819" height="877" alt="image" src="https://github.com/user-attachments/assets/bda519e2-bc80-48a3-a48b-6db015db8c4d" />
