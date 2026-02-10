 HỆ THỐNG FEEDBACK ONLINE

## SRS - Tài liệu đặc tả yêu cầu phần mềm
**Version 1.0**

**Đà Nẵng, 5/2019**

---

## LỊCH SỬ TÀI LIỆU

| Ngày | Tổng thay đổi | Phiên bản |
|------|---------------|-----------|
| 26/5/2019 | Bản đầu tiên | Ver 1.0 |

---

## TÀI LIỆU THAM KHẢO

| Tên tài liệu | Mô tả |
|--------------|-------|
| | |

---

## ĐÓNG GÓP VÀ PHÊ DUYỆT

| Tên | Tiêu đề |
|-----|---------|
| | |

---

## I. GIỚI THIỆU

### 1. Mục đích
Xây dựng hệ thống đánh giá chất lượng giảng viên và nội dung đào (tại các cơ sở đào tạo).

### 2. Phạm vi
Được sử dụng trong các cơ sở đào tạo có quy mô vừa và nhỏ.

---

## II. TỔNG QUAN ĐỀ TÀI

| Loại người dùng | Mô tả |
|-----------------|-------|
| **Admin** (Quản lý cơ sở đào tạo hoặc cán bộ quản lý giáo vụ) | Có quyền tạo account học viên. Quản lý template feedback, quản lý lớp học viên, xem kết quả feedback. |
| **User** (Học viên) | Có quyền đánh giá feedback. |

---

## III. MÔ TẢ CHỨC NĂNG CHO LOẠI NGƯỜI DÙNG ADMIN

### 1. Đăng nhập

| Thuộc tính | Nội dung |
|------------|----------|
| **Tên chức năng** | Đăng nhập |
| **Yêu cầu tổng quát** | Cho phép admin được quyền đăng nhập vào hệ thống |
| **Loại người dùng được sử dụng** | Admin |
| **Mô tả chức năng** | Đăng nhập bằng cách nhập username và password |
| **Điều kiện tiên quyết** | |
| **Cách truy cập** | http://localhost:8080/FeedbackOnline/LoginServlet (Lưu ý: localhost:8080 có thể thay đổi tùy theo địa chỉ IP và Port của server thực tế) |

#### Nội dung màn hình

| Mục | Kiểu | Dữ liệu | Mô tả |
|-----|------|---------|-------|
| Username | TextField - String(50) | [ADMIN].[Username] | Bắt buộc nhập. |
| Password | TextField - String(50) | [ADMIN].[Password] | Bắt buộc nhập. |

#### Hành động

| Tên hành động | Mô tả | Thành công | Thất bại |
|---------------|-------|------------|----------|
| Login | Đăng nhập vào hệ thống | Hiển thị trang chủ | Hiển thị message "Login failed. Invalid username or password" |
| Trang đăng nhập cho user | Mở trang đăng nhập cho User | | |

---

### 2. Trang chủ

| Thuộc tính | Nội dung |
|------------|----------|
| **Tên chức năng** | Trang chủ |
| **Yêu cầu tổng quát** | Hiển thị toàn bộ các chức năng chính của admin |
| **Loại người dùng được sử dụng** | Admin |

---

### 3. Tạo mới template

| Thuộc tính | Nội dung |
|------------|----------|
| **Tên chức năng** | Tạo mới template |
| **Yêu cầu tổng quát** | Cho phép tạo mới 1 template (bao gồm các câu hỏi dùng để đánh feedback) |
| **Loại người dùng được sử dụng** | Admin |
| **Mô tả chức năng** | Tạo mới template feedback bao gồm các câu hỏi |
| **Điều kiện tiên quyết** | Đăng nhập thành công |

---

### 4. Sửa template

Tương tự như chức năng Tạo mới template. Riêng TextField Tên template bị disable.

---

### 5. Quản lý template

| Thuộc tính | Nội dung |
|------------|----------|
| **Tên chức năng** | Quản lý template |
| **Yêu cầu tổng quát** | Hiển thị danh sách template |
| **Loại người dùng được sử dụng** | Admin |

---

### 6. Tạo mới lớp

| Thuộc tính | Nội dung |
|------------|----------|
| **Tên chức năng** | Tạo mới lớp |
| **Yêu cầu tổng quát** | Cho phép tạo mới 1 lớp |
| **Loại người dùng được sử dụng** | Admin |
| **Điều kiện tiên quyết** | Đăng nhập thành công |

