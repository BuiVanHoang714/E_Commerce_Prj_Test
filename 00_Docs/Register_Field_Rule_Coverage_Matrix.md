# Register coverage matrix (Field × Rule × Test Case ID)

Mục tiêu: nhìn nhanh **mỗi field đang được cover rule nào** và **test case nào cover**.


## Quy ước

- **EP**: Equivalence Partitioning
- **BVE**: Boundary Value Equivalence
- **Checklist**: UI/Navigation/Content checklist

## Matrix (bảng tổng hợp)

| Field | Rule / What to verify | Test Case ID(s) |
|---|---|---|
| Register (end-to-end) | Register success với mandatory fields | TC_RF_001 |
| Register (end-to-end) | Register success với all fields | TC_RF_003 |
| Register (end-to-end) | All supported environments | TC_RF_027 |
| First Name | Mandatory empty ⇒ warning | TC_RF_004 |
| First Name | Length boundaries (1–32) – cần bổ sung case explicit (0/1/32/33) | Covered gián tiếp: TC_RF_004 |
| Last Name | Mandatory empty ⇒ warning | TC_RF_004 |
| Last Name | Length boundaries (1–32) – cần bổ sung case explicit (0/1/32/33) | Covered gián tiếp: TC_RF_004 |
| E-Mail | Invalid format(s) | TC_RF_010 |
| E-Mail | Duplicate/existing email | TC_RF_009 |
| E-Mail | Mandatory empty ⇒ warning | TC_RF_004 |
| Telephone | Invalid phone (alpha/too short examples) | TC_RF_011 |
| Telephone | Mandatory empty ⇒ warning | TC_RF_004 |
| Telephone | Only spaces accepted? (should reject) | TC_RF_016 (ghi nhận issue: phone chấp nhận spaces) |
| Telephone | Length boundaries (3–32) – cần bổ sung case explicit (2/3/32/33) | Covered gián tiếp: TC_RF_004 |
| Password | Mandatory empty ⇒ warning | TC_RF_004 |
| Password | Length boundaries (4–20) – cần bổ sung case explicit (3/4/20/21) | Covered gián tiếp: TC_RF_004 |
| Password | Complexity standard (nếu yêu cầu) | TC_RF_017 |
| Password | Masked input / hidden characters | TC_RF_022 |
| Password Confirm | Mismatch password vs confirm | TC_RF_008, TC_RF_024 |
| Newsletter | Subscribe = Yes flow + verify selection | TC_RF_005 |
| Newsletter | Subscribe = No flow + verify selection | TC_RF_006 |
| Privacy Policy | Checkbox default not selected | TC_RF_020 |
| Privacy Policy | Submit without checking ⇒ warning | TC_RF_021 |
| Whitespace / trimming | Leading/trailing spaces should be trimmed | TC_RF_019 |
| Whitespace / trimming | Mandatory fields accept only spaces? should reject | TC_RF_016 |
| Navigation | Different ways to open Register page | TC_RF_007 |
| Navigation | Links/options on Register page navigate correctly | TC_RF_023 |
| UI | Placeholders present and correct | TC_RF_013 |
| UI | Mandatory * marker shown | TC_RF_014 |
| UI | Breadcrumb / heading / URL / title | TC_RF_025 |
| UI | Overall Register page UI | TC_RF_026 |
| Email | Confirmation email sent + verify subject/body/from + login link | TC_RF_002 |
| Data persistence | Data stored in DB | TC_RF_015 |

## Gaps (điểm thiếu để review nhanh)

- Boundary tests explicit chưa có (đang “cover gián tiếp”):
  - First Name: 0/1/32/33
  - Last Name: 0/1/32/33
  - Telephone: 2/3/32/33
  - Password: 3/4/20/21
- Một số case đang là “UI/Checklist” nhưng có thể tách rule rõ hơn nếu muốn trace (ví dụ: từng link nào, từng khu vực UI nào).


