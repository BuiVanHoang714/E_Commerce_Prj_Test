# BÀI TẬP SQL – DATABASE QUẢN LÝ WEBSITE BÁN HÀNG ONLINE

## Lược đồ cơ sở dữ liệu

| Bảng | Các cột |
|---|---|
| **KHACHHANG** | MaKH (PK), HoTenKH, DiaChi, SoDienThoai |
| **NHANVIEN** | MaNV (PK), HoTenNV |
| **DONHANG** | MaDonHang (PK), MaKH (FK), MaNVPhuTrach (FK→NV), MaNVGiaoHang (FK→NV), TrangThaiDH, NgayGioLapDonHang, NgayGioGiaoHang |
| **CHITIETDONHANG** | MaDonHang (PK, FK→DH), MaHangHoa (PK, FK→HH), SoLuong, DonGiaBan |
| **HANGHOA** | MaHangHoa (PK), TenHangHoa, DonViTinh, DonGiaHienTai, MaLoaiHH (FK) |
| **LOAIHANGHOA** | MaLoaiHH (PK), TenLoaiHH |

---

## Câu 1 – LIKE và %

**Câu hỏi:** Hãy liệt kê họ tên và số điện thoại của những khách hàng có địa chỉ bắt đầu bằng "Hà Nội".

```sql
SELECT HoTenKH, SoDienThoai
FROM KHACHHANG
WHERE DiaChi LIKE N'Hà Nội%';
```

---

## Câu 2 – LIKE, % và _

**Câu hỏi:** Tìm các khách hàng có số điện thoại bắt đầu bằng "09", ký tự thứ 3 là bất kỳ, ký tự thứ 4 là "8", và phần còn lại không giới hạn.  
*(Dùng `_` để đại diện đúng 1 ký tự bất kỳ)*

```sql
SELECT MaKH, HoTenKH, SoDienThoai
FROM KHACHHANG
WHERE SoDienThoai LIKE '09_8%';
```

---

## Câu 3 – LIKE, % và []

**Câu hỏi:** Tìm các hàng hóa có tên bắt đầu bằng một trong các chữ cái từ A đến M (không phân biệt hoa/thường), phần tên còn lại không giới hạn.

```sql
SELECT MaHangHoa, TenHangHoa, DonGiaHienTai
FROM HANGHOA
WHERE TenHangHoa LIKE '[A-Ma-m]%';
```

---

## Câu 4 – LIKE, [] và [^]

**Câu hỏi:** Tìm các nhân viên có họ tên mà ký tự đầu tiên nằm trong khoảng N–Z, nhưng ký tự thứ hai **không phải** là một trong các nguyên âm a, e, i, o, u.

```sql
SELECT MaNV, HoTenNV
FROM NHANVIEN
WHERE HoTenNV LIKE '[N-Zn-z][^aeiouAEIOU]%';
```

---

## Câu 5 – INNER JOIN 2 bảng

**Câu hỏi:** Liệt kê danh sách đơn hàng cùng với họ tên và số điện thoại của khách hàng đặt hàng.

```sql
SELECT DH.MaDonHang,
       KH.HoTenKH,
       KH.SoDienThoai,
       DH.TrangThaiDH,
       DH.NgayGioLapDonHang
FROM DONHANG DH
INNER JOIN KHACHHANG KH ON DH.MaKH = KH.MaKH;
```

---

## Câu 6 – INNER JOIN 3 bảng

**Câu hỏi:** Hiển thị thông tin đơn hàng gồm: tên khách hàng, mã đơn hàng, tên nhân viên phụ trách và trạng thái đơn hàng.

```sql
SELECT KH.HoTenKH,
       DH.MaDonHang,
       NV.HoTenNV     AS NhanVienPhuTrach,
       DH.TrangThaiDH,
       DH.NgayGioLapDonHang
FROM DONHANG DH
INNER JOIN KHACHHANG KH  ON DH.MaKH          = KH.MaKH
INNER JOIN NHANVIEN  NV  ON DH.MaNVPhuTrach   = NV.MaNV;
```

---