#### Nội dung màn hình

| Mục | Kiểu | Dữ liệu | Mô tả |
|-----|------|---------|-------|
| Mã lớp | TextField - String(50) | [LOP].[MaLop] | |
| Tên lớp | TextField - String(50) | [LOP].[TenLop] | |
| Template | Combobox | [TEMPLATE].[TenTemplate] | |

#### Hành động

| Tên hành động | Mô tả | Thành công | Thất bại |
|---------------|-------|------------|----------|
| Hoàn tất | Thêm mới 1 lớp vào DB | Hiển thị thông báo "Thêm Lớp thành công" | Nếu chưa điền mã lớp: "Bạn chưa điền vào mã lớp!". Nếu chưa điền tên lớp: "Bạn chưa điền tên lớp!" |
| Reset | Xóa toàn bộ dữ liệu đang nhập trên màn hình | | |
| Back | Quay về màn hình Quản lý lớp | | |

---

### 7. Sửa lớp

Tương tự như chức năng Tạo mới lớp. Riêng TextField **Mã lớp bị disable (read-only)**.

---

### 8. Quản lý lớp

| Thuộc tính | Nội dung |
|------------|----------|
| **Tên chức năng** | Quản lý lớp |
| **Yêu cầu tổng quát** | Hiển thị danh sách lớp |
| **Loại người dùng được sử dụng** | Admin |

#### Nội dung màn hình

| Mục | Kiểu | Dữ liệu | Mô tả |
|-----|------|---------|-------|
| STT | Label | Tự động tăng theo thứ tự | |
| Mã lớp | Label | [LOP].[MaLop] | |
| Tên lớp | Label | [LOP].[TenLop] | |
| Template | Label | [TEMPLATE].[TenTemplate] | |

#### Hành động

| Tên hành động | Mô tả | Thành công | Thất bại |
|---------------|-------|------------|----------|
| Sửa | Mở màn hình Sửa lớp | | |
| Xóa | Xóa 1 lớp trong danh sách. Hiển thị popup confirm với message "Bạn có chắc chắn muốn xóa lớp này không?" trước khi xóa. | Sau khi xóa thành công thì quay về màn hình Quản lý lớp | |

---

### 9. Tạo mới học viên

| Thuộc tính | Nội dung |
|------------|----------|
| **Tên chức năng** | Tạo mới học viên |
| **Yêu cầu tổng quát** | Cho phép tạo mới 1 học viên (sau khi đã tạo lớp tương ứng) |
| **Loại người dùng được sử dụng** | Admin |
| **Mô tả chức năng** | Tạo mới học viên cho 1 lớp nào đó (lớp đã được tạo trước) |
| **Điều kiện tiên quyết** | Đăng nhập thành công |
| **Cách truy cập** | Xuất phát từ màn hình Quản lý học viên, kích chọn button Tạo mới học viên |

#### Nội dung màn hình

| Mục | Kiểu | Dữ liệu | Mô tả |
|-----|------|---------|-------|
| Account học viên | TextField - String(50) | [HOCVIEN].[MaHocVien] | |
| Tên học viên | TextField - String(50) | [HOCVIEN].[TenHocVien] | |
| Lớp | Combobox | [LOP].[TenLop] | Giá trị mặc định là item đầu tiên trong danh sách |

#### Hành động

| Tên hành động | Mô tả | Thành công | Thất bại |
|---------------|-------|------------|----------|
| Hoàn tất | Thêm mới 1 học viên vào DB | Hiển thị thông báo "Thêm Học Viên thành công". Reset toàn bộ các field. | Nếu chưa điền mã học viên: "Bạn chưa điền mã Học Viên!". Nếu chưa điền tên: "Bạn chưa điền tên Học Viên!" |
| Reset | Xóa toàn bộ dữ liệu đang nhập trên màn hình | | |

---

### 10. Chỉnh sửa học viên

Tương tự như chức năng Tạo mới học viên. Riêng TextField **Account học viên bị disable (read-only)**.

---

### 11. Quản lý học viên

