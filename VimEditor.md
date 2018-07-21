# Vim editor
---

Trình soạn thảo chuẩn của Linux là __vim__. Để thi hành lệnh vi có nhiều cú pháp khác nhau,nhưng phần lớn vim thường được khởi động để sửa đổi nội dung tập tin với cú pháp cơ bản như sau:<br>
>`vi [file]...`
Một số chú ý:
 - Nếu lệnh __vi__ được khởi động mà không có tên tập tin hay tên tập tin chưa tồn tại,
thì __vi__ sẽ khởi động với một bộ đệm (_buffer_) rỗng..
 - Trong trường hợp tên tập có ký tự '-' đứng đầu, thì ta phải thêm ký tự '--' ở phía
trước.
 - Nếu __vi__ được khởi động với nhiều hơn một tập tin. Tập tin đầu tiên trong danh sách sẽ là tập tin hiện hành và được đọc vào trong bộ đệm.

__Vim__ có 2 chế  độ làm việc chính: Insert mode và Command mode.

    - Command mode: mọi thứ ta nhập vào đều được chương trình xử lý như là _lệnh_.
    - Insert mode: mọi thứ ta nhập vào đều được coi là nôi dung và được đưa vài văn bản.

Để chuyển từ _chế độ soạn thảo_ sang _chế độ lệnh_, nhấn phím __[Esc]__; ngược lại, để chuyển từ _chế độ lệnh_ sang _chế độ soạn thảo_, nhấn __[Ins]__ hay phím chữ cái bất kỳ.

Khi làm việc với __vim__ ta cần biết đến các định nghĩa về từ, câu và đoạn trong __vim__:
- Một từ là bất kỳ chuỗi ký tự nào được phân ranh giới bởi các khoảng trắng hay dấu
chấm câu, mặc dù bản thân mỗi ký tự dấu chấm câu cũng là một từ.
- Một câu là một chuỗi ký tự kết thúc bằng một dấu chấm và sau đó là hai khoảng
trắng.
- Một đoạn là chuỗi ký tự kết thúc bằng hai ký tự xuống hàng (các đoạn được phân
cách nhau bằng một dòng trắng).

## Các lệnh cơ bản trong VI
| Lệnh | Chức năng |
|------------|--------|
|__:help__ |Mở hướng dẫn sử dụng vim|
|__:w__[file] | Ghi lại nội dung tập tin. Nếu tập tin đang soạn thảo chưa có tên, ta phải chỉ ra tên tập tin _file_ |
| __:q__ | Thoát khỏi vim; __:q!__ thoát khỏi vim mà không ghi lại tập tin; :qa! thoát khỏi vim mà không ghi lại tất cả các tập tin đang mở; :wq thực hiện ghi lại tập tin trước khi thoát |
|__:next__| Chuyển tới bộ đệm (tập tin) kế tiếp (trong trường hợp vim mở đồng thời  nhiều tập tin)|
|__:prev__| Chuyển tới bộ đệm (tập tin) kế trước (trong trường hợp vim mở đồng thời nhiều tập tin) |
|__:e__ _file_|Đóng tập tin hiện hành và mở tập tin _file_|
|__:sh__|Chuyển tạm sang shell để thi hành các lệnh của shell. Để từ shell quay trở lại vim, nhập exit tại lời nhắc lệnh shell |

## Di chuyển trong văn bản
---
| Lệnh | Chức năng |
|--------|------|
|__[[__|Chuyển lên đầu văn bản|
|__]]__|Chuyển lên màn hình trước|
|[__Ctrl-F__]|Chuyển lên màn hình trước|
|[__Ctrl-B__]|Chuyển xuống màn hình sau|
|[__Enter__]|Chuyển xuống đầu dòng kế tiếp|
|*n*__G__| Chuyển đến dòng thứ _n_. Nếu không có _n_, lệnh G chuyển xuống dòng cuối cùng của văn bản. Số dòng hiện hành có thể được hiển thị bằng cách nhấn __[Ctrl-G]__ |
|__w__| Chuyển lên trước một từ. Nếu sử dụng __W__ thì không coi dấu chấm là một từ |
|__b__| Chuyển về sau một từ. Nếu sử dụng __B__ thì không coi dấu chấm là một từ |
|__(__| Chuyển lên câu trước |
|__)__| Chuyển xuống câu sau |
|__{__| Chuyển tới cuối đoạn trước |
|__}__| Chuyển tới cuối đoạn hiện hành (đầu đoạn kế tiếp) |

