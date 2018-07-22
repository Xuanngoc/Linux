# Các lệnh quản trị người dùng và nhóm người dùng 
---
## Tạo tài khoản người dùng - lệnh _useradd_
Cú pháp:
>> __useradd__ [option] ... login

Trong đó _login_ là tên của tài khoản người dùng, tên tài khoản này phải duy nhất, và phải được bắt đầu phải bằng một chữ cái.<br>
Khi thực hiện lệnh này, useradd thực hiện tạo một tài khoản người dùng mới sử dụng các giá trị được chỉ ra tại dòng lệnh và các giá trị mặc định của hệ thống. Tuỳ thuộc vào các lựa chọn của dòng lệnh, tài khoản người dùng mới sẽ được nhập vào các tập tin hệ thống, thư mục chủ của người dùng sẽ được tạo và các tập tin khởi nạp của người dùng sẽ được sao chép vào thư mục chủ của họ. Trong trường hợp mặc định (không có lựa chọn -n), mỗi tài khoản được tạo sẽ thuộc về một nhóm có tên trùng với tên tài khoản người dùng.

Các lựa chọn chính cảu lệnh:

||| 
|----------|----|
|__-u__ uid [__-o]__ | Giá trị mã nhận diện người dùng (__UID__). Giá trị này phải là duy nhất (trừ trường hợp sử dụng với lựa chọn __-o__). Giá trị này phải là một số dương. Khi không có lựa chọn này, uid của tài khoản được tạo là số nhỏ nhất lớn hơn 99 và lớn hơn mọi uid người dùng khác. Giá trị 0-99 được sử dụng cho các tài khoản hệ thống.|
|__-g__ initial_group | Lựa chọn này cho phép chỉ ra tài khoản nhóm khởi nạp của người dùng initial_group. Tên nhóm hay mã số nhóm (GID) này phải tồn tại.|
|__-G__ group[,...] |Lựa chọn này cho phép chỉ ra một danh sách tên các nhóm group muốn cho người dùng là thành viên|
|-e expire_date |Xác định thời điểm hết hạn sử dụng tài khoản expire_date. Định dạng ngày tháng như sau: YYYY-MM-DD|
|__-s__ shell| Tên shell đăng nhập của người dùng. Khi không sử dụng lựa chọn này, tài khoản sử dụng shell mặc định của hệ thống |
|__-d__ home_dir |Tạo thư mục __home_dir__, thự mục này sẽ là thư mục chủ của người dùng. Trong trường hợp không có lựa chọn này, mặc định hệ thống sẽ tạo thư mục chủ của người dùng trong thư mục _/home/_ |
|__-r__|Được sử dụng để tạo một tài khoản hệ thống (tài khoản có UID nhỏ hơn 100)|
|__-M__ |Khi có lựa chọn này, Linux sẽ không tạo thư mục chủ của người dùng |
|__-m__ [__-k__ skeleton_dir]|Tạo thư mục chủ của người dùng, nếu chưa có. Các tập tin, thư mục có trong thư mục skeleton_dir sẽ được sao chép vào thư chủ nếu sử dụng lựa chọn –k; ngược lại, các tập tin có trong thư mục /etc/skel/ sẽ được sử dụng để thay thế. |

Thí dụ: Để tạo tài khoản người dùng mới với tên __A32007__ có UID=503 và là thành viên của
các nhóm sales, adv, team, ta thi hành lệnh sau:
$ useradd –u 503 –o –G sales,adv,team A32007<br>
Chú ý:
- Mã nhận diện người dùng UID có giá trị nhỏ hơn 100 là người dùng hệ thống
- Mã nhận diện người dùng được phát sinh dựa trên khai báo trong tập tin /
etc/login.defs.

## Thay đổi mật mã tài khoản - lệnh _passwd_

Sau khi tạo xong một tài khoản người dùng, thao tác tiếp theo là phải tạo mật mã truy nhập cho tài khoản người dùng đó. Mặc định, Linux không cho phép tài khoản không có mật mã truy nhập vào hệ thống. Lệnh __passwd__ cho phép ta _tạo mới_ hay _thay đổi_ mật mã của một tài khoản người dùng; lệnh này cũng được sử dụng để khoá hay mở khoá một tài khoản người dùng.<br>
Cú pháp lệnh:
>> __passwd__ [option] [username]

Trong đó _username_ là tên tài khoản muốn tạo hay thay đổi mật mã. Trường hợp không có
đối số _username_, lệnh __passwd__ sẽ thực hiện thay đổi mật mã cho tài khoản hiện hành.
Các lựa chọn của lệnh:
|||
|---|---|
|__-l__|Lựa chọn này được sử dụng để khoá tài khoản. Một tài khoản bị khoá sẽ có một ký tự ‘!’ đứng trước chuỗi mật mã đã được mã hoá trong tập tin /etc/shadow, đồng thời gán giá trị -1 tại các trường expire và disable trong tập tin|
|__-u__[__-f__]   |Mở khoá một tài khoản đã bị khoá (ngược lại lựa chọn –l). Theo mặc định, passwd sẽ không mở khoá tài khoản nào không sử dụng mật mã. Lựa chọn -f bổ sung sẽ cho phép mở khoá tài khoản không sử dụng mật mã|
|__-d__|Xoá bỏ mật mã của tài khoản|





