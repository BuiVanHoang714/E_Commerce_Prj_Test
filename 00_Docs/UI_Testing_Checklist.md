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
