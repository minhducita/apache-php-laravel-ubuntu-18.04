# Thiết lập môi trường chạy ứng dụng Laravel trên Ubuntu
Để chạy một project Laravel chúng ta cần một web server. Giống như trên Windows, khi phát triển một ứng dụng Web sẽ sử dụng XAMPP, thì ở trên Ubuntu sẽ có một Web Server tương tự đó là LAMP. Tiếp theo, cần cài đặt Composer để cài đặt Laravel. Trong bài viết này, mình sẽ hướng dẫn các bạn cài đặt LAMP, Composer trên Ubuntu 18.04, các phiên bản khác cũng tương tự, nhưng mình khuyên mọi người nên sử dụng bản Ubuntu mới nhất để có những trải nghiệm người dùng tốt nhất.

- [1. Cài đặt Apache](#1)
- [2. Cài đặt MySQL](#2)
- [3. Cài đặt PHP](#3)

<a name="1" />

### 1. Cài đặt Apache
Apache là phần mềm web server miễn phí mã nguồn mở. Nó đang chiếm đến khoảng 46% thị phần websites trên toàn thế giới. Tên chính thức của Apache là Apache HTTP Server, được điều hành và phát triển bởi Apache Software Foundation. Sau đây là cách cài đặt Apache trên Ubuntu:

- **Chạy câu lệnh sau**: 

```sh
sudo apt-get install apache2
```

![alt text](https://images.viblo.asia/6311e160-ec62-48b1-b618-d69291cfe8cd.png?raw=true)

- **Sau đó bấm Y để tiếp tục cài đặt.**:  Tiếp theo, mở trình duyệt gõ 127.0.0.1 để kiểm tra Apache đã hoạt động chưa.

![alt text](https://images.viblo.asia/83d5bbb6-3612-457e-be93-67c7ea8b21ed.png?raw=true)

Khi trình duyệt hiện ra như trên, đã cài đặt Apache thành công. Tiếp theo sẽ cài đặt MySQL.


<a name="2" />

### 2. Cài đặt MySQL

 MySQL là hệ quản trị cơ sở dữ liệu mã nguồn mở, được sử dụng phổ biến rộng rãi trên thế giới.
 
- **Sau đây là câu lệnh cài đặt MySQL**:

```sh
sudo apt-get install mysql-server
```

![alt text](https://images.viblo.asia/a956d888-98cd-4d2f-80f9-dbadaa4e3ceb.png?raw=true)

- **Bấm chọn Y để tiếp tục cài đặt**.
Sau khi cài đặt xong, tiếp tục chạy câu lệnh sau: $ sudo mysql_secure_installation.

![alt text](https://images.viblo.asia/b10c44ac-aae4-49e4-a790-154d8f562d0e.png?raw=true)

Ở đây có 2 lựa chọn, nếu chọn Y sẽ sử dụng VALIDATE PASSWORD PLUGIN có nghĩa là bạn phải sử dụng mất khẩu mạnh cho cơ sở dữ liệu, như là độ dài mật khẩu phải trên 8 kí tự, in hoa, in thường, kí tự đặt biệt, etc... Còn nếu chọn N sẽ không sử dụng VALIDATE PASSWORD PLUGIN. Và ở đây cài đặt trên máy cá nhân nên cũng không cần sử VALIDATE PASSWORD PLUGIN. Nên ở đây mình sẽ chọn N để tiện cho việc cài đặt.

Sau khi chọn N, sẽ yêu cầu bạn thiết lập mật khẩu cho MySQL. Ở đây để dễ nhớ mình sẽ đặt là: 123456

![alt text](https://images.viblo.asia/54afc2ba-22a8-4546-b29a-d24fe4d17b83.png?raw=true)

Gõ lại mật khẩu lần nữa. Và ấn Enter.

![alt text](https://images.viblo.asia/22822362-cada-479a-943a-b107939116f7.png?raw=true)

Tiếp theo chọn Y và ấn Enter.

![alt text](https://images.viblo.asia/6d74f186-dc4b-4477-bed5-455a4f9ab2bc.png?raw=true)

Tiếp theo chọn N và ấn Enter.

![alt text](https://images.viblo.asia/bffea3e6-f422-4af2-ab50-4823d3e15897.png?raw=true)

Tiếp theo chọn Y và Enter.

![alt text](https://images.viblo.asia/56a1f210-fa55-4a72-a748-3898ae56f785.png?raw=true)

Tiếp theo chọn Y và Enter.

![alt text](https://images.viblo.asia/306705b4-5a61-41e9-94f4-c697affa1a82.png?raw=true)

Vậy là đã cài đặt xong MySQL. Tiếp theo chạy cậu lệnh sau:$ mysql -u root -p để truy cập vào MySQL, root ở đây là username mặc định khi cài đặt MySQL. Bạn cũng thể tự tạo một tài khoản khác để truy cập vào MySQL.

```sh
mysql -u root -p
```

![alt text](https://images.viblo.asia/675e629f-4fa2-4ae0-9be9-1dc9daecd0c2.png?raw=true)

Nhập mật khẩu đã thiết lập trước đó, nếu như hiện thông tin như ảnh trên. Thì chạy câu lệnh sau: $ sudo mysql. Để truy cập vào MySQL với quyền root mà không cần mật khẩu cho tài khoản có username là root.

![alt text](https://images.viblo.asia/f58af39c-2da9-47bb-bf79-0264427e9c68.png?raw=true)

Sau khi đăng nhập vào MySQL với quyền root, chạy câu lệnh sau:

ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';. Trường password là để thiết lập lại mật khẩu cho tài khoản root. Ở đây mình sẽ đặt giá trị password là 123456.

```sh
ALTER USER 'root'@'localhost' IDENTIFIED WITH
```

![alt text](https://images.viblo.asia/7d737a84-1d22-4fae-ba76-3b0fd66c0589.png?raw=true)

Tiếp theo chạy câu lệnh:FLUSH PRIVILEGES; Mục đích là để reload lại và apply những thay đổi.

![alt text](https://images.viblo.asia/199a8a5c-06d3-49bf-8dab-88a2edd064f3.png?raw=true)

Sau đó thoát ra và đăng nhập lại MySQL để kiểm tra thiết lập mật khẩu thành công hay không.

![alt text](https://images.viblo.asia/1d3ab55c-7604-48f3-9cc4-3e97835e6b62.png?raw=true)

![alt text](https://images.viblo.asia/04204f28-22bf-4ccd-9367-25acb420fd83.png?raw=true)

Vậy là đã cài xong MySQL. Tiếp đến sẽ cài đặt PHP.

<a name="3" />

### 1. Cài đặt PHP

Để cài đặt PHP, chạy câu lệnh sau:

```sh
sudo apt-get install php libapache2-mod-php php-mysql
```

![alt text](https://images.viblo.asia/704b0875-10bd-4030-9924-b4df690ed6c5.png?raw=true)

Để kiểm tra PHP đã cài đặt thành công hay chưa, sử dụng câu lệnh: 

```sh
php -v
```

![alt text](https://images.viblo.asia/5a127b0e-2460-40b7-bce4-6ae53caa4ce1.png?raw=true)

Tiếp cần phải cài đặt một số thư viện cần thiết cho PHP. Ở đây mình cài thư viện mcrypt.

Chạy câu lệnh sau: 

```sh
sudo apt install php-dev libmcrypt-dev php-pear
```

Sau đó chạy tiếp 2 câu lệnh sau:

```sh
sudo pecl channel-update pecl.php.net
sudo pecl install mcrypt-1.0.1
```

Sau khi cài đặt xong, chạy câu lệnh sau: 

```sh
sudo vi /etc/php/7.2/cli/php.ini
```
 và thêm vào file php.ini dòng sau: extension=mcrypt.so
 
 ![alt text](https://images.viblo.asia/b7dd1b24-9fc3-406c-865f-39959129bb70.png?raw=true)
 
 Để kiểm tra cài đặt thành công hay chưa, sử dụng câu lệnh sau:
 
 ```sh
php -m | grep mcrypt.
```

Nếu thành công sẽ hiện ra như sau:
 
 ![alt text](https://images.viblo.asia/7747abbf-420f-4f8d-bf47-27d0acb23638.png?raw=true)