## Câu 7 – INNER JOIN 4 bảng

**Câu hỏi:** Liệt kê chi tiết từng đơn hàng gồm: tên khách hàng, mã đơn hàng, tên hàng hóa, số lượng mua và đơn giá bán thực tế.

```sql
SELECT KH.HoTenKH,
       DH.MaDonHang,
       HH.TenHangHoa,
       CTDH.SoLuong,
       CTDH.DonGiaBan,
       (CTDH.SoLuong * CTDH.DonGiaBan) AS ThanhTien
FROM DONHANG DH
INNER JOIN KHACHHANG       KH   ON DH.MaKH        = KH.MaKH
INNER JOIN CHITIETDONHANG  CTDH ON DH.MaDonHang   = CTDH.MaDonHang
INNER JOIN HANGHOA         HH   ON CTDH.MaHangHoa = HH.MaHangHoa;
```

---

## Câu 8 – LEFT JOIN 2 bảng

**Câu hỏi:** Liệt kê **tất cả** khách hàng và đơn hàng của họ. Những khách hàng chưa có đơn hàng nào vẫn phải xuất hiện trong kết quả (hiển thị NULL ở cột đơn hàng).

```sql
SELECT KH.MaKH,
       KH.HoTenKH,
       KH.SoDienThoai,
       DH.MaDonHang,
       DH.TrangThaiDH
FROM KHACHHANG KH
LEFT JOIN DONHANG DH ON KH.MaKH = DH.MaKH;
```

---

## Câu 9 – LEFT JOIN 3 bảng

**Câu hỏi:** Liệt kê **tất cả** loại hàng hóa, các hàng hóa thuộc từng loại và thông tin chi tiết đặt hàng (nếu có). Những loại hàng hoặc hàng hóa chưa có đơn đặt hàng vẫn hiển thị.

```sql
SELECT LHH.MaLoaiHH,
       LHH.TenLoaiHH,
       HH.MaHangHoa,
       HH.TenHangHoa,
       CTDH.MaDonHang,
       CTDH.SoLuong
FROM LOAIHANGHOA LHH
LEFT JOIN HANGHOA          HH   ON LHH.MaLoaiHH   = HH.MaLoaiHH
LEFT JOIN CHITIETDONHANG   CTDH ON HH.MaHangHoa   = CTDH.MaHangHoa;
```

---

## Câu 10 – JOIN tất cả 6 bảng trong lược đồ

**Câu hỏi:** Hiển thị toàn bộ thông tin liên quan đến từng dòng chi tiết đơn hàng: tên khách hàng, mã đơn hàng, tên nhân viên phụ trách, tên nhân viên giao hàng (nếu có), tên hàng hóa, tên loại hàng, số lượng và đơn giá bán.  
*(Bảng NHANVIEN được JOIN 2 lần với alias khác nhau)*

```sql
SELECT KH.HoTenKH                    AS KhachHang,
       DH.MaDonHang,
       DH.TrangThaiDH,
       NV1.HoTenNV                   AS NVPhuTrach,
       NV2.HoTenNV                   AS NVGiaoHang,
       HH.TenHangHoa,
       LHH.TenLoaiHH,
       CTDH.SoLuong,
       CTDH.DonGiaBan,
       (CTDH.SoLuong * CTDH.DonGiaBan) AS ThanhTien
FROM DONHANG DH
INNER JOIN KHACHHANG      KH   ON DH.MaKH          = KH.MaKH
INNER JOIN NHANVIEN       NV1  ON DH.MaNVPhuTrach   = NV1.MaNV
LEFT  JOIN NHANVIEN       NV2  ON DH.MaNVGiaoHang   = NV2.MaNV
INNER JOIN CHITIETDONHANG CTDH ON DH.MaDonHang      = CTDH.MaDonHang
INNER JOIN HANGHOA        HH   ON CTDH.MaHangHoa    = HH.MaHangHoa
INNER JOIN LOAIHANGHOA    LHH  ON HH.MaLoaiHH       = LHH.MaLoaiHH;
```

