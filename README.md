# Môn: Phát triển ứng dụng với mã nguồn mở-TEE0421

# Lớp: 58KTPM

3Bài tập 02:

# SỬ DỤNG DJANGO ĐỂ TẠO WEB QUẢN LÝ TIỆM CẦM ĐỒ
deadline : 23h59 ngày 09 tháng 5 năm 2026.
Link gửi bài: Tại đây

# TỔ CHỨC CSDL CHO HỆ THỐNG QUẢN LÝ TIỆM CẦM ĐỒ: viết tay ra giấy, lấy điện thoại chụp lại, upload ảnh lên github (đã nói về các nghiệp vụ trên lớp, ghi bảng)

# SỬ DỤNG DOCKER TRÊN UBUNTU ĐỂ:

## Mariadb : chứa csdl của hệ thống này

## Phpmyadmin: để soi được csdl (chỉ để xem, ko cần tạo bảng từ đây, django sẽ làm hết)

## Django: build 1 docker container (dùng Dockerfile): trên nền python, sử dụng django, nhớ mount thư mục để dễ edit, edit dùng: sudo nano ten_file

## sau khi có 3 service này trong file docker-compose.yml :
run nó, cấu hình để Django nhận csdl mariadb (sửa file settings.py), cấu hình user login ban đầu, mô tả các bảng trong models.py, .... (đc phép sử dụng AI để làm) => KQ được trang admin, y/c đăng nhập, vào trang admin: cho phép thêm sửa xoá dữ liệu các bảng. các trường là khoá ngoại chỉ việc chọn text (mặc dù là csdl tại trường FK đó lưu ID của PK mà nó tham chiếu : sử dụng phpmyadmin để kiểm chứng)
chú ý kết hợp ssh để chạy lệnh tác động vào django và sudo nano để edit file.
sử dụng template (file html, sử dụng cú pháp jinja2), lấy context từ 1 view home_page, để tạo trang liệt kê các con nợ đến hạn mà chưa trả tiền!
sử dụng cloudflare tunnel để public kết quả lên 1 sub-domain => chụp kết quả

# Hướng dẫn:

# Tạo thư mục để chứa image tự buid cho django
Vào thư mục đó tạo file tên: Dockerfile (nội dung hỏi AI xem file này cần có nội dung gì, full comment cho từng dòng lệnh trong file này => mục tiêu kép: để hiểu và để hệ thống chạy được)
AI sẽ nói cần thêm file requirements.txt để cài các thư viện cho python (cài qua lệnh pip) => tạo file requirements.txt với nội dung tưng ứng, trong file này cũng comment được => comment xem thư viện nào dùng để làm gì
Sau mỗi lần sửa đỏi có thể phải chạy lệnh dạng : docker compose exec TÊN_SERVICE_DJANGO_CỦA_BẠN python manage.py migrate để tác động vào django (còn nhiều lệnh khác chứ ko luôn như này), để django thay đổi csdl hoặc thay đổi cấu hình.
# A.  Dựa vào ubuntu trước đó ở bài số 1 tiếp tục chạy trên server đó 
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e3446248-96ec-4407-af09-2eec8cdabb4d" />

# B. Tạo file compose
<img width="1912" height="1080" alt="image" src="https://github.com/user-attachments/assets/326902ec-4a7e-4ee4-bee2-c083aa031fca" />

# C. tạo project

## với lênh này để tạo project
- docker run --rm -v $(pwd)/app:/app python:3.11 bash -c "pip install django && django-admin startproject mysite /app"
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6919c080-5c69-48d0-9898-bf1bb62cfa79" />
<img width="1916" height="1080" alt="image" src="https://github.com/user-attachments/assets/43206832-2d19-4391-81c8-1a904ac24b8a" />

# D. Tiếp theo sửa settings.py để sửa phần database
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c56eb366-e9f7-4c03-963f-68936f3f755a" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1883e46b-63fa-4ce6-8046-76c894aca917" />
<img width="1920" height="1034" alt="image" src="https://github.com/user-attachments/assets/82108881-3ec3-49bb-9bdb-fc101b5b378a" />