| Thuộc tính | Nội dung |
|------------|----------|
| **Tên chức năng** | Quản lý học viên |
| **Yêu cầu tổng quát** | Hiển thị danh sách học viên |
| **Loại người dùng được sử dụng** | Admin |
| **Mô tả chức năng** | Hiển thị danh sách học viên (tất cả học viên hoặc phân theo lớp). Có bao gồm chức năng xóa học viên. |
| **Điều kiện tiên quyết** | Đăng nhập thành công |
| **Cách truy cập** | Xuất phát từ menu trái, kích vào link Học viên |

#### Nội dung màn hình

| Mục | Kiểu | Dữ liệu | Mô tả |
|-----|------|---------|-------|
| STT | Label | Tự động tăng theo thứ tự | |
| Account | Label | [HOCVIEN].[MaHocVien] | |
| Tên học viên | Label | [HOCVIEN].[TenHocVien] | |
| Tên lớp | Label | [LOP].[TenLop] | |
| Lớp | Combobox | [LOP].[TenLop] | Giá trị mặc định là "Lớp". Khi chọn "Lớp" thì hiển thị toàn bộ học viên. |

#### Hành động

| Tên hành động | Mô tả | Thành công | Thất bại |
|---------------|-------|------------|----------|
| Sửa | Mở màn hình Sửa học viên | | |
| Xóa | Xóa một học viên | Hiển thị popup confirm trước khi xóa | |
| Tạo mới học viên | Mở màn hình Tạo mới học viên | | |
| Tạo mới học viên theo file | Mở màn hình Tạo mới nhiều học viên cùng lúc theo cách import file | | |
| Hướng dẫn import file | Mở file hướng dẫn cách import danh sách học viên theo file | | |

---

### 12. Tạo mới học viên theo file

| Thuộc tính | Nội dung |
|------------|----------|
| **Tên chức năng** | Tạo mới học viên theo file |
| **Yêu cầu tổng quát** | Cho phép import nhiều học viên cùng lúc của một lớp nào đó |
| **Loại người dùng được sử dụng** | Admin |
| **Mô tả chức năng** | Chọn file đã điền đầy đủ thông tin theo mẫu có sẵn. Sau đó cho phép lưu nhiều học viên của cùng 1 lớp vào DB. |
| **Điều kiện tiên quyết** | Đăng nhập thành công |

#### Nội dung màn hình

| Mục | Kiểu | Dữ liệu | Mô tả |
|-----|------|---------|-------|
| Chọn file | Hộp chọn file | | |
| Lớp | Combobox | [LOP].[TenLop] | |

#### Hành động

| Tên hành động | Mô tả | Thành công | Thất bại |
|---------------|-------|------------|----------|
| Hoàn tất | Import học viên từ file | Quay về màn hình Quản lý học viên | |
| Reset | Xóa toàn bộ dữ liệu đang nhập | | |

---

### 13. Tạo mới trainer

| Thuộc tính | Nội dung |
|------------|----------|
| **Tên chức năng** | Tạo mới trainer |
| **Yêu cầu tổng quát** | Cho phép tạo mới 1 trainer |
| **Loại người dùng được sử dụng** | Admin |
| **Điều kiện tiên quyết** | Đăng nhập thành công |
| **Cách truy cập** | Xuất phát từ màn hình Quản lý trainer, kích chọn button Tạo mới trainer |

#### Nội dung màn hình

| Mục | Kiểu | Dữ liệu | Mô tả |
|-----|------|---------|-------|
| Account trainer | TextField - String(50) | [TRAINER].[MaTrainer] | |
| Họ tên | TextField - String(50) | [TRAINER].[TenTrainer] | |

#### Hành động

| Tên hành động | Mô tả | Thành công | Thất bại |
|---------------|-------|------------|----------|
| Hoàn tất | Thêm mới 1 trainer vào DB | Quay về màn hình Quản lý trainer. Hiển thị "Thêm trainer thành công" | Nếu chưa điền Account trainer: "Bạn chưa điền Account trainer!". Nếu chưa điền họ tên: "Bạn chưa điền họ tên!". Nếu họ tên có chứa số thì báo lỗi. |
| Reset | Xóa toàn bộ dữ liệu đang nhập | | |
| Back | Quay về màn hình Quản lý trainer | | |

---

### 14. Sửa trainer

Tương tự như chức năng Tạo mới trainer. Riêng TextField **Account trainer bị disable (read-only)**.

---

### 15. Quản lý trainer

