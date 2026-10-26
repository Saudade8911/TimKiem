# Quản lý sản phẩm bằng mảng

## Giới thiệu

Chương trình cài đặt các chức năng đọc dữ liệu sản phẩm từ tệp TXT, hiển thị danh sách, tìm kiếm tuần tự, sắp xếp và tìm kiếm nhị phân trong C++.

Chương trình sử dụng mảng để lưu trữ danh sách sản phẩm, thực hiện các thao tác tìm kiếm và thống kê số lần so sánh trong quá trình tìm kiếm.

Thông tin mỗi sản phẩm bao gồm mã sản phẩm, tên sản phẩm, đơn giá và số lượng.

## Cấu trúc dữ liệu

cpp
struct SanPham {
    string maSP;
    string tenSP;
    int donGia;
    int soLuong;
};

SanPham ds[1000], dsSapXep[1000];
int n = 0;


Trong đó:

- `maSP`: Mã sản phẩm.
- `tenSP`: Tên sản phẩm.
- `donGia`: Đơn giá sản phẩm.
- `soLuong`: Số lượng sản phẩm.
- `ds[1000]`: Mảng lưu danh sách sản phẩm ban đầu.
- `dsSapXep[1000]`: Mảng lưu bản sao danh sách sản phẩm đã sắp xếp.
- `n`: Số lượng sản phẩm được đọc từ tệp.

## Cấu trúc tệp dữ liệu

Chương trình sử dụng tệp `san_pham.txt` để lưu thông tin sản phẩm.

Dòng đầu tiên chứa số lượng sản phẩm. Các dòng tiếp theo chứa thông tin từng sản phẩm theo định dạng:

text
Số lượng sản phẩm
Mã sản phẩm|Tên sản phẩm|Đơn giá|Số lượng


Ví dụ:

text
5
SP103|Ban_phim_co|750000|8
SP101|USB_32GB|125000|50
SP105|Tai_nghe|325000|17
SP102|Lot_chuot|55000|40
SP104|Chuot_khong_day|185000|26


Các trường dữ liệu được phân cách bằng ký tự `|`.

Chương trình kiểm tra số lượng sản phẩm, định dạng dữ liệu và mã sản phẩm trùng nhau.

## Các chức năng

### 1. Đọc tệp TXT và in danh sách

Cho phép đọc dữ liệu sản phẩm từ tệp `san_pham.txt`.

Chương trình thực hiện:

- Mở tệp dữ liệu bằng `ifstream`.
- Đọc số lượng sản phẩm.
- Đọc thông tin từng sản phẩm.
- Tách các trường dữ liệu dựa trên ký tự `|`.
- Kiểm tra định dạng dữ liệu và mã sản phẩm trùng nhau.
- Lưu thông tin vào mảng `ds`.
- Hiển thị danh sách sản phẩm sau khi đọc thành công.

Các hàm sử dụng:

- `docTep()`: Đọc và kiểm tra dữ liệu từ tệp.
- `inDanhSach()`: In danh sách sản phẩm.

Bảng hiển thị gồm các cột:

`MaSP | TenSP | DonGia | SoLuong`

### 2. Tìm kiếm tuần tự

Cho phép tìm kiếm sản phẩm theo mã sản phẩm trong mảng ban đầu `ds`.

Hàm chính: `timKiemTuanTu()`.

Nguyên lý hoạt động:

1. Bắt đầu từ phần tử đầu tiên của mảng.
2. So sánh mã sản phẩm cần tìm với mã của từng phần tử.
3. Nếu tìm thấy, lưu vị trí và kết thúc tìm kiếm.
4. Nếu duyệt hết mảng mà không tìm thấy, thông báo không tìm thấy sản phẩm.
5. Đếm và hiển thị số lần so sánh.

Nếu tìm thấy, chương trình hiển thị mã sản phẩm, tên sản phẩm, đơn giá, số lượng và vị trí trong mảng gốc.

### 3. Sắp xếp và tìm kiếm nhị phân

Chức năng này sao chép danh sách sản phẩm sang mảng `dsSapXep`, sắp xếp tăng dần theo mã sản phẩm và thực hiện tìm kiếm nhị phân.

**Hàm `saoChepVaSapXep()`**

- Sao chép dữ liệu từ mảng `ds` sang mảng `dsSapXep`.
- So sánh mã sản phẩm giữa các phần tử.
- Hoán đổi vị trí để sắp xếp mã sản phẩm theo thứ tự tăng dần.
- Hiển thị danh sách đã sắp xếp.

**Hàm `timKiemNhiPhan()`**

Nguyên lý hoạt động:

1. Khởi tạo hai biến `trai` và `phai` để xác định phạm vi tìm kiếm.
2. Tính vị trí giữa bằng công thức `(trai + phai) / 2`.
3. So sánh mã sản phẩm cần tìm với mã tại vị trí giữa.
4. Nếu hai mã bằng nhau, tìm thấy sản phẩm và kết thúc.
5. Nếu mã cần tìm lớn hơn, tiếp tục tìm ở nửa bên phải.
6. Nếu mã cần tìm nhỏ hơn, tiếp tục tìm ở nửa bên trái.
7. Nếu phạm vi tìm kiếm không còn phần tử, thông báo không tìm thấy.

Nếu tìm thấy, chương trình hiển thị thông tin sản phẩm, vị trí trong mảng đã sắp xếp và số lần so sánh.

**Lưu ý:** Tìm kiếm nhị phân yêu cầu danh sách đã được sắp xếp theo mã sản phẩm. Chương trình sử dụng mảng bản sao nên không làm thay đổi thứ tự của danh sách gốc.

### 4. Thoát chương trình

Cho phép người dùng kết thúc chương trình bằng cách chọn chức năng 4.

## Các hàm chính