## kiểm tra đã được hay trưa bằng cách truy cập
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/62142019-e398-460b-b199-8b98463f045a" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6b85dd2f-7605-4e8b-a277-43960bd9a380" />

# E. Cloudflare Tunnel + tên miền 
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7c4cd2df-2aa8-464e-bab8-c2d3d6c257cc" />

# F Thực hành TẠO WEB QUẢN LÝ TIỆM CẦM ĐỒ

## 1. Tạo file tên: Dockerfile và requirements.txt

### Tạo Dockerfile

### nội dung
Ý chính:
FROM → chọn image nền
WORKDIR → thư mục làm việc
COPY → copy file/source code
RUN → chạy lệnh cài thư viện
EXPOSE → mở port
CMD → lệnh chạy Django khi container start
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1b23a599-e84f-489b-bf8a-fa4f953c41c8" />

### Tạo requirements.txt
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2d849b79-f6e5-46cd-b111-8ed990359ecd" />

### sửa docker compose trước đó
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b81523b0-1635-4846-b955-c15a3a93a827" />

### Reset và cập nhật toàn bộ hệ thống
dùng tập lệnh 
docker compose down
docker compose up --build -d
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4358de00-fcff-4a12-9fd9-ba8fe06617a9" />

## 2. Tạo tài khoản admin Django 

- dùng lệnh :docker compose exec django python manage.py createsuperuser
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/bb5cc47e-0e4c-4937-86fd-affd12947d21" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/89df4a10-77d0-453e-ba65-8cd1d7bdce50" />

## 3. Tạo app TIỆM CẦM ĐỒ
-lệnh tạo app: docker-compose exec django python manage.py startapp pawnshop

## Khai báo app trong settings.py
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/95b97e0a-6fcb-470d-ac4f-e9d2c375c600" />

## Tạo models
lệnh nano app/pawnshop/models.py 

<img width="1917" height="1080" alt="image" src="https://github.com/user-attachments/assets/f00b7b92-0540-49c4-a771-a27fb078fb09" />

### Tạo migration
lệnh: docker-compose exec django python manage.py makemigrations
-docker-compose exec django python manage.py migrate
1. makemigrations (Đóng gói thay đổi)
Chức năng: Quét các thay đổi trong file models.py và tự động tạo ra các file hướng dẫn (file migration).
Mục đích: Ghi lại "lịch sử" thay đổi cấu trúc dữ liệu dưới dạng bản nháp.
2. migrate (Cập nhật Database)
Chức năng: Áp dụng các file hướng dẫn từ bước trên vào Database thật.
Mục đích: Trực tiếp tạo bảng, thêm cột hoặc sửa đổi dữ liệu trong hệ quản trị cơ sở dữ liệu (PostgreSQL, MySQL, SQLite...).
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0843a017-b59b-4f1a-9e7d-1e747cf23789" />

### bảng trong admin
lệnh: nano app/pawnshop/admin.py
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/84a19572-df11-44d1-84fb-70c25348354c" />
<img width="1918" height="1080" alt="image" src="https://github.com/user-attachments/assets/3fc7df4c-7344-401a-8fb4-7d117eaac44a" />


### Tạo thư mục template
lệnh: mkdir -p app/pawnshop/templates

### Tạo file HTML
lệnh: nano app/pawnshop/templates/home.html
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/91c36e2f-5164-4b86-a7b0-0d295b9407a3" />


### Tạo view
lệnh: nano app/pawnshop/views.py
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b63302af-e3cf-4604-ab9e-e5570ebfc1e1" />


### Tạo urls cho app
lệnh: nano app/pawnshop/urls.py
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/8ce9b225-2403-486a-848e-f126cae8a702" />


### Kết nối URL chính
lệnh :nano app/mysite/urls.py
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/322b4d95-da93-4108-8a7a-9c4eed51b170" />

### Restart
lệnh: docker-compose restart
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/03b39653-437c-4664-984a-fab0137acca7" />

### TEST
thêm dữ liệu demo
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/cd6341ef-7305-4d62-bcd3-6d794fdd166a" />

<img width="1920" height="1079" alt="image" src="https://github.com/user-attachments/assets/5c8865ae-f1c2-4372-9b5a-d02bcf7f9832" />