| Thuộc tính | Nội dung |
|------------|----------|
| **Tên chức năng** | Quản lý trainer |
| **Yêu cầu tổng quát** | Hiển thị danh sách trainer |
| **Loại người dùng được sử dụng** | Admin |
| **Mô tả chức năng** | Hiển thị danh sách tất cả trainer. Có bao gồm chức năng xóa trainer. |
| **Điều kiện tiên quyết** | Đăng nhập thành công |
| **Cách truy cập** | Xuất phát từ menu trái, kích vào link Trainer |

#### Nội dung màn hình

| Mục | Kiểu | Dữ liệu | Mô tả |
|-----|------|---------|-------|
| STT | Label | Tự động tăng theo thứ tự | |
| Account | Label | [TRAINER].[MaTrainer] | |
| Tên trainer | Label | [TRAINER].[TenTrainer] | |

#### Hành động

| Tên hành động | Mô tả | Thành công | Thất bại |
|---------------|-------|------------|----------|
| Sửa | Mở màn hình Sửa trainer | | |
| Xóa | Xóa một trainer | Hiển thị popup confirm trước khi xóa | |
| Tạo mới trainer | Mở màn hình Tạo mới trainer | | |

---

### 16. Tạo mới topic

| Thuộc tính | Nội dung |
|------------|----------|
| **Tên chức năng** | Tạo mới topic |
| **Yêu cầu tổng quát** | Cho phép tạo mới 1 topic (1 topic trong 1 môn học nào đó) |
| **Loại người dùng được sử dụng** | Admin |
| **Mô tả chức năng** | Cho phép tạo mới 1 topic. Hệ thống này không quản lý các subject (môn học) mà chỉ quản lý các topic cụ thể của các môn học. |
| **Điều kiện tiên quyết** | Đăng nhập thành công |
| **Cách truy cập** | Xuất phát từ màn hình Quản lý topic, kích chọn button Tạo mới topic |

#### Nội dung màn hình

| Mục | Kiểu | Dữ liệu | Mô tả |
|-----|------|---------|-------|
| Tên topic | TextField - String(50) | [TOPIC].[TenTopic] | |

#### Hành động

| Tên hành động | Mô tả | Thành công | Thất bại |
|---------------|-------|------------|----------|
| Hoàn tất | Thêm mới 1 topic vào DB | Quay về màn hình Quản lý topic. Hiển thị "Thêm Topic thành công" | Nếu chưa điền Tên topic: "Bạn chưa điền Tên Topic!" |
| Reset | Xóa toàn bộ dữ liệu đang nhập | | |
| Back | Quay về màn hình Quản lý topic | | |

---

### 17. Sửa topic

Tương tự như chức năng Tạo mới topic. Riêng TextField **Mã topic bị disable (read-only)**.
Mã topic được lấy dữ liệu từ [TOPIC].[MaTopic] (Kiểu số).

---

### 18. Quản lý topic

| Thuộc tính | Nội dung |
|------------|----------|
| **Tên chức năng** | Quản lý topic |
| **Yêu cầu tổng quát** | Hiển thị danh sách topic |
| **Loại người dùng được sử dụng** | Admin |
| **Mô tả chức năng** | Hiển thị danh sách tất cả topic. Có bao gồm chức năng xóa topic. |
| **Điều kiện tiên quyết** | Đăng nhập thành công |
| **Cách truy cập** | Xuất phát từ menu trái, kích vào link Topic |

#### Nội dung màn hình

| Mục | Kiểu | Dữ liệu | Mô tả |
|-----|------|---------|-------|
| STT | Label | Tự động tăng theo thứ tự (bắt đầu từ 1) | |
| Tên topic | Label | [TOPIC].[TenTopic] | |

#### Hành động

| Tên hành động | Mô tả | Thành công | Thất bại |
|---------------|-------|------------|----------|
| Sửa | Mở màn hình Sửa topic | | |
| Xóa | Xóa một topic | Hiển thị popup confirm. Hiển thị "Xóa Topic thành công" | |
| Tạo mới topic | Mở màn hình Tạo mới topic | | |

---

### 19. Gán topic

