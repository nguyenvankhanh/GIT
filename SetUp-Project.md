CODE

- Clone code từ nhánh chính về (bản mới nhất): git clone http://101.99.14.196:3030/du2-cglobal/support.git (clone code từ dự án support)

- Cài composer (nếu chưa cài): Mặc định dự án sẽ sử dụng nhiều module core, hoặc contribute module (những bản không cần convert). Composer sẽ tự động gọi các module này cho mình, mặc định lưu ở file composer.json ở trong file code clone về. Chạy composer trên git: compose install

- gọi lệnh git checkout để tạo nhanh mới với form_name

- Chú ý: Phần cài đặt mã tập tin thì cái bên phải là utf8, bên trái là utf8-genaral-ci

- Khi clone code với git ms cài lần đầu sẽ bị lỗi ssl -> nhập lệnh sau vào command: 

- git config --global http.sslVerify false Sau đó nhập user password của git

- Sau đó chạy lại lệnh 

  ```
  git config --global http.sslVerify true
  ```

  


  để tránh bị tấn công git

### DATABASE

- Cài **navicat**: search itseo -> có bản crack -> coppy link tải fsare vào trang https://linksvip.net/ để tải max speech

- Confix database MySQL: mở file hosts ở đường dẫn C:\Windows\System32\drivers\etc 

file hosts nếu không lưu được thì phải chạy dưới quyền admin

- Confix file httpd-vhosts.conf ở đường dẫn: C:\xampp\apache\conf\extra

​	dấu //## là comment

​	Bắt đầu từ Listen là tạo đường dẫn cho 1 dự án mới:

 	1. ServerAdmin đặt tên tùy ý
 	2. DocumentRoot là đường dẫn đến thư mục chứa code
 	3. ServerName là tên domain mình đặt cho dự án. ServerName này cũng cần phải khai báo ở file hosts ở trên 
 	4. Với mỗi dự án khác nhau chỉ cần coppy đoạn cofix này xuống dưới, sửa ServerName và cổng đi là được. Chú ý cần bật tắt lại xampp sau khi đã sửa cổng

- Clone code từ server về:

  1. tạo một connection MySql mới, đặt tên là cmc_server hay tùy ý 

  2.  Các thông tin điền theo file wiki của git (wiki ở trong 1 project bất kỳ)

     Chọn data trasfer để clone database về


Chạy project với ServerName đã tạo, thêm cổng ở cuối Ex: support.lc:8001 hoặc http://localhost:8100/

- Chú ý: mặc định giới hạn dung lượng download là 1M, cần configure thành 16M để có thể down thành công !

- **Nếu việc transfer database tự động vào local bị lỗi ko transfer được thì dump database ra rồi import thủ công vào phpmyadmin**

  ##### **Nếu upload db ko được có thể do chưa confix dung lượng upload ở file php.ini**

  max_execution_time = 5000
  max_input_time = 5000
  memory_limit = 1000M
  post_max_size = 750M
  upload_max_filesize = 750M


#### Update user-password drupal su dung git

./vendor/bin/drush upwd admin 123456