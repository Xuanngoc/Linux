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
|-----|-----|
|__-l__ |Lựa chọn này được sử dụng để khoá tài khoản. Một tài khoản bị khoá sẽ có một ký tự ‘!’ đứng trước chuỗi mật mã đã được mã hoá trong tập tin /etc/shadow, đồng thời gán giá trị -1 tại các trường expire và disable trong tập tin|
| __-u__[__-f__]|Mở khoá một tài khoản đã bị khoá (ngược lại lựa chọn –l). Theo mặc định, passwd sẽ không mở khoá tài khoản nào không sử dụng mật mã. Lựa chọn -f bổ sung sẽ cho phép mở khoá tài khoản không sử dụng mật mã|
|__-d__|Xoá bỏ mật mã của tài khoản|

## Xóa tài khoản người dùng - lệnh _userdel_
Lệnh userdel được sử dụng để xoá tài khoản người dùng và các tập tin liên quan đến tài
khoản người dùng đó.<br>
Cú pháp<br>
>>__userdel__ [-r] login

Trong đó login là tên tài khoản người dùng muốn xoá bỏ. Mặc định, khi xoá bỏ tài khoản
người dùng, các tập tin liên quan đến tài khoản đó không bị xoá. Lựa chọn -r trong lệnh này cho phép khi xoá bỏ một tài khoản, thư mục chủ của tài khoản cùng với tập tin thư tín của tài khoản đó cũng sẽ bị xoá.

## Thay đổi thông tin tài khoản người dùng - lệnh _usermod_ 
Lệnh usermod được sử dụng để thay đổi các thông tin về tài khoản người dùng
Cú pháp<br>
>>__usermod__ [option]... login

Trong đó _login_ là tên tài khoản muốn thay đổi thông tin.

|||
|----|----|
|__-L__| Lựa chọn này được sử dụng để khoá tài khoản. Một tài khoản bị khoá sẽ có một ký tự '!' đứng trước chuỗi mật mã đã được mã hoá trong tập tin /etc/shadow. |
|__-U__| Mở khoá một tài khoản đã bị khoá |
|__-l__login_name| Thay đổi tên tài khoản từ login thành login_name. Trong trường hợp thay đổi tên tài khoản, tên thư mục chủ của tài khoản đó không thay đổi. |
|__-u__udi [__-o__]| Giá trị mã số nhận diện người dùng (uid). Giá trị này phải là duy nhất (trừ trường hợp sử dụng với lựa chọn -o). Giá trị này phải là một số dương. Giá trị mặc định là số nhỏ nhất lớn hơn 99 và lớn hơn mọi người dùng khác. Giá trị 0-99 được sử dụng cho các tài khoản hệ thống. |
|__-g__ initial-group| Lựa chọn này cho phép thay đổi nhóm khởi nạp của tài khoản. Tên nhóm hay mã số nhóm (GID) initial_group phải tồn tại. |
|__-G__ group[,...]| Thay đổi nhóm group mà tài khoản người dùng sẽ là thành viên|
|__-e__ expire_date|  Thay đổi thời điểm hết hạn của tài khoản expire_date. Định dạng ngày tháng như sau: YYYY-MM-DD |
|__-s__ shell|  Thay đổi shell đăng nhập của người dùng. Nếu trường shell bỏ trống thì cho phép tài khoản sử dụng shell mặc định của hệ thống |
|__-d__ home_dir| Thay đổi thư mục chủ của tài khoản người dùng thành thư mục home_dir |

Thí dụ: Lệnh sau đây sẽ đổi tên tài khoản _alan_ thành tên _admin_ và gán cho tài khoản này UID=0:<br>
$ __usermod -u 0 -o –l admin alan__

## Thay đổi thông tin mặc định khi tạo tài khoản
Để thay đổi các thông tin mặc định khi tạo một tài khoản người dùng, ta có thể thực hiện bằng cách sử dụng lệnh 
_useradd_ với lựa chọn -D (hay sửa tập tin _/etc/default/useradd_) và/hay sửa đổi thông tin trong tập tin _/etc/login.defs_.