> **Ghi chú:** `NV2` dùng `LEFT JOIN` vì nhân viên giao hàng có thể chưa được phân công (NULL), trong khi `NV1` luôn tồn tại.

---

## Câu 11 – GROUP BY và ORDER BY

**Câu hỏi:** Thống kê số lượng đơn hàng của mỗi khách hàng và sắp xếp theo số đơn hàng từ nhiều đến ít.

```sql
SELECT MaKH,
       COUNT(MaDonHang) AS SoDonHang
FROM DONHANG
GROUP BY MaKH
ORDER BY SoDonHang DESC;
```

---

## Câu 12 – GROUP BY, HAVING và hàm gộp

**Câu hỏi:** Tìm những mã hàng hóa có tổng số lượng bán ra (trên tất cả đơn hàng) lớn hơn 50 đơn vị.

```sql
SELECT MaHangHoa,
       SUM(SoLuong)  AS TongSoLuongBan,
       AVG(DonGiaBan) AS GiaBanTrungBinh
FROM CHITIETDONHANG
GROUP BY MaHangHoa
HAVING SUM(SoLuong) > 50;
```

---

## Câu 13 – INNER JOIN, GROUP BY, HAVING và hàm gộp

**Câu hỏi:** Tìm danh sách tên hàng hóa có tổng số lượng bán ra lớn hơn 50 đơn vị, kèm theo tổng doanh thu của từng mặt hàng đó.

```sql
SELECT HH.MaHangHoa,
       HH.TenHangHoa,
       SUM(CTDH.SoLuong)                        AS TongSoLuongBan,
       SUM(CTDH.SoLuong * CTDH.DonGiaBan)       AS TongDoanhThu
FROM HANGHOA HH
INNER JOIN CHITIETDONHANG CTDH ON HH.MaHangHoa = CTDH.MaHangHoa
GROUP BY HH.MaHangHoa, HH.TenHangHoa
HAVING SUM(CTDH.SoLuong) > 50;
```

---

## Câu 14 – INNER JOIN, GROUP BY, HAVING, hàm gộp và ORDER BY

**Câu hỏi:** Liệt kê tên khách hàng và tổng giá trị mua hàng của họ. Chỉ lấy những khách hàng có tổng chi tiêu trên 5.000.000 đồng và sắp xếp giảm dần theo tổng chi tiêu.

```sql
SELECT KH.MaKH,
       KH.HoTenKH,
       COUNT(DISTINCT DH.MaDonHang)              AS SoDonHang,
       SUM(CTDH.SoLuong * CTDH.DonGiaBan)       AS TongChiTieu
FROM KHACHHANG KH
INNER JOIN DONHANG        DH   ON KH.MaKH        = DH.MaKH
INNER JOIN CHITIETDONHANG CTDH ON DH.MaDonHang   = CTDH.MaDonHang
GROUP BY KH.MaKH, KH.HoTenKH
HAVING SUM(CTDH.SoLuong * CTDH.DonGiaBan) > 5000000
ORDER BY TongChiTieu DESC;
```

---

## Câu 15 – UNION và DISTINCT

**Câu hỏi:** Lấy danh sách tất cả người trong hệ thống (khách hàng và nhân viên) không trùng lặp, gồm mã, họ tên và loại người dùng.

```sql
SELECT DISTINCT MaKH  AS MaNguoiDung,
                HoTenKH AS HoTen,
                N'Khách hàng' AS LoaiNguoiDung
FROM KHACHHANG

UNION

SELECT DISTINCT MaNV,
                HoTenNV,
                N'Nhân viên'
FROM NHANVIEN;
```

---

## Câu 16 – UNION và GROUP BY

**Câu hỏi:** Thống kê số lần mỗi nhân viên tham gia vào đơn hàng, phân theo vai trò: "Phụ trách" và "Giao hàng". Kết hợp kết quả hai vai trò bằng UNION.

```sql
SELECT MaNVPhuTrach  AS MaNV,
       N'Phụ trách'  AS VaiTro,
       COUNT(*)       AS SoDonHangThamGia
FROM DONHANG
GROUP BY MaNVPhuTrach

UNION

SELECT MaNVGiaoHang,
       N'Giao hàng',
       COUNT(*)
FROM DONHANG
WHERE MaNVGiaoHang IS NOT NULL
GROUP BY MaNVGiaoHang;
```

