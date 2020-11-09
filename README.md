# Thiết lập môi trường chạy ứng dụng Laravel trên Ubuntu
Để chạy một project Laravel chúng ta cần một web server. Giống như trên Windows, khi phát triển một ứng dụng Web sẽ sử dụng XAMPP, thì ở trên Ubuntu sẽ có một Web Server tương tự đó là LAMP. Tiếp theo, cần cài đặt Composer để cài đặt Laravel. Trong bài viết này, mình sẽ hướng dẫn các bạn cài đặt LAMP, Composer trên Ubuntu 18.04, các phiên bản khác cũng tương tự, nhưng mình khuyên mọi người nên sử dụng bản Ubuntu mới nhất để có những trải nghiệm người dùng tốt nhất.

- [1. Cài đặt Apache](#1)

<a name="1" />
### 1. Cài đặt Apache
Apache là phần mềm web server miễn phí mã nguồn mở. Nó đang chiếm đến khoảng 46% thị phần websites trên toàn thế giới. Tên chính thức của Apache là Apache HTTP Server, được điều hành và phát triển bởi Apache Software Foundation. Sau đây là cách cài đặt Apache trên Ubuntu:
Chạy câu lệnh sau: 

```sh
sudo apt-get install apache2
```