## Thay đổi thông tin tài khoản mặc định - lệnh _useradd_
Ta có thể thực hiện lệnh __useradd__ với lựa chọn –D để xem hay thay đổi các giá trị mặc định khi tạo tài khoản người dùng theo cú pháp sau:<br>
__useradd__ -D [option] ...<br>
Trong trường hợp thi hành lệnh useradd mà không chỉ ra bất kỳ lựa chọn nào, lệnh sẽ hiển thị các giá trị mặc định hiện hành.
Các lựa chọn chính của lệnh:
|||
|-----|----|
|__-b__ *default_home* | Xác định thư mục mặc định (*default_home*) chứa các thư mục chủ của người dùng |
|__-e__ *expire_date*| Xác định thời điểm mà tài khoản sẽ hết hạn sử dụng *expire_date*. Định dạng ngày tháng như sau: YYYY-MM-DD. Mặc định mọi tài khoản đều có khả năng sử dụng vô thời hạn. |
|__-s__ *shell*| Xác định *shell* đăng nhập của người dùng. Shell này sẽ được sử dụng cho tất cả các tài khoản người dùng được tạo sau này |
|__-f__ *default_inact*| Xác định số ngày (*default_inact*) sau khi tài khoản hết hạn sử dụng mà tài khoản vẫn còn có hiệu lực (sau đó tài khoản sẽ bị làm vô hiệu). Giá trị mặc định là -1 : tài khoản bị vô hiệu ngay khi hết  hạn sử dụng tài khoản |
|__-g__ *default_group*| Tên nhóm hay mã số (*default_group*) nhóm đăng nhập khởi nạp của người dùng. Tên nhóm phải tồn tại. |

__Chú ý__: Ta có thể thực hiện thay đổi nội dung của tập tin _/etc/default/useradd_ thay vì sử dụng lệnh __useradd__ -D.

# Group 
## Tạo tài khoản nhóm - lệnh groupadd
---
Lệnh __groupadd__ cho phép tạo một tài khoản nhóm.<br>
Cú pháp lệnh:
>> __groupadd__ [options] group

Trong đó _group_ là tên nhóm muốn tạo. Trên một máy tính, tên nhóm phải là duy nhất. Các lựa chọn chính của lệnh:
|||
|-----|-----|
|**g** gid [__-o__]| Xác định mã nhận diện nhóm (GID). Giá trị này phải là duy nhất (trừ trường hợp sử dụng với lựa chọn -o). Giá trị này phải là một số nguyên dương. Giá trị mặc định là số nhỏ nhất lớn hơn 500 và lớn hơn mọi GID của nhóm khác hiện có. Giá trị từ 0 đến 499 được sử dụng cho các tài khoản nhóm hệ thống. |
|__-r__| Được sử dụng để tạo một tài khoản nhóm hệ thống. Thông thường lựa chọn này được thực hiện bởi các phần mềm. Tài khoản nhóm hệ thống có UID nằm trong khoảng từ 0-499 |
|||
Thí dụ: Để tạo tài khoản nhóm có tên là __sales__ và có GID=10, ta thực hiện lệnh sau:<br>
$ __groupadd -g 10 -o sales__

## Xoá tài khoản nhóm - lệnh _groupdel_
Lệnh __groupdel__ cho phép xoá tài khoản nhóm cùng tất cả các mục từ tham chiếu tới tài nhóm bị xoá đó.<br>
Cú pháp lệnh:
>>__groupdel__ group_name

Trong đó *group_name* là tên tài khoản nhóm muốn xoá.<br>
__Chú ý:__ Ta không thể xoá tài khoản nhóm còn có chứa các tài khoản người dùng. Muốn xoá được tài khoản nhóm, ta phải thực hiện loại bỏ các thành viên ra khỏi nhóm sau đó mới thực hiện xoá tài khoản nhóm.

## Thay đổi thông tin tài khoản nhóm - lệnh _groupmod_

Khi muốn thực hiện thay đổi thông tin về một tài khoản nhóm nào đó, ta có thể sử dụng groupmod với cú pháp như sau:
>> __groupmod__ [option] group

Trong đó _group_ là tên tài khoản nhóm muốn thay đổi thông tin. Các lựa chọn chính của lệnh:
|||
|-----|-----|
|__-g gid [-o]__ |Xác định mã nhận diện tài khoản nhóm (GID). Giá trị này phải là duy nhất (trừ trường hợp sử dụng với lựa chọn -o). Giá trị này phải là một số nguyên dương. Giá trị từ 0 đến 499 được sử dụng cho các tài khoản hệ thống.|
|__-n__ group_name |Thay đổi tên nhóm từ group thành group_name. Chú ý là tên nhóm phải là duy nhất trên một hệ thống|
|||