---

## Câu 17 – UNION và INTERSECT

**Câu hỏi:** Tìm tất cả mã nhân viên có tham gia đơn hàng (dù là phụ trách hay giao hàng) bằng UNION; đồng thời xác định những mã nhân viên **vừa** phụ trách **vừa** giao hàng bằng INTERSECT.

```sql
-- Tất cả mã NV tham gia đơn hàng (phụ trách HOẶC giao hàng)
SELECT MaNVPhuTrach AS MaNV FROM DONHANG
UNION
SELECT MaNVGiaoHang        FROM DONHANG WHERE MaNVGiaoHang IS NOT NULL;

-- Mã NV vừa phụ trách vừa giao hàng
SELECT MaNVPhuTrach AS MaNV FROM DONHANG
INTERSECT
SELECT MaNVGiaoHang        FROM DONHANG WHERE MaNVGiaoHang IS NOT NULL;
```

---

## Câu 18 – UNION và EXCEPT

**Câu hỏi:** Từ danh sách tất cả nhân viên tham gia đơn hàng (kết hợp bằng UNION), loại bỏ những nhân viên đã từng giao hàng (dùng EXCEPT) để tìm ra những nhân viên **chỉ** phụ trách đơn hàng, chưa từng giao hàng.

```sql
-- Tất cả NV tham gia (phụ trách HOẶC giao hàng)
SELECT MaNVPhuTrach AS MaNV FROM DONHANG
UNION
SELECT MaNVGiaoHang        FROM DONHANG WHERE MaNVGiaoHang IS NOT NULL

EXCEPT

-- Loại bỏ những NV đã giao hàng
SELECT MaNVGiaoHang FROM DONHANG WHERE MaNVGiaoHang IS NOT NULL;
```

---

## Câu 19 – INTERSECT và NOT IN

**Câu hỏi:** Tìm những hàng hóa vừa tồn tại trong bảng HANGHOA vừa đã được đặt mua (dùng INTERSECT). Song song đó, liệt kê những hàng hóa **chưa từng** được đặt mua bằng NOT IN.

```sql
-- Hàng hóa đã được đặt mua (tồn tại ở cả 2 bảng)
SELECT MaHangHoa FROM HANGHOA
INTERSECT
SELECT MaHangHoa FROM CHITIETDONHANG;

-- Hàng hóa chưa từng xuất hiện trong bất kỳ đơn hàng nào
SELECT MaHangHoa, TenHangHoa, DonGiaHienTai
FROM HANGHOA
WHERE MaHangHoa NOT IN (
    SELECT MaHangHoa FROM CHITIETDONHANG
);
```

---

## Câu 20 – INNER JOIN + UNION + NOT IN + GROUP BY + HAVING + hàm gộp + DISTINCT + ORDER BY

**Câu hỏi:** Tạo báo cáo "Những người đóng góp nổi bật" gồm hai nhóm:  
- **Khách hàng VIP**: tổng chi tiêu > 10.000.000 đồng và không có đơn hàng nào bị hủy.  
- **Nhân viên xuất sắc**: phụ trách từ 5 đơn hàng trở lên và không có đơn hàng nào bị hủy.  
Kết quả không trùng lặp, sắp xếp theo giá trị/số đơn giảm dần.