| Thuộc tính | Nội dung |
|------------|----------|
| **Tên chức năng** | Gán topic |
| **Yêu cầu tổng quát** | Ghép nối 1 trainer dạy 1 hoặc nhiều topic cho 1 lớp nào đó |
| **Loại người dùng được sử dụng** | Admin |
| **Mô tả chức năng** | 1 trainer sẽ được chọn dạy 1 hoặc nhiều topic cho các học viên của 1 lớp cụ thể nào đó |
| **Điều kiện tiên quyết** | Đăng nhập thành công |
| **Cách truy cập** | Xuất phát từ màn hình Quản lý gán topic, kích chọn button Gán mới |

#### Nội dung màn hình

| Mục | Kiểu | Dữ liệu | Mô tả |
|-----|------|---------|-------|
| Lớp | Combobox | [LOP].[TenLop] | Lấy toàn bộ danh sách lớp. **Giá trị mặc định là lớp đầu tiên trong danh sách.** |
| Trainer | Combobox | [TRAINER].[TenTrainer] | Lấy toàn bộ danh sách trainer. **Giá trị mặc định là trainer đầu tiên trong danh sách.** |
| Topic | List checkbox | [TOPIC].[TenTopic] | Lấy toàn bộ danh sách topic. Mỗi dòng tương ứng với 1 topic. **Checkbox Chọn có giá trị mặc định là Unchecked.** |

#### Hành động

| Tên hành động | Mô tả | Thành công | Thất bại |
|---------------|-------|------------|----------|
| Gán | Gán topic cho trainer | Quay về màn hình Quản lý gán topic | |

---

### 20. Quản lý gán topic

| Thuộc tính | Nội dung |
|------------|----------|
| **Tên chức năng** | Quản lý gán topic |
| **Yêu cầu tổng quát** | Hiển thị danh sách topic đã được gán cho trainer |
| **Loại người dùng được sử dụng** | Admin |
| **Mô tả chức năng** | Hiển thị danh sách tất cả topic đã được gán cho trainer theo từng lớp. Có bao gồm chức năng xóa 1 lệnh gán topic cho trainer nào đó. |
| **Điều kiện tiên quyết** | Đăng nhập thành công |
| **Cách truy cập** | Xuất phát từ menu trái, kích vào link Gán topic |

#### Nội dung màn hình

| Mục | Kiểu | Dữ liệu | Mô tả |
|-----|------|---------|-------|
| STT | Label | Tự động tăng theo thứ tự | |
| Topic | Label | [TOPIC].[TenTopic] | |
| Trainer | Combobox | [TRAINER].[TenTrainer] | Bị disable. Giá trị tương ứng với trainer đang được gán topic. |
| Lớp | Combobox | [LOP].[TenLop] | **Giá trị mặc định là tên của lớp đầu tiên trong danh sách.** |

#### Hành động

| Tên hành động | Mô tả | Thành công | Thất bại |
|---------------|-------|------------|----------|
| Sửa | Dòng tương ứng sẽ được enable để người dùng sửa | | |
| Xóa | Xóa một lệnh gán topic cho trainer | Hiển thị popup confirm trước khi xóa | |
| Gán mới | Mở màn hình Gán topic | | |
| Hoàn tất | Lưu trữ các thay đổi | Vẫn ở lại màn hình này | |
| Xóa hết | Xóa tất cả các lệnh gán topic của lớp đang được chọn | Hiển thị popup "Xóa hết gán topic" trước khi xóa | |

---

### 21. Quản lý học viên chưa feedback

| Thuộc tính | Nội dung |
|------------|----------|
| **Tên chức năng** | Quản lý học viên chưa feedback |
| **Yêu cầu tổng quát** | Hiển thị danh sách các học viên chưa đánh feedback |
| **Loại người dùng được sử dụng** | Admin |
| **Mô tả chức năng** | Hiển thị danh sách tất cả các học viên chưa đánh feedback. Có thể xem theo từng lớp hoặc tất cả các lớp. |
| **Điều kiện tiên quyết** | Đăng nhập thành công |
| **Cách truy cập** | Xuất phát từ menu trái, kích vào link Học viên chưa FB |

#### Nội dung màn hình

| Mục | Kiểu | Dữ liệu | Mô tả |
|-----|------|---------|-------|
| STT | Label | Tự động tăng theo thứ tự | |
| Học viên | Label | [HOCVIEN].[TenHocVien] | |
| Topic | Label | [TOPIC].[TenTopic] | |
| Lớp | Combobox | [LOP].[TenLop] | Giá trị mặc định là "Lớp" |

