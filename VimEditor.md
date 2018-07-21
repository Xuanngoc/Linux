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
---
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
---
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
---
Trong __vim__, việc thực hiện sao chép và di chuyển nội dung là rất bất tiện. Để thực hiện sao chép hay di chuyển nội dung, ta cần thực hiện các bước sau:
- Đưa các dòng muốn sao chép/di chuyển vào bộ đệm.
- Di chuyển con trỏ tới điểm mà ta muốn đưa nội dung vào.
- Lấy nội dung từ trong bộ đệm ra.

Các lệnh chủ yếu thường dùng để di chuyển nội dung vào/ra bộ đệm như sau:
|||
|---|---|
|__:r__ |file Chèn tập tin file vào vị trí hiện hành của con trỏ|
|__:co__*num* |Sao chép nội dung, tính từ vị trí con trỏ đến cuối dòng, đến dòng thứ _num_
trong văn bản|
|__:m__*num* |Di chuyển nội dung, tính từ vị trí con trỏ đến cuối dòng, đến dòng thứ _num_ trong văn bản|
|*n*__yy__ |Đưa _n_ dòng, tính từ vị trí con trỏ trở xuống cuối văn bản, vào bộ đệm|
|__y)__|Chép phần nội dung từ vị trí con trỏ đến cuối câu vào bộ đệm|
|__y}__| Chép phần nội dung từ vị trí con trỏ đến cuối đoạn vào bộ đệm|
|__p__| Lấy nội dung của bộ đệm đưa vào văn bản vào sau vị trí hiện hành của con trỏ.|
|__P__ |Lấy nội dung của bộ đệm đưa vào văn bản vào trước vị trí hiện hành của con trỏ.|
|__m__*a*| Đánh dấu dòng hiện hành với tên _a_|
|"bufname | Xác định tên của bộ đệm|

Một cách để thực hiện sao chép là sử dụng các bộ đệm. vim có 26 bộ đệm (được đặt tên
theo 26 chữ cái: a, b ….) mà ta có thể truy nhập bằng cách nhập ký tự " ở phía trước tên bộ đệm. Thí dụ, để đưa 5 dòng (tính từ vị trí con trỏ trở xuống) vào bộ đệm 'a', ta nhập lệnh sau:
>`"a5yy`

Để lấy nội dung trong bộ đệm 'a' vào văn bản, ta chỉ cần di chuyển con trỏ tới vị trí đích và nhập lệnh:
>`"ap`

Ta cũng có thể sao chép nội dung từ một tập tin này sang một tập tin khác, bằng cách thực
hiện ghi chúng xuống một tập tin tạm thời, và sau đó đọc tập tin đó vào tập tin đích. Thí
dụ, thực hiện lệnh sau đây để ghi nội dung từ dòng thứ 3 đến dòng thứ 7 của tập tin hiện
hành vào tập tin tạm thời có tên _temp_:
>`:3, 7w temp`

Ta có thể sửa đổi tập tin tạm thời này. Sau đó, di chuyển con trỏ tới vị trí mong muốn và nhập lệnh :r temp để lấy nội dung từ tập tin temp chèn vào trong tập tin hiện hành. Cách thức đơn giản để di chuyển một khối văn bản là sử dụng cách thức đánh dấu (mark). Để thực hiện điều này, ta di chuyển con trỏ đến dòng đầu tiên trong khối muốn di chuyển và đánh dấu nó bằng lệnh ma. Di chuyển con trỏ đến dòng cuối cùng của khối muốn di chuyển và đánh dấu nó bằng lệnh mb. Sau đó di chuyển con trỏ đến vị trí muốn chuyển khối văn bản đến, và thực hiện lệnh sau:
>`:'a, 'b m`

Lệnh này thực hiện lấy các dòng giữa điểm đánh dấu 'a' và điểm đánh dấu 'b' và di chuyển
tới dòng hiện hành (được chỉ ra bởi dấu chấm).

 ### **_Easier_**
 Di chuyển và sao chép:

__Di chuyển (cut):__
1. Đặt con trỏ soạn thảo vào vị trí bạn muốn bắt đầu di chuyển (cut)
2. Bấm __v__ (hoặc __V__ nếu bạn muốn cut cả dòng).
3. Di chuyển con trỏ đến vị trí cuối đoạn văn bản bạn muốn cut
4. Bấm __d__
5. Di chuyển con trỏ đến vị trí bạn muốn dán (paste)
6. Bấm __p__ để dán vào sau con trỏ, bấm __P__ để dán vào trước con trỏ.

__Sao chép (copy):__
1. Đặt con trỏ soạn thảo vào vị trí bạn muốn bắt đầu sao chép (copy)
2. Bấm __v__ (hoặc V nếu bạn muốn copy cả dòng).
3. Di chuyển con trỏ đến vị trí cuối đoạn văn bản bạn muốn copy
4. Bấm __y__
5. Di chuyển con trỏ đến vị trí bạn muốn dán (paste)
6. Bấm __p__ để dán vào sau con trỏ, bấm __P__ để dán vào trước con trỏ.



















