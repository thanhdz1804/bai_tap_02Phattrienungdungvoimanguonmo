# bai_tap_03_Phattrienungdungvoimanguonmo
## Django + MariaDB + phpMyAdmin + Cloudflare Tunnel + domain

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

# F Thực hành tạo website
## 1.lên ý tưởng và bắt đầu làm
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d9c3e030-2067-4b63-938d-abf91f62ae43" />
### Có thể thầy đã chạy lệnh python manage.py startapp love ở ảnh trên và đã tạo app love

# 2. Thêm app vào settings.py
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/781a7fd2-d8d8-480d-9842-f9e97a2f190d" />
# 3. Chỉnh love/views.py
<img width="1917" height="1080" alt="image" src="https://github.com/user-attachments/assets/d5f5eb7d-434e-4432-9092-70516fdc3a12" />
# 4. Chỉnh  love/urls.py
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/036e54e2-f896-4d1b-bc02-163c5e9d11ef" />
# 5. Nối URL chính Mở file: mysite/urls.py
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/39554e83-2fc2-4832-88b9-6792c9babc02" />
# 6 Tạo thư mục template
##  Lệnh tạo thư mục (mkdir): mkdir -p love/templates/love/
## Sau đó :nano love/templates/love/index.html
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b6e1389a-5fd0-4a09-89d3-46636964f5c8" />

# kết quả
<img width="1914" height="1080" alt="image" src="https://github.com/user-attachments/assets/198171cf-ac5a-4b65-b135-08c473409bf9" />
