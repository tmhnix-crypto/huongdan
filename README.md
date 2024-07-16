#Bước 1: Cài đặt NVM và Node.js


# Cài đặt NVM
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh |  

# Thiết lập biến môi trường cho NVM
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/ _completion" ] && \. "$NVM_DIR/ _completion"

# Cài đặt Node.js
nvm install node
#Bước 2: Cài đặt các gói cần thiết


# Cài đặt unzip
sudo apt install unzip

# Cập nhật danh sách gói
sudo apt-get update
#Bước 3: Cài đặt gdown để tải file từ Google Drive nhanh chóng
 
 
# Cài đặt pip3
sudo apt-get install python3-pip

# Cài đặt gdown
pip3 install gdown

# Cài đặt các công cụ hỗ trợ phần mềm
sudo apt-get install software-properties-common
#Bước 4: Cài đặt MySQL
 
 
# Cập nhật danh sách gói
sudo apt update

# Cài đặt MySQL Server
sudo apt-get install mysql-server

# Kiểm tra trạng thái MySQL
sudo systemctl status mysql

# Khởi động lại MySQL
sudo systemctl restart mysql

# Bảo mật MySQL
sudo mysql_secure_installation
# Đặt mật khẩu root tùy theo mong muốn

# Đăng nhập vào MySQL
sudo mysql

# Tạo database và user
CREATE DATABASE db;
CREATE USER 'root'@'localhost' IDENTIFIED BY '123123Aa';
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '123123Aa';
GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost' WITH GRANT OPTION;
FLUSH PRIVILEGES;
exit
#Bước 5: Cài đặt Redis
 
 
# Cài đặt Redis Server
sudo apt-get install redis-server

# Bật Redis Server khi khởi động
sudo systemctl enable redis-server

# Chỉnh sửa cấu hình Redis
cd /etc/redis
sudo nano redis.conf

# Thay đổi các dòng sau:
# supervised no -> supervised systemd
# bind 127.0.0.1 ::1 -> bind 127.0.0.1

# Tạo thư mục và thay đổi quyền sở hữu
sudo mkdir /var/run/redis
sudo chown redis /var/run/redis

# Khởi động Redis
sudo systemctl start redis.service

# Kiểm tra trạng thái Redis
sudo systemctl status redis
#Bước 6: Cài đặt Node.js và PM2
 
 
# Cài đặt Node.js phiên bản 14.17
nvm install 14.17

# Cài đặt PM2
npm install pm2 -g

# Cài đặt các gói Node.js
npm install    # (mỗi lần tạo mới node_modules)
#Bước 7: Khởi động ứng dụng
 
 
# Di chuyển vào thư mục dự án của bạn
cd /var/app1/server-new

# Cấu hình file .env

# Nếu còn node_modules cũ thì xóa đi
rm -rf node_modules

# Cài đặt lại các gói Node.js
npm install

# Chạy ứng dụng
node server.js  # chạy xong bấm Ctrl + C

# Sử dụng PM2 để quản lý tiến trình
pm2 start server.js

# Khởi động lại tất cả tiến trình PM2 và cập nhật môi trường
pm2 restart all --update-env
#Lưu ý: Bạn sẽ cần cấu hình và quản lý phpMyAdmin theo hướng dẫn riêng nếu cần thiết.