---

### 22. Xóa toàn bộ

Chức năng này dùng để xóa sạch dữ liệu đang có trong hệ thống **trừ các dữ liệu sau**: 
- Danh sách template
- Danh sách topic
- Danh sách trainer

Để xóa toàn bộ dữ liệu thì admin phải nhập mật khẩu vào text field "Nhập lại mật khẩu", sau đó nhấn button Hoàn tất.

---

### 23. Đổi mật khẩu và đăng xuất

---

### 24. Xuất kết quả

| Thuộc tính | Nội dung |
|------------|----------|
| **Tên chức năng** | Xuất kết quả |
| **Yêu cầu tổng quát** | Xuất kết quả đánh feedback của học viên ra file Excel |
| **Loại người dùng được sử dụng** | Admin |
| **Mô tả chức năng** | Chọn 1 hoặc tất cả các lớp, sau đó xuất toàn bộ kết quả đánh feedback của học viên ra file Excel |
| **Điều kiện tiên quyết** | Đăng nhập thành công |
| **Cách truy cập** | Xuất phát từ menu trái, kích vào link Xuất kết quả |

#### Nội dung màn hình

| Mục | Kiểu | Dữ liệu | Mô tả |
|-----|------|---------|-------|
| Lớp | Combobox | [LOP].[TenLop] | Giá trị mặc định là "Lớp" |
| STT | Label | Số tự sinh, tự động tăng | |
| Topic | Label | [TOPIC].[TenTopic] | |
| Chọn | Checkbox | | Chọn topic nào được xuất kết quả. Giá trị mặc định là Unchecked. |

#### Hành động

| Tên hành động | Mô tả | Thành công | Thất bại |
|---------------|-------|------------|----------|
| Xuất | Xuất kết quả ra file Excel | Xuất ra file Excel | Combobox Lớp phải được chọn một giá trị cụ thể (khác giá trị "Lớp" mặc định) |

---

## IV. MÔ TẢ CHỨC NĂNG CHO LOẠI NGƯỜI DÙNG USER

### 1. Đăng nhập

| Thuộc tính | Nội dung |
|------------|----------|
| **Tên chức năng** | Đăng nhập |
| **Yêu cầu tổng quát** | Cho phép user (học viên) được quyền đăng nhập vào hệ thống |
| **Loại người dùng được sử dụng** | User (học viên) |
| **Mô tả chức năng** | Đăng nhập bằng cách nhập username và password |
| **Điều kiện tiên quyết** | Đã được tạo account học viên trong chức năng của admin |
| **Cách truy cập** | http://localhost:8080/FeedbackOnline/LoginUserServlet hoặc từ màn hình đăng nhập của admin |

#### Nội dung màn hình

| Mục | Kiểu | Dữ liệu | Mô tả |
|-----|------|---------|-------|
| Username | TextField - String(50) | [HOCVIEN].[MaHocVien] | Bắt buộc nhập. |
| Password | TextField - String(50) | [HOCVIEN].[Password] | Bắt buộc nhập. Nếu user mới đăng nhập lần đầu thì password = username. |

#### Hành động

| Tên hành động | Mô tả | Thành công | Thất bại |
|---------------|-------|------------|----------|
| Login | Đăng nhập vào hệ thống | Hiển thị trang "Chọn topic cần feedback" | Hiển thị message "Login failed. Invalid username or password" |

---

### 2. Chọn topic cần feedback

| Thuộc tính | Nội dung |
|------------|----------|
| **Tên chức năng** | Chọn topic cần feedback |
| **Yêu cầu tổng quát** | Cho phép user (học viên) chọn topic để đánh feedback |
| **Loại người dùng được sử dụng** | User (học viên) |
| **Điều kiện tiên quyết** | Đã đăng nhập |
| **Cách truy cập** | Đăng nhập vào hệ thống |

#### Nội dung màn hình

| Mục | Kiểu | Dữ liệu | Mô tả |
|-----|------|---------|-------|
| Danh sách topic | Button | | Các button. Mỗi button tương ứng với một topic cần phải đánh feedback. |

#### Hành động

| Tên hành động | Mô tả | Thành công | Thất bại |
|---------------|-------|------------|----------|
| Chọn 1 button topic | Mở ra màn hình "Đánh feedback" | | Nếu học viên chọn vào topic có ghi chú là (Đã hoàn thành) thì sẽ hiển thị thông báo |

