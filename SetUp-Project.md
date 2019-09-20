### CODE

- Clone code từ nhánh chính về (bản mới nhất): git clone http://101.99.14.196:3030/du2-cglobal/support.git (clone code từ dự án support)

![1546836127776](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\1546836127776.png)

- Cài composer (nếu chưa cài): Mặc định dự án sẽ sử dụng nhiều module core, hoặc contribute module (những bản không cần convert). Composer sẽ tự động gọi các module này cho mình, mặc định lưu ở file composer.json ở trong file code clone về. Chạy composer trên git: compose install

- gọi lệnh git checkout để tạo nhanh mới với form_name: ![1546842343177](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\1546842343177.png)

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

![1546843477768](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\1546843477768.png)

file hosts nếu không lưu được thì phải chạy dưới quyền admin

![1551090860808](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\1551090860808.png)

- Confix file httpd-vhosts.conf ở đường dẫn: C:\xampp\apache\conf\extra

![1546843640248](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\1546843640248.png)

​	dấu //## là comment

​	Bắt đầu từ Listen là tạo đường dẫn cho 1 dự án mới:

 	1. ServerAdmin đặt tên tùy ý
 	2. DocumentRoot là đường dẫn đến thư mục chứa code
 	3. ServerName là tên domain mình đặt cho dự án. ServerName này cũng cần phải khai báo ở file hosts ở trên 
 	4. Với mỗi dự án khác nhau chỉ cần coppy đoạn cofix này xuống dưới, sửa ServerName và cổng đi là được. Chú ý cần bật tắt lại xampp sau khi đã sửa cổng

- Clone code từ server về:

  1. tạo một connection MySql mới, đặt tên là cmc_server hay tùy ý ![1546844166420](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\1546844166420.png)

  2.  Các thông tin điền theo file wiki của git (wiki ở trong 1 project bất kỳ)

     ![1554868679661](C:\Users\nvkhanh\AppData\Roaming\Typora\typora-user-images\1554868679661.png)

- Chọn data trasfer để clone database về

  ![1546844669412](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\1546844669412.png)

![1546844779068](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\1546844779068.png)

Chạy project với ServerName đã tạo, thêm cổng ở cuối Ex: support.lc:8001 hoặc http://localhost:8100/

- Chú ý: mặc định giới hạn dung lượng download là 1M, cần configure thành 16M để có thể down thành công !

- **Nếu việc transfer database tự động vào local bị lỗi ko transfer được thì dump database ra rồi import thủ công vào phpmyadmin**

- ![1552554196113](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\1552554196113.png)

  ##### **Nếu upload db ko được có thể do chưa confix dung lượng upload ở file php.ini**

  max_execution_time = 5000
  max_input_time = 5000
  memory_limit = 1000M
  post_max_size = 750M
  upload_max_filesize = 750M

  ***Chú ý:***
  ***Con ab cần truncate các bảng có chữ cache***

  ![1552647400977](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\1552647400977.png)

  

  ### Sau khi làm các bước trên:

  chạy đường dẫn http://kurashare.lc:8200/ sau chọn thư mục web và cài bình thường

  Cần confix ở file vhost vì với confix đó nó sẽ lắng nge cổng vd:8200 rồi trỏ đến DocumentRoot "C:/xampp/htdocs/kurashare/web". Như vậy sẽ không bị sai 1 số đường dẫn link

  ### Con AB

  cần chạy update trước ![1553053860512](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\1553053860512.png)

  ### Tạo symbol link để chuyển đổi ngôn ngữ:

  C:\WINDOWS\system32>mklink /d C:\xampp\htdocs\cmc-global\ab_site\jp C:\xampp\htdocs\cmc-global\ab_site

  ### Crack PHP storm

  https://ntcde.com/phan-mem-hay/active-phpstorm-2019-voi-license-key-full-crack.html

  https://gist.github.com/me7media/3a7017e0a86f22c8f463774f41e2af34#gistcomment-2877745

### Con OPIGNO 

cần import file .htacess để chạy

### Ở con shanaing và có thể một số con khác:

bị bug không load được js, css -> Vào admin: admin/config/development/performance bỏ tích 2 trường sau và save lại

![1554871851762](C:\Users\nvkhanh\AppData\Roaming\Typora\typora-user-images\1554871851762.png)

```

```

### Wingarc

để chạy được lệnh composer cần configure trong file php.ini

![1558494869699](C:\Users\nvkhanh\AppData\Roaming\Typora\typora-user-images\1558494869699.png)

#### Update user-password wingarc-cs

./vendor/bin/drush upwd admin 123456