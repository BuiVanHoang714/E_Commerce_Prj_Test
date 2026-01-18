# UI Testing Checklist

## 1. Text (Nội dung chữ hiển thị)

- [ ] Kiểm tra chính tả (spelling mistakes)
- [ ] Kiểm tra ngữ pháp (grammatical mistakes)
- [ ] Đảm bảo dễ đọc (readability: font size, màu, kiểu chữ)
- [ ] Kiểm tra căn chỉnh (alignment: trái, phải, giữa)
- [ ] Text không chồng lấn (overlapping) với phần tử khác
- [ ] Text không bị tràn ra ngoài khung hoặc trang
- [ ] Phân biệt rõ heading và nội dung (size, style khác nhau)

## 2. Text Fields (Ô nhập liệu)

- [ ] Đúng label cho mỗi text field
- [ ] Label và text field căn chỉnh đúng
- [ ] Read-only field: không cho nhập dữ liệu
- [ ] Disabled field: bị mờ, không cho nhập hoặc chỉnh sửa
- [ ] Enabled field: cho nhập dữ liệu, có cursor khi click
- [ ] Có placeholder text nếu yêu cầu
- [ ] Có thể có pre-populated values (giá trị mặc định)
- [ ] Kiểm tra kích thước (width/height) theo yêu cầu
- [ ] Kiểm tra giới hạn ký tự (min/max length)
- [ ] Kiểm tra loại dữ liệu chấp nhận (chữ, số, ký tự đặc biệt)
- [ ] Formatted fields: nhập theo định dạng (ví dụ số điện thoại, SSN)
- [ ] Browse button field: hiển thị tên file sau khi chọn
- [ ] Scroll bar xuất hiện khi nội dung vượt quá kích thước text area
- [ ] Cho phép chọn text bằng phím Shift + mũi tên
- [ ] Kiểm tra validation cho email, password, mandatory fields
- [ ] Không chấp nhận blank values hoặc chỉ có khoảng trắng
- [ ] Kiểm tra leading/trailing spaces không hợp lệ

## 3. Drop-downs

- [ ] Có mũi tên hiển thị trên drop-down
- [ ] Click mũi tên hiển thị danh sách tùy chọn
- [ ] Có default option theo yêu cầu
- [ ] Nếu là mandatory field: phải chọn giá trị
- [ ] Nhập chữ cái đầu để chọn nhanh option
- [ ] Drop-down không được rỗng
- [ ] Nếu nhiều option → có scroll bar
- [ ] Các option căn chỉnh đúng
- [ ] Có label đúng cho drop-down
- [ ] Label và drop-down căn chỉnh đúng
- [ ] Khi chọn option, drop-down được highlight
- [ ] Các option hiển thị theo thứ tự sắp xếp (alphabetical hoặc theo yêu cầu)

## 4. Buttons

- [ ] Kiểm tra enabled/disabled trạng thái
- [ ] Button clickable và hoạt động đúng
- [ ] Có thể chọn bằng Tab + Enter hoặc Space bar
- [ ] Button căn chỉnh đúng với các phần tử khác
- [ ] Label text trên button đúng (ví dụ: "Login" thay vì "Logout")
- [ ] Kiểm tra với single click / double click nếu yêu cầu
- [ ] Khi hover chuột, button được highlight
- [ ] Các button trên toàn site có style, font, màu sắc đồng nhất
- [ ] Trong alert box: Enter chọn OK, Escape chọn Cancel

## 5. Checkbox

- [ ] Kiểm tra trạng thái Enabled/Disabled đúng theo yêu cầu
- [ ] Xác minh trạng thái mặc định: Checked/Unchecked
- [ ] Nhãn (Label) của checkbox phải chính xác, rõ ràng
- [ ] Có thể chọn/bỏ chọn bằng chuột
- [ ] Có thể chọn/bỏ chọn bằng Tab + Spacebar trên bàn phím
- [ ] Checkbox bị Disabled thì không được chỉnh sửa
- [ ] Checkbox phải căn chỉnh đúng với label và các thành phần khác trên trang

## 6. Radio Button

- [ ] Kiểm tra radio button mặc định có được chọn đúng theo yêu cầu
- [ ] Trong một nhóm, chỉ một lựa chọn được chọn tại một thời điểm
- [ ] Nhãn (Label) phải rõ ràng, đúng nội dung
- [ ] Có thể chọn bằng chuột
- [ ] Có thể chọn bằng Tab + phím mũi tên trên bàn phím
- [ ] Radio button bị Disabled thì không được chỉnh sửa
- [ ] Radio button phải căn chỉnh đúng với label, nhóm và bố cục trang

## 7. Hyperlink

- [ ] Hyperlink phải có màu chuẩn (ví dụ: xanh dương) và đồng nhất trên toàn site
- [ ] Khi hover chuột, màu phải thay đổi đúng thiết kế
- [ ] Click bằng chuột phải dẫn đến đúng trang
- [ ] Click bằng Tab + Enter phải hoạt động chính xác
- [ ] Ctrl + Click phải mở link trong tab mới
- [ ] Không có hyperlink bị gãy/broken
- [ ] Hyperlink phải căn chỉnh đúng với nội dung xung quanh
- [ ] Văn bản hyperlink phải đúng chính tả, không lỗi chữ

## 8. Image

- [ ] Hình ảnh phải hiển thị đầy đủ, không bị mất
- [ ] Hình ảnh phải có độ phân giải tốt, không mờ, không vỡ pixel
- [ ] Hình ảnh phải căn chỉnh đúng với bố cục, không chồng chéo
- [ ] Kích thước (height/width) phải đúng yêu cầu thiết kế
- [ ] Hình ảnh phải hiển thị đúng trong khung chứa và không bị lệch
- [ ] Đảm bảo hình ảnh responsive trên nhiều màn hình

## 9. Date/Time Pickers (Bộ chọn ngày/giờ)

- [ ] Định dạng ngày tháng hiển thị đúng (dd/mm/yyyy hoặc mm/dd/yyyy)
- [ ] Chọn ngày từ lịch cập nhật vào field chính xác
- [ ] Kiểm tra năm nhuận (29/02)
- [ ] Kiểm tra nhập ngày không hợp lệ (ví dụ: 30/02, 31/04)
- [ ] Kiểm tra vô hiệu hóa ngày trong quá khứ hoặc tương lai nếu yêu cầu
- [ ] Kiểm tra chọn khoảng thời gian (Start Date <= End Date)
- [ ] Reset bộ chọn về ngày hiện tại khi cần thiết
- [ ] Cho phép nhập tay (manual input) song song với chọn lịch

## 10. File Upload (Tải lên tệp)

- [ ] Chỉ cho phép các định dạng file quy định (extensions filter: .jpg, .pdf, .docx...)
- [ ] Kiểm tra giới hạn dung lượng file tối đa/tối thiểu
- [ ] Kiểm tra upload file rỗng (0KB)
- [ ] Kiểm tra upload file có tên chứa ký tự đặc biệt hoặc quá dài
- [ ] Kiểm tra chức năng Drag & Drop (Kéo thả)
- [ ] Hiển thị thanh tiến trình (progress bar) khi upload file lớn hoặc mạng chậm
- [ ] Có nút xóa/hủy file đã chọn trước khi submit
- [ ] Kiểm tra upload nhiều file cùng lúc (nếu hỗ trợ)

## 11. Tables & Grids (Bảng dữ liệu)

- [ ] Tiêu đề cột (Header) có hỗ trợ sort (sắp xếp) tăng/giảm dần
- [ ] Phân trang (Pagination) hoạt động đúng (Next, Previous, First, Last, Jump to page)
- [ ] Kiểm tra thay đổi số lượng bản ghi hiển thị trên mỗi trang (Items per page)
- [ ] Kiểm tra tính năng lọc (Filter) trả về dữ liệu đúng
- [ ] Cột cố định (Sticky headers/columns) khi scroll bảng lớn
- [ ] Dữ liệu dài trong ô được xử lý đúng (truncate, wrap text, tooltip)
- [ ] Kiểm tra chức năng "Select All" nếu có checkbox trong bảng
- [ ] Hiển thị thông báo khi không có dữ liệu (Empty state / No data found)

## 12. Modals & Popups (Cửa sổ bật lên)

- [ ] Modal xuất hiện ở giữa màn hình hoặc vị trí quy định
- [ ] Background phía sau bị làm mờ (overlay dimmed) để tập trung sự chú ý
- [ ] Không thể tương tác với màn hình chính khi Modal đang mở (trừ phi thiết kế khác)
- [ ] Đóng Modal bằng nút "X", nút "Cancel" hoặc click ra vùng overlay (nếu cho phép)
- [ ] Phím ESC có đóng được Modal không
- [ ] Focus con trỏ chuột luân chuyển trong Modal (Focus trapping - Accessibility)

## 13. Responsive & Cross-Browser (Thích ứng & Đa trình duyệt)

- [ ] Giao diện không vỡ (layout broken) khi thay đổi kích thước cửa sổ trình duyệt
- [ ] Các phần tử tự động sắp xếp lại (stacking) trên mobile/tablet
- [ ] Font size và button touch target đủ lớn trên thiết bị cảm ứng
- [ ] Hamburger menu (menu 3 gạch) hoạt động đúng trên mobile
- [ ] Hiển thị và hoạt động nhất quán trên Chrome, Firefox, Edge, Safari
- [ ] Kiểm tra xoay màn hình (Landscape/Portrait) trên thiết bị di động
- [ ] Kiểm tra chế độ Zoom in/Zoom out (đến 200%) mà không vỡ layout

## 14. Error Handling & Toasts (Thông báo & Xử lý lỗi)

- [ ] Thông báo lỗi (Error message) nội dung rõ ràng, hướng dẫn cách khắc phục
- [ ] Thông báo thành công (Success toast) tự động biến mất sau vài giây (timeout)
- [ ] Thông báo lỗi biến mất khi người dùng sửa đúng dữ liệu (real-time validation)
- [ ] Vị trí thông báo không che khuất các nút thao tác quan trọng
- [ ] Màu sắc thông báo chuẩn (Đỏ: Lỗi, Xanh: Thành công, Vàng: Cảnh báo, Xanh dương: Info)
- [ ] Kiểm tra trang 404/500 được custom đẹp, có nút quay về trang chủ

## 15. Security (Kiểm tra bảo mật trên UI)

- [ ] Password field hiển thị dạng masked (dấu chấm/sao)
- [ ] Có nút "Show/Hide password" hoạt động đúng
- [ ] Không cho phép copy nội dung từ password field
- [ ] Tự động đăng xuất hoặc khóa màn hình sau thời gian chờ (Session timeout)
- [ ] Không hiển thị thông tin nhạy cảm (ID, Token) rõ ràng trên URL
- [ ] Kiểm tra input field chống XSS cơ bản: nhập `<script>` không bị thực thi