---

### 3. Đánh feedback

| Thuộc tính | Nội dung |
|------------|----------|
| **Tên chức năng** | Đánh feedback |
| **Yêu cầu tổng quát** | Cho phép user (học viên) đánh feedback cho topic đã chọn |
| **Loại người dùng được sử dụng** | User (học viên) |
| **Điều kiện tiên quyết** | Đã đăng nhập |
| **Cách truy cập** | Xuất phát từ màn hình "Chọn topic cần feedback" |

#### Nội dung màn hình

| Mục | Kiểu | Dữ liệu | Mô tả |
|-----|------|---------|-------|
| Topic | Label | [TOPIC].[TenTopic] | Tên topic đang được chọn để học viên đánh feedback |
| Trainer | Label | [TRAINER].[TenTrainer] | Tên trainer đang được học viên đánh feedback |
| ID | Label | | Số thứ tự của câu hỏi |
| Câu hỏi | Label | [CAUHOI].[TenCauHoi] | |
| Điểm | Combobox | [CAUHOI].[DiemToiDa] | Nằm giữa điểm 1 và điểm tối đa. Lưu vào [CHITIETFEEDBACK].[Diem] |
| Nhận xét chi tiết | Text Field - String (Max) | [CHITIETFEEDBACK].[GhiChu] | |

#### Hành động

| Tên hành động | Mô tả | Thành công | Thất bại |
|---------------|-------|------------|----------|
| Submit | Gửi kết quả feedback cho hệ thống | Thông báo việc đánh feedback đã hoàn thành | Nếu user cho điểm dưới mức điểm tối thiểu mà không nhập nhận xét chi tiết thì báo lỗi |

---

### 4. Đổi mật khẩu và đăng xuất

---

## V. ĐẶC TẢ YÊU CẦU PHI CHỨC NĂNG VÀ YÊU CẦU KHÁC

### 1. Hiệu suất

| STT | Yêu cầu |
|-----|---------|
| 1. | Tối thiểu là 5 users đăng nhập vào hệ thống cùng một lúc, thời gian đăng nhập tối đa là 1s |
| 2. | Thời gian cập nhật dữ liệu tối đa là 2s |

### 2. Khả năng tăng cường

| STT | Yêu cầu |
|-----|---------|
| 1. | Khi cần có thể tăng số người đăng nhập vào hệ thống lên khoảng 7-8 người |

### 3. Bảo mật

| STT | Yêu cầu |
|-----|---------|
| 1. | Sử dụng tài khoản để đăng nhập vào hệ thống. Gồm 2 loại: Admin và user. Mỗi loại sẽ có một số quyền riêng |
| 2. | Các dữ liệu về tài khoản được lưu trong cơ sở dữ liệu và được bảo mật |

### 4. Sao lưu và phục hồi

| STT | Yêu cầu |
|-----|---------|
| 1. | Các dữ liệu được lưu trong các cơ sở dữ liệu và được sao lưu thường xuyên và được phục hồi khi cần |

### 5. Yêu cầu hệ điều hành

| STT | Yêu cầu |
|-----|---------|
| 1. | Phần mềm được thiết kế để thích ứng trên nhiều hệ điều hành như Windows XP, Windows 7, Windows 8, Windows 8.1, Windows 10, Linux |

### 6. Độ tin cậy

| STT | Yêu cầu |
|-----|---------|
| 1. | Phần mềm chạy tốt, ít lỗi |

### 7. Giao diện

| STT | Yêu cầu |
|-----|---------|
| 1. | Giao diện đẹp mắt, dễ sử dụng, thân thiện với người dùng |
| 2. | Font chữ: Times new roman |

### 8. Ngôn ngữ

| STT | Yêu cầu |
|-----|---------|
| 1. | **Chương trình chỉ sử dụng Tiếng Việt** |

---

## VI. PHỤ LỤC

- Hướng dẫn sử dụng phần mềm. Mỗi người sử dụng được cấp một tài liệu hướng dẫn sử dụng lưu dưới dạng tệp .doc.
- Lược đồ cơ sở dữ liệu quan hệ của hệ thống.

---

*HỆ THỐNG FEEDBACK ONLINE - Đặc tả yêu cầu phần mềm - Trang 25*