| Hàm | Chức năng |
|---|---|
| `docTep()` | Đọc dữ liệu sản phẩm từ tệp TXT và kiểm tra dữ liệu |
| `inDanhSach()` | In danh sách sản phẩm |
| `saoChepVaSapXep()` | Sao chép và sắp xếp sản phẩm tăng dần theo mã |
| `timKiemTuanTu()` | Tìm kiếm sản phẩm bằng phương pháp tuần tự |
| `timKiemNhiPhan()` | Tìm kiếm sản phẩm bằng phương pháp nhị phân |
| `main()` | Hiển thị menu và điều khiển các chức năng |

## Cách chạy chương trình

Có thể biên dịch và chạy chương trình bằng các môi trường lập trình C++ như:

- Code::Blocks
- Dev-C++
- Visual Studio
- Visual Studio Code kết hợp GCC/G++

Đặt tệp `san_pham.txt` trong thư mục làm việc phù hợp với đường dẫn mà chương trình sử dụng để mở tệp.

Sau khi chạy, menu chính xuất hiện:

text
===== MENU CHINH =====
1. Doc tep TXT va in danh sach
2. Tim kiem tuan tu
3. Sap xep va tim kiem nhi phan
4. Thoat
Nhap lua chon:


### Chức năng 1: Đọc tệp TXT và in danh sách

Chọn `1`.

Kết quả: Chương trình đọc dữ liệu từ tệp, kiểm tra thông tin và hiển thị danh sách sản phẩm. Nếu dữ liệu không hợp lệ, chương trình thông báo lỗi tương ứng.

### Chức năng 2: Tìm kiếm tuần tự

Chọn `2`, sau đó nhập mã sản phẩm cần tìm.

Ví dụ:

text
Nhap ma san pham can tim: SP105


Nếu sản phẩm tồn tại, chương trình hiển thị thông tin, vị trí trong mảng gốc và số lần so sánh.

### Chức năng 3: Sắp xếp và tìm kiếm nhị phân

Chọn `3`.

Chương trình sao chép danh sách, sắp xếp tăng dần theo mã sản phẩm và hiển thị danh sách đã sắp xếp. Sau đó, người dùng nhập mã sản phẩm cần tìm.

Kết quả: Chương trình hiển thị thông tin sản phẩm nếu tìm thấy hoặc thông báo không tìm thấy, kèm theo số lần so sánh.

### Chức năng 4: Thoát

Chọn `4` để kết thúc chương trình.

## Kiểm thử

### Test 1: Đọc tệp và in danh sách

Lựa chọn:

text
1


Kết quả mong đợi:

- Đọc được dữ liệu từ tệp `san_pham.txt`.
- Hiển thị danh sách sản phẩm.
- Cho phép sử dụng các chức năng tìm kiếm sau khi đọc thành công.

### Test 2: Tìm kiếm tuần tự với mã tồn tại

Lựa chọn:

text
1
2
SP105


Kết quả mong đợi:

- Tìm thấy sản phẩm có mã `SP105`.
- Hiển thị thông tin sản phẩm.
- Hiển thị vị trí trong mảng gốc và số lần so sánh.

### Test 3: Tìm kiếm tuần tự với mã không tồn tại

Lựa chọn:

text
1
2
SP999


Kết quả mong đợi:

text
KET QUA TIM KIEM TUAN TU
Khong tim thay san pham!


Chương trình hiển thị số lần so sánh đã thực hiện.

### Test 4: Sắp xếp và tìm kiếm nhị phân

Lựa chọn:

text
1
3
SP105


Kết quả mong đợi:

- Danh sách được sao chép và sắp xếp tăng dần theo mã sản phẩm.
- Tìm thấy sản phẩm `SP105` nếu mã tồn tại trong dữ liệu.
- Hiển thị vị trí trong mảng đã sắp xếp và số lần so sánh.

### Test 5: Tìm kiếm nhị phân với mã không tồn tại

Lựa chọn:

text
1
3
SP999


Kết quả mong đợi:

text
KET QUA TIM KIEM NHI PHAN
Khong tim thay san pham!


Chương trình hiển thị thêm số lần so sánh đã thực hiện.

### Test 6: Tìm kiếm trước khi đọc tệp

Chọn `2` hoặc `3` khi chưa đọc tệp thành công.

Kết quả mong đợi:

text
Hay doc tep truoc!


## Đặc điểm của chương trình

- Sử dụng `struct SanPham` để quản lý thông tin sản phẩm.
- Sử dụng mảng tĩnh để lưu trữ dữ liệu, không sử dụng `vector`.
- Đọc dữ liệu từ tệp TXT bằng `ifstream`.
- Sử dụng ký tự `|` để phân tách các trường dữ liệu.
- Kiểm tra số lượng sản phẩm, định dạng dữ liệu và mã sản phẩm trùng nhau.
- Có chức năng in danh sách sản phẩm.
- Có chức năng tìm kiếm tuần tự trên mảng ban đầu.
- Có chức năng sao chép và sắp xếp sản phẩm tăng dần theo mã.
- Có chức năng tìm kiếm nhị phân trên mảng đã sắp xếp.
- Thống kê số lần so sánh trong cả hai phương pháp tìm kiếm.
- Có menu để người dùng lựa chọn và kiểm thử từng chức năng.
- Yêu cầu đọc tệp thành công trước khi thực hiện tìm kiếm.
- Giữ nguyên danh sách gốc khi thực hiện sắp xếp trên bản sao.

## Tác giả

- Họ tên: Phạm Tùng Lâm - A52505
- Lớp: TC3801
- Môn: Cấu trúc dữ liệu và giải thuật
- Bài thực hành: Đọc tệp TXT, sắp xếp và tìm kiếm sản phẩm bằng mảng
