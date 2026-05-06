# bai_tap_03_Phattrienungdungvoimanguonmo
## Django + MariaDB + phpMyAdmin + Cloudflare Tunnel + domain

# 1.  Dựa vào ubuntu trước đó ở bài số 1 tiếp tục chạy trên server đó 
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e3446248-96ec-4407-af09-2eec8cdabb4d" />

# 2. Tạo file compose
<img width="1912" height="1080" alt="image" src="https://github.com/user-attachments/assets/326902ec-4a7e-4ee4-bee2-c083aa031fca" />

# 3. tạo project
## với lênh này để tạo project
- docker run --rm -v $(pwd)/app:/app python:3.11 bash -c "pip install django && django-admin startproject mysite /app"
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6919c080-5c69-48d0-9898-bf1bb62cfa79" />
<img width="1916" height="1080" alt="image" src="https://github.com/user-attachments/assets/43206832-2d19-4391-81c8-1a904ac24b8a" />

# 4. Tiếp theo sửa settings.py để sửa phần database
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c56eb366-e9f7-4c03-963f-68936f3f755a" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1883e46b-63fa-4ce6-8046-76c894aca917" />
<img width="1920" height="1034" alt="image" src="https://github.com/user-attachments/assets/82108881-3ec3-49bb-9bdb-fc101b5b378a" />