__Chú ý:__ Ngoài các lệnh di chuyển con trỏ trên, ta cũng có thể sử dụng các phím mũi tên,
phím [Home], [End], [Ins]… để di chuyển trong văn bản (trong chế độ lệnh cũng như trong
chế độ soạn thảo).

## Các lệnh xóa, sửa
---
| Lệnh | Chức năng |
|--------|------|
|__u__| Huỷ bỏ lệnh vừa thực hiện |
|__.__| Lập lại thay đổi được thực hiện sau cùng |
|__x__| Xoá một ký tự tại vị trí con trỏ |
|__dw__| Xoá một từ tại vị trí con trỏ |
|__dd__| Xoá dòng hiện hành |
|__D__| Xoá phần cuối dòng tính từ vị trí con trỏ |
|__d0__| Xoá phần đầu dòng tính từ vị trí con trỏ |
|__r__| Thay thế một ký tự tại vị trí con trỏ |
|__cw__| Xoá từ tại vị trí con trỏ và chuyển về chế độ soạn thảo |
|__o__|Chèn một dòng trắng phía dưới dòng hiện hành, và chuyển về chế độ soạn thảo|
|__O__|Chèn một dòng trắng phía trên dòng hiện hành, và chuyển về chế độ soạn thảo|
|__a__|Chuyển về chế độ soạn thảo, và cho phép nhập nội dung vào sau vị trí con trỏ|
|__A__|Chuyển về chế độ soạn thảo và di chuyển con trỏ tới cuối dòng|
|__i__|Chuyển về chế độ soạn thảo và cho phép nhập nội dung vào trước vị trí con trỏ|
|__I__|Chuyển về chế độ soạn thảo và di chuyển con trỏ tới đầu dòng|
|__R__| Chuyển sang chế độ ghi đè (trong chế độ soạn thảo) |

__Chú ý:__ Nhiều lệnh vim chấp nhận một sự đếm lặp trước khi thực hiện bản thân lệnh. Thí
dụ, lệnh dd xoá một dòng, và có thể nhập vào một số đứng trước lệnh dd để chỉ ra số dòng
bị xoá, như là 4dd để xoá 4 dòng.

## Các lệnh liên quan đến tìm kiếm, thay thế 
| Lệnh | Chức năng |
|--------|------|
|__/__*string* | Thực hiện tìm chuỗi string trong văn bản từ trên xuống. Để thực hiện tìm ngược từ dưới lên trên, sử dụng __?__ thay thế cho __/__. |
|__n__|Thực hiện tìm kiếm tiếp tục|
|__N__|Thực hiện tìm kiếm tiếp tục theo chiều ngược lại|
|:n1,n2 __s/__*string*__/__ replace __/g__ |Thực hiện tìm kiếm chuỗi pattern và thay thế bằng chuỗi replace từ dòng thứ n1 đến dòng n2|
|:1,$ __s/__*string*__/__ replace __/g__| Thực hiện tìm kiếm chuỗi pattern và thay thế bằng chuỗi replace trong toàn bộ văn bản. Ta cũng có thể dùng cú pháp sau: __:g/__ pattern __/s//__ replace __/__ |

__Chú ý:__ Trong trường hợp muốn tìm kiếm những ký tự đặc biệt, ta phải nhập ký tự __\\__ ở phía trước ký tự đặc biệt.

Thí dụ:
Nhập lệnh __/__ cat để tìm chuỗi _'cat'_. Sau đó nhập lệnh __cw__ và nhập chuỗi _'dog'_ để thay thế chuỗi 'cat'. Nhấn [Esc] để quay trở lại chế độ lệnh. Để tiếp tục tìm, nhập lệnh __n__ và sau đó nhấn __.__ để thực hiện thay thế.
Để thay thế toàn bộ các ký tự $ bằng chuỗi **, ta nhập lệnh sau:
__:g/__\$__/s//__\*\*__/g__.

## Sao chép, di chuyển nội dung 


