```sql
SELECT DISTINCT KH.MaKH                               AS MaDoiTuong,
                KH.HoTenKH                            AS HoTen,
                N'Khách hàng VIP'                     AS PhanLoai,
                SUM(CTDH.SoLuong * CTDH.DonGiaBan)   AS GiaTri
FROM KHACHHANG KH
INNER JOIN DONHANG        DH   ON KH.MaKH        = DH.MaKH
INNER JOIN CHITIETDONHANG CTDH ON DH.MaDonHang   = CTDH.MaDonHang
WHERE KH.MaKH NOT IN (
    SELECT MaKH FROM DONHANG WHERE TrangThaiDH = N'Đã hủy'
)
GROUP BY KH.MaKH, KH.HoTenKH
HAVING SUM(CTDH.SoLuong * CTDH.DonGiaBan) > 10000000

UNION

SELECT DISTINCT NV.MaNV,
                NV.HoTenNV,
                N'Nhân viên xuất sắc',
                COUNT(DH.MaDonHang)
FROM NHANVIEN NV
INNER JOIN DONHANG DH ON NV.MaNV = DH.MaNVPhuTrach
WHERE NV.MaNV NOT IN (
    SELECT MaNVPhuTrach FROM DONHANG WHERE TrangThaiDH = N'Đã hủy'
)
GROUP BY NV.MaNV, NV.HoTenNV
HAVING COUNT(DH.MaDonHang) >= 5

ORDER BY GiaTri DESC;
```

---

## Câu 21 – SELECT TOP

**Câu hỏi:** Lấy **Top 5** khách hàng có tổng giá trị mua hàng cao nhất, kèm số đơn hàng và tổng chi tiêu.

```sql
SELECT TOP 5
       KH.MaKH,
       KH.HoTenKH,
       COUNT(DISTINCT DH.MaDonHang)            AS SoDonHang,
       SUM(CTDH.SoLuong * CTDH.DonGiaBan)     AS TongChiTieu
FROM KHACHHANG KH
INNER JOIN DONHANG        DH   ON KH.MaKH        = DH.MaKH
INNER JOIN CHITIETDONHANG CTDH ON DH.MaDonHang   = CTDH.MaDonHang
GROUP BY KH.MaKH, KH.HoTenKH
ORDER BY TongChiTieu DESC;
```

> **Biến thể – TOP WITH TIES** (lấy thêm những khách hàng có cùng giá trị với vị trí thứ 5):
> ```sql
> SELECT TOP 5 WITH TIES
>        KH.MaKH,
>        KH.HoTenKH,
>        SUM(CTDH.SoLuong * CTDH.DonGiaBan) AS TongChiTieu
> FROM KHACHHANG KH
> INNER JOIN DONHANG        DH   ON KH.MaKH        = DH.MaKH
> INNER JOIN CHITIETDONHANG CTDH ON DH.MaDonHang   = CTDH.MaDonHang
> GROUP BY KH.MaKH, KH.HoTenKH
> ORDER BY TongChiTieu DESC;
> ```

---

## Tổng kết từ khóa đã sử dụng

| Câu | Từ khóa / Kỹ thuật chính |
|-----|--------------------------|
| 1 | `LIKE`, `%` |
| 2 | `LIKE`, `%`, `_` |
| 3 | `LIKE`, `%`, `[]` |
| 4 | `LIKE`, `[]`, `[^]` |
| 5 | `INNER JOIN` 2 bảng |
| 6 | `INNER JOIN` 3 bảng |
| 7 | `INNER JOIN` 4 bảng |
| 8 | `LEFT JOIN` 2 bảng |
| 9 | `LEFT JOIN` 3 bảng |
| 10 | `INNER JOIN` + `LEFT JOIN` tất cả 6 bảng |
| 11 | `GROUP BY`, `ORDER BY` |
| 12 | `GROUP BY`, `HAVING`, hàm gộp (`SUM`, `AVG`) |
| 13 | `INNER JOIN`, `GROUP BY`, `HAVING`, hàm gộp |
| 14 | `INNER JOIN`, `GROUP BY`, `HAVING`, hàm gộp, `ORDER BY` |
| 15 | `UNION`, `DISTINCT` |
| 16 | `UNION`, `GROUP BY` |
| 17 | `UNION`, `INTERSECT` |
| 18 | `UNION`, `EXCEPT` |
| 19 | `INTERSECT`, `NOT IN` |
| 20 | `INNER JOIN`, `UNION`, `NOT IN`, `GROUP BY`, `HAVING`, hàm gộp, `DISTINCT`, `ORDER BY` |
| 21 | `SELECT TOP`, `SELECT TOP WITH TIES` |
