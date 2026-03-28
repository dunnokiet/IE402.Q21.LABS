# Lab 1 – Bản Đồ Hành Chính Nam Bộ
 
Bài tập nhóm môn **IE402 – GIS** (ĐH Công nghệ Thông tin, ĐHQG TP.HCM).
 
## Mô tả
 
Ứng dụng web GIS hiển thị bản đồ khu vực **Nam Bộ** sử dụng **ArcGIS JavaScript API 5.0**, bao gồm:
 
- **Ranh giới hành chính** 8 tỉnh/TP (đơn vị sau sáp nhập)
- **Tuyến đường** cao tốc và quốc lộ
- **Điểm đại học** khu vực Nam Bộ (picture marker)
 
## Cấu trúc thư mục
 
```
lab1/
├── assets/               # Logo các trường đại học (PNG)
│   ├── agu.png           # ĐH An Giang
│   ├── bvu.png           # ĐH Bà Rịa - Vũng Tàu
│   ├── ctu.png           # ĐH Cần Thơ
│   ├── ctump.png         # ĐH Y Dược Cần Thơ
│   ├── dnu.png           # ĐH Đồng Nai
│   ├── dthu.png          # ĐH Đồng Tháp
│   ├── hcmue.png         # ĐH Sư phạm TP.HCM
│   ├── hcmut.png         # ĐH Bách Khoa TP.HCM
│   ├── kgu.png           # ĐH Kiên Giang
│   ├── pnt.png           # ĐH Phan Thiết
│   ├── tdmu.png          # ĐH Thủ Dầu Một
│   ├── tgu.png           # ĐH Tiền Giang
│   ├── ttu.png           # ĐH Trà Vinh
│   ├── tvu.png           # ĐH Tân Tạo
│   ├── uit.png           # ĐH Công nghệ Thông tin
│   ├── ump.png           # ĐH Y Dược TP.HCM
│   ├── vlute.png         # ĐH Sư phạm Kỹ thuật Vĩnh Long
│   └── vttu.png          # ĐH Võ Trường Toàn (Hậu Giang)
├── data/
│   ├── nambo/            # Dữ liệu GeoJSON ranh giới từng tỉnh
│   │   ├── angiang.js    # An Giang
│   │   ├── camau.js      # Cà Mau
│   │   ├── cantho.js     # TP. Cần Thơ
│   │   ├── dongnai.js    # Đồng Nai
│   │   ├── dongthap.js   # Đồng Tháp
│   │   ├── hochiminh.js  # TP. Hồ Chí Minh
│   │   ├── tayninh.js    # Tây Ninh
│   │   └── vinhlong.js   # Vĩnh Long
│   ├── daihoc.js         # Dữ liệu các trường đại học (tọa độ, thông tin)
│   └── duong.js          # Dữ liệu cao tốc và quốc lộ
└── index.html            # File chính của ứng dụng
```
 
## Cách chạy
 
Mở `index.html` trực tiếp trong trình duyệt (hoặc qua Live Server trong VS Code).
 
> **Lưu ý về ảnh logo**: Thay vì dùng đường dẫn tới file `assets/*.png`, mỗi trường trong `data/daihoc.js` lưu logo dưới dạng **chuỗi Base64** (`data:image/png;base64,...`) gắn thẳng vào trường `symbol_url`. Cách này giúp ứng dụng chạy được mà **không cần server** và không bị lỗi CORS khi mở file local, đồng thời các file trong thư mục `assets/` vẫn được giữ lại làm tài liệu gốc. 
## Công nghệ sử dụng
 
