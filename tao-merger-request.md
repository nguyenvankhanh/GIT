### Pull code mới nhất về

Nếu đang ở nhán dev: thì thực hiện pull code luôn

#### - xem đang ở nhánh nào:

git branch                                                                                      `

#### Check status


$ git status                                                                                             
                                                            `

#### Tạo Branch moi (mã là mã của task cha)

`git checkout -b 837_validate_field_apply_edit_seminar                         `

### add

$ git add file_thay_doi_code

Chú ý: ko được git add.

#### tạo commit (tên mã cũng là mã của task cha)

`$ git commit -m "Issue #OST-ma_task_cha - create form search and validate exception (ost#ma_redmine)"                `

###### **chú ý**: nếu issue xử lý internal bug thì fomat như sau

$ git commit -m "Issue #OST-ma_task_cha - create form search and validate exception (internal)" 

#### Push code lên branch vừa tạo

`git push origin 837_validate_field_apply_edit_seminar                         `

 + ![1554975383694](C:\Users\nvkhanh\AppData\Roaming\Typora\typora-user-images\1554975383694.png)
 + chú ý là nhánh dev, ko phải master

### Sau đó vào sub task gắn link và assignee cho người review

![1551754253585](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\1551754253585.png)

link merger request

https://source.cmcglobal.com.vn/du2/drupal8-training/merge_requests/17

cái link gắn merequest mà  ko phải giống như trên thì ko được

![1551754285389](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\1551754285389.png)

 làm tương tự ở tag cha

![1551870028272](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\1551870028272.png)

Tạo sub task cần gắn duedate

## Ngoại lệ

### Lấy lại commit khi có một số file add không mong muốn

`$ git reset --soft HEAD^                                                                                                                                                                                                                                                       `

### Sửa lại tên của commit

git commit --amend

gõ chữ i (insert)

kéo chuột lên trên commit và sửa lại tên

sau đó gõ phím esc và ấn (hai chấm):wq

sau đó push lại code theo branch cũ (tuy nhiên phải git push -f thì ms đè được code)

### Ghi đè lên commit trước, mà không tạo ra commit mới

add file tùy ý

`git commit --amend --no-edit                                                  `

sau đó git push -f ...

**Để tạo nhánh mới thì trước hết cần checkout về nhánh dev trước rồi mới tạo nhánh nếu không sẽ ghi đè commit cũ lên nhánh mới này**

**Để add thêm file hoặc add lại file mình đã add thì không cần tạo nhánh mới, dùng git commit --amend hoặc thêm --no-edit nếu không muốn sửa tên commit rồi vào sửa lạ**i

### Xóa file:

git clean -df duong_dan_file

Cách xóa file dùng lệnh git, tương đương với lệnh git rm -rf (lệnh hệ thống)

### Xóa toàn bộ các file đang thay đổi:

`git stash                                                                                                                                                                                                                                                                    `

### Con support:

Vì nó bị dính file rác nên khi tải code về cần chạy lệnh git stash trước để xóa toàn bộ các file rác nêu không khi commit sẽ bị dính conflic

#### Bỏ tất cả các thay đổi trên 1 nhánh bất kỳ

`git reset --hard HEAD~1                                                                                                                                                                                                                                                      

-> chú ý: lệnh này sẽ loại bỏ tất cả các thay đổi và không lưu lại giống như **git stash**

#### Cách pull code mới nhất về khi code local đã bị thay đổi

1. git checkout dev
2. git stash
3. git pull origin
4. git checkout nhanh_hien_tai
5. git merge dev

-> sẽ merge code mới nhất vào nhánh hiện tại mà vẫn giữ được code đang làm

#### Fix conflic code

push code bình thường (add, commit, push)

-> xuất hiện thông báo conflic



git checkout dev (mockup - shanaing d8)

git pull origin

git checkout nhanh_hien_tai

git rebase dev (mockup)

![1561609201553](C:\Users\nvkhanh\AppData\Roaming\Typora\typora-user-images\1561609201553.png)

vào từng mục và Ctrl + D để xem các sự thay đổi ở các file đó, có thể sửa luôn và lưu lại.

![1561609297305](C:\Users\nvkhanh\AppData\Roaming\Typora\typora-user-images\1561609297305.png)

git rebase --continue

git status để kiểm tra xem file vừa sửa conflic đã được add vào nhánh hay chưa (chưa add thì cần add không thì thôi)

git push -f origin ten_nhanh

#### Sửa merge request khi muốn loại bỏ 1 số file sau khi đã push code

rm -rf ten_file_muon_xoa

git add ten_file_muon_xoa

git commit --amend --no-edit

git push -f origin ten_nhanh

#### Lệnh chạy import configure trên drupal (wingarc cs ...)

./vendor/bin/drupal ci

#### Lệnh chạy export configure trên drupal (wingarc cs ...)

./vendor/bin/drupal ce

#### Bật debug d8

`./vendor/bin/drupal site:mode dev                                             `

#### Reset code về nhanh dev

`git reset --hard origin/dev                                                                                                                                                                                                                                                  `

#### thay đổi password

./vendor/bin/drush upwd admin 123456

```

```

#### Chú ý: Khi cài mới module cần phải :

push cả file config/sync/core.extension.yml lên - file này để configure việc bật module -  tức là up file này lên chạy install module sẽ tự động bât