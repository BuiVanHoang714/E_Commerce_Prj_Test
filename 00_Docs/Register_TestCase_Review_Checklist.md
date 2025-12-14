# Checklist review test case Register

Tài liệu này dùng để review chất lượng + độ bao phủ của bộ test case **Register** (tham chiếu từ file [01_BaseLine/BL01/E Commerce Project_Register.csv](../01_BaseLine/BL01/E%20Commerce%20Project_Register.csv)).

## 1) Coverage map (tham chiếu nhanh theo Test Case ID)

- Happy path
  - Mandatory fields: `TC_RF_001`
  - All fields: `TC_RF_003`
  - Newsletter Yes/No: `TC_RF_005`, `TC_RF_006`
- Validation / Negative
  - Submit rỗng + message mandatory: `TC_RF_004`
  - Password mismatch: `TC_RF_008`, `TC_RF_024`
  - Existing email: `TC_RF_009`
  - Invalid email formats: `TC_RF_010`
  - Invalid phone: `TC_RF_011`
  - Mandatory accepts spaces: `TC_RF_016`
  - Password complexity standard: `TC_RF_017`
  - Leading/trailing spaces trimmed: `TC_RF_019`
  - Privacy Policy unchecked default: `TC_RF_020`
  - Register without Privacy Policy: `TC_RF_021`
- UI / Navigation / Checklist
  - Ways to open Register page: `TC_RF_007`
  - Placeholders: `TC_RF_013`
  - Mandatory marks (*): `TC_RF_014`
  - Password masked: `TC_RF_022`
  - Navigate via links/options: `TC_RF_023`
  - Breadcrumb/heading/url/title: `TC_RF_025`
  - UI page: `TC_RF_026`
  - Supported environments: `TC_RF_027`
- Integrations / Persistence
  - Confirmation email: `TC_RF_002`
  - Data stored in DB: `TC_RF_015`

## 2) Checklist review (tick để pass/fail khi review)

### 2.1 Thông tin test case (format/consistency)

- [ ] `Test Case ID` đúng convention, không trùng, không thiếu
- [ ] `Test Scenario` thống nhất (TS_001 Register Functionality) và không bị sai chính tả
- [ ] `Test Case Title` mô tả đúng mục tiêu, không mơ hồ (ví dụ “Validate …” nhưng thiếu điều kiện)
- [ ] `Priority` hợp lý (P1 cho happy path/critical validations)
- [ ] Cột `Test Technique` được gán hợp lý (EP/BVE/Checklist) và thống nhất quy ước

### 2.2 Preconditions / môi trường

- [ ] Preconditions đủ để người khác chạy lại được (URL, trạng thái login/logout)
- [ ] Với case “existing email” có mô tả rõ tài khoản đã tồn tại và dữ liệu không thay đổi
- [ ] Với case cần email nhận thư, có nêu rõ mailbox/test inbox dùng để kiểm tra
- [ ] Nếu có ràng buộc browser/device, đã nêu rõ (hoặc được bao bởi `TC_RF_027`)

### 2.3 Test Steps (rõ ràng, lặp lại được)

- [ ] Steps đánh số rõ, không thiếu bước quan trọng (submit, verify màn success, verify email…)
- [ ] Không gộp nhiều hành động/expected vào 1 bước quá khó kiểm chứng
- [ ] Mỗi bước có điểm kiểm chứng rõ (Expected Result) hoặc reference ER-x hợp lý
- [ ] Có bước “cleanup”/khôi phục dữ liệu khi cần (ví dụ account đã tạo) hoặc ghi chú cách tránh làm bẩn dữ liệu

### 2.4 Test Data (đầy đủ + có thể tái sử dụng)

- [ ] Dữ liệu vào cụ thể (không chỉ “Not Applicable” nếu thật sự cần ví dụ email/phone)
- [ ] Email tạo mới đảm bảo unique (nêu cách generate: timestamp/alias…)
- [ ] Có tách rõ dữ liệu hợp lệ vs không hợp lệ
- [ ] Dữ liệu không chứa thông tin nhạy cảm thật (mật khẩu thật, email thật của cá nhân…)

### 2.5 Bao phủ validation theo field (EP/BVE)

**First Name** (range 1–32)
- [ ] Có case biên: 0 / 1 / 32 / 33 ký tự (hiện đang cover chủ yếu qua `TC_RF_004`)

**Last Name** (range 1–32)
- [ ] Có case biên: 0 / 1 / 32 / 33 ký tự (hiện đang cover chủ yếu qua `TC_RF_004`)

**Email**
- [ ] Case invalid format đủ đại diện (hiện có `TC_RF_010`)
- [ ] Case duplicate email (hiện có `TC_RF_009`)

**Telephone** (range 3–32)
- [ ] Case invalid phone (numeric/alpha) (hiện có `TC_RF_011`)
- [ ] Case biên 2 / 3 / 32 / 33 ký tự (chưa thấy case explicit)

**Password** (range 4–20 + complexity nếu áp dụng)
- [ ] Case biên 3 / 4 / 20 / 21 ký tự (hiện đang cover chủ yếu qua `TC_RF_004`)
- [ ] Case complexity (hiện có `TC_RF_017`)

**Password Confirm**
- [ ] Mismatch (hiện có `TC_RF_008`, `TC_RF_024`)

**Newsletter**
- [ ] Yes/No + verify default selection (hiện có `TC_RF_005`, `TC_RF_006`)

**Privacy Policy**
- [ ] Default unchecked (hiện có `TC_RF_020`)
- [ ] Submit without checking => warning (hiện có `TC_RF_021`)

**Spaces/Trimming**
- [ ] Mandatory chỉ spaces bị reject (hiện có `TC_RF_016`)
- [ ] Leading/trailing spaces được trim (hiện có `TC_RF_019`)

### 2.6 UI/UX checklist

- [ ] Placeholder đầy đủ & đúng (hiện có `TC_RF_013`)
- [ ] Field mandatory được đánh dấu * đúng (hiện có `TC_RF_014`)
- [ ] Password được mask khi nhập (hiện có `TC_RF_022`)
- [ ] Breadcrumb/Heading/URL/Title đúng (hiện có `TC_RF_025`)
- [ ] UI tổng thể trang register đạt checklist (hiện có `TC_RF_026`)

### 2.7 Navigation / flows

- [ ] Có đủ cách điều hướng đến trang Register (hiện có `TC_RF_007`)
- [ ] Link “Login page”, “Privacy Policy”, menu/footer/right-column hoạt động (hiện có `TC_RF_023`)
- [ ] Sau khi register thành công, flow “Continue” về Account page đúng (hiện cover trong `TC_RF_001`, `TC_RF_003`)

### 2.8 Email / notification

- [ ] Có case xác nhận email được gửi (hiện có `TC_RF_002`)
- [ ] Subject/from/body/link login được verify rõ ràng và có tiêu chí pass/fail

### 2.9 Data persistence

- [ ] Có case verify dữ liệu được lưu DB (hiện có `TC_RF_015`) và định nghĩa rõ “verify” bằng cách nào

### 2.10 Cross-environment

- [ ] Có scope rõ cho “supported environments” (browser/device) và cách chạy (hiện có `TC_RF_027`)

## 3) Gợi ý chuẩn hoá technique (để dùng thống nhất)

- `EP`: test theo phân vùng dữ liệu (valid/invalid representative)
- `BVE`: test theo giá trị biên/ngưỡng/range (min/max, N-th attempt, timeout…)
- `Checklist`: UI/Navigation/Content review theo danh sách mục