__Thí dụ:__ Lệnh sau đây cho phép đổi tên tài khoản nhóm sales thành marketing:
$ __groupmod -n sales marketing__ <br>

__Chú ý:__ Khi thay đổi mã nhận diện tài khoản nhóm, ta phải thực hiện thay đổi thủ công các thông tin có tham chiếu đến mã nhận diện tài khoản này.

## Xem thông tin nhận diện tài khoản - lệnh _id_

Lệnh __id__ cho biết thông tin nhận diện tài khoản người dùng bao gồm UID và GID thật (real) và một hay nhiều GID thực tế (effective). Một tài khoản người dùng luôn có một UID và một GID tương ứng (GID này chính là mã nhận diện tài khoản nhóm khởi nạp của người dùng), nhưng họ cũng có thể có một hay nhiều GID thực tế. GID thực tế là những mã nhận diện tài khoản nhóm mà tài khoản người dùng là thành viên của chúng.

Lệnh xem thông tin nhận diện tài khoản người dùng được thi hành theo cú pháp sau:
>>__id__ [option] ... [username]

Trong đó _username_ là tên tài khoản người dùng ta muốn xem thông tin. Trường hợp không chỉ ra _username_, lệnh __id__ sẽ cho biết thông tin về tài khoản người dùng hiện hành.<br>
Khi thi hành lệnh id mà không chỉ ra bất kỳ một lựa chọn nào, lệnh id sẽ hiển thị tất cả các UID và GID có liên quan đến tài khoản muốn xem thông tin. Một số lựa chọn thường dùng của lệnh là:

|||
|-----|-------|
|__-g__ | Chỉ hiển thị GID thật của tài khoản|
|__-u__ |Chỉ hiển thị UID thật của tài khoản|
|__-G__ |Chỉ hiển thị danh sách tất cả các GID của các nhóm mà tài khoản là thành viên |
|||

__Thí dụ:__ Để xem thông tin về tài khoản foo, ta sử dụng lệnh sau:
$ __-id aa32007__
uid=1000(aa32007) gid=1000(aa32007) groups=1000(aa32007),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),113(lpadmin),128(sambashare),130(libvirtd)

## Trở thành người dùng khác - lệnh _su_
Để tạm thời _‘trở thành’_ một người dùng khác, tức là đăng nhập vào hệ thống với tài khoản người dùng khác mà không cần đăng xuất ra khỏi đăng nhập hiện hành, ta có thể sử dụng lệnh __su__<br>
Cú pháp lệnh:
>> __su__ [-] [username]

Lệnh __su__ khi thực hiện không có đối số thì cho phép ta ‘chuyển sang’ người dùng __root__.<br>
Khi thi hành lệnh __su__, hệ thống sẽ xuất hiện lời nhắc yêu cầu nhập mật mã của tài khoản _username_, ngoại trừ rằng khi ta hiện đang đăng nhập với quyền root.<br>
Lệnh su chỉ thực hiện thay đổi tài khoản hiện hành để mà có được quyền truy nhập của tài khoản username. Phần lớn các biến môi trường sẽ giữ nguyên. Các biến môi trường HOME, LOGNAME, và USER sẽ được thay đổi ứng với người dùng username, tất cả các biến môi trường còn lại vẫn sẽ giữ nguyên (được thừa hưởng lại). Do vậy, lệnh su không giống như một đăng nhập bình thường.<br>
Tuy nhiên, nếu thi hành lệnh __su__ với lựa chọn '__-__', tất cả các script khởi nạp, thường được chạy khi người dùng đăng nhập hệ thống, sẽ được thi hành. Do đó sau khi chạy lệnh su với lựa chọn '-', thì coi như ta đã đăng nhập vào hệ thống với tài khoản username qua lệnh __login__.<br>
Lệnh __su__ được sử dụng chủ yếu trong trường hợp người dùng đăng nhập từ xa qua tài khoản thường và sau đó muốn có quyền của root để thi hành các lệnh quản trị.