| Công nghệ | Phiên bản | Mục đích |
|---|---|---|
| [ArcGIS JS API](https://developers.arcgis.com/javascript/latest/) | 5.0 | Nền bản đồ, hiển thị layer |
| HTML / CSS / JS | - | Giao diện và logic |
 
## Các lớp dữ liệu (Layers)
 
### 1. Ranh giới tỉnh/TP (`provinceLayer`)
- **Loại geometry**: Polygon
- **Nguồn dữ liệu**: `data/nambo/*.js`
- **Thuộc tính popup**:
  - Tên tỉnh/TP
  - Dân số (người)
  - Diện tích (km²)
 
### 2. Đường cao tốc / Quốc lộ (`roadLayer`)
- **Loại geometry**: Polyline
- **Nguồn dữ liệu**: `data/duong.js`
- **Phân loại**:
  - Đỏ đậm – Cao tốc (`type: "highway"`)
  - Cam – Quốc lộ (`type: "national_road"`)
- **Thuộc tính popup**:
  - Tên đường
  - Chiều dài (km)
  - Lộ giới (m)
  - Các tỉnh đi qua
 
### 3. Trường đại học (`universityLayer`)
- **Loại geometry**: Point
- **Nguồn dữ liệu**: `data/daihoc.js`
- **Ký hiệu**: Picture marker (logo trường, 28×28px)
- **Thuộc tính popup**:
  - Tên trường
  - Năm thành lập
  - Ngành đào tạo
  - Số sinh viên (tương đối)
 
## Phân công nhóm
 
| Tỉnh/TP | Người phụ trách | MSSV |
|---|---|---|
| Đồng Nai |  Dương Nguyễn Nhật Quang | 23521278 |
| Tây Ninh | Ngô Tuấn Kiệt | 22520719 | 
| TP. HCM | Trịnh Thanh Tâm | 23521395 |
| Đồng Tháp | Nguyễn Trần Bảo Anh | 22520066 |
| An Giang | Trần Nguyễn Ngọc Hùng | 23520578 |
| Vĩnh Long | Lê Thị Thùy Trang | 23521627 |
| TP. Cần Thơ | Nguyễn Thanh Trí | 23521645 | 
| Cà Mau | Lê Tùng Bảo  | 22520016 |
 
### Phân công đường
 
| Người | Cao tốc | Quốc lộ |
|---|---|---|
| Kiệt | Cao tốc TP.HCM – Trung Lương | Quốc lộ 22 |
| Hùng | Cao tốc Trung Lương – Mỹ Thuận | Quốc lộ 62 |
| Ân | Cao tốc Mỹ Thuận – Cần Thơ | Quốc lộ 80 |
| Trang | Cao tốc Lộ Tẻ – Rạch Sỏi | Quốc lộ 91 |
| Anh | Cao tốc Bến Lức – Long Thành | Quốc lộ 60 |
| Quang | Cao tốc TP.HCM – Long Thành – Dầu Giây | Quốc lộ 63 |
| Tâm |  | Quốc lộ 50, Quốc lộ 61 |
| Trí |  | Quốc lộ 56, Quốc lộ 1A |
 
### Phân công đại học
 
| Người | Trường đại học |
|---|---|
| Tâm | ĐH Bách khoa – ĐHQG TP.HCM, ĐH Sư phạm TP.HCM |
| Ân | ĐH Phạm Ngọc Thạch, ĐH Y Dược TP.HCM |
| Trí | ĐH Thủ Dầu Một (Bình Dương), ĐH Đồng Nai |
| Trang | ĐH Tân Tạo (Long An), ĐH Cần Thơ |
| Quang | ĐH Y Dược Cần Thơ, ĐH Tiền Giang |
| Anh | ĐH Trà Vinh, ĐH An Giang |
| Hùng | ĐH Sư phạm Kỹ thuật Vĩnh Long, ĐH Kiên Giang, ĐH Võ Trường Toàn (Hậu Giang), ĐH Đồng Tháp |
| Kiệt | ĐH Công nghệ thông tin, ĐH Bà Rịa - Vũng Tàu  |
 
## Yêu cầu bài tập
 
- Vẽ bản đồ hành chính **8 tỉnh/TP** khu vực Nam Bộ (đơn vị hành chính sau sáp nhập)
- Vẽ **2n tuyến đường** quốc lộ/cao tốc (n = số thành viên nhóm = 8 → 16 tuyến)
- Vẽ **2n điểm** đại diện cho các trường đại học (→ 16 trường)
- Click vào tỉnh/TP → xem **dân số, diện tích**
- Click vào đường → xem **chiều dài, lộ giới, các tỉnh đi qua**
- Click vào trường → xem **tên trường, năm thành lập, ngành đào tạo, số sinh viên**
 
## Liên kết

- [Resources](https://github.com/vu-pt/arcgis-sample)
- [ArcGIS JS API Docs](https://developers.arcgis.com/javascript/latest/)
