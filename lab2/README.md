# Lab 2 – Biểu Diễn Dữ Liệu Không Gian 3D: Nhà Hát Opéra Garnier

Bài tập nhóm môn **IE402 – GIS 3D** (ĐH Công nghệ Thông tin, ĐHQG TP.HCM).

## Mô tả

Ứng dụng web GIS hiển thị mô hình **3D công trình kiến trúc** của **Nhà hát Opéra Garnier (Paris, Pháp)** sử dụng **ArcGIS JavaScript API**, bao gồm:

- **Khối chính** của tòa nhà với chiều cao được extrude (~30–40m)
- **Các phần mái** riêng biệt với height và màu sắc khác nhau
- **Cột phía trước** được chia nhỏ polygon để tăng độ chính xác
- **Hai cánh bên** công trình với chiều cao khác khối chính
- **Cửa chính và cửa sổ** dạng polygon nhỏ (height 5–10m)
- **Popup thông tin** khi click vào từng phần (tên, chiều cao)
- Toàn bộ dữ liệu ở **mức độ chi tiết LOD3**

## Công nghệ sử dụng

| Công nghệ | Phiên bản | Mục đích |
|---|---|---|
| [ArcGIS JS API](https://developers.arcgis.com/javascript/latest/) | 5.x | Nền bản đồ 3D, hiển thị SceneLayer |
| GeoJSON / JSON | – | Lưu trữ dữ liệu footprint & thuộc tính |
| HTML / CSS / JS | – | Giao diện và logic |

## Cấu trúc thư mục

```
lab2/
├── data/
│   └── part1.geojson ...   # Các dữ liệu GeoJSON toàn bộ công trình
├── index.html                  # File chính của ứng dụng
└── README.md
```

## Cách chạy

Mở `index.html` trực tiếp trong trình duyệt (hoặc qua Live Server trong VS Code).

> **Lưu ý**: Dữ liệu GeoJSON được load local, không cần server. Mỗi feature trong file GeoJSON chứa thuộc tính `height` để ArcGIS extrude thành khối 3D và `color` để phân biệt các phần của công trình.


## Phân công nhóm

| Họ và tên | MSSV | Phân công |
|---|---|---|
| Trịnh Thanh Tâm | 23521395 | Tạo project HTML (ArcGIS JS), gộp toàn bộ GeoJSON, kiểm tra hiển thị 3D hoàn chỉnh |
| Ngô Tuấn Kiệt | 22520719 | Vẽ polygon footprint toàn công trình, đảm bảo đúng tọa độ & khép kín |
| Lê Tùng Bảo Ân | 22520016 | Tạo khối chính, thiết lập height chính (~30–40m) |
| Lê Thị Thùy Trang | 23521627 | Vẽ các phần mái riêng biệt, height thấp hơn + khác màu |
| Nguyễn Thanh Trí | 23521645 | Tạo các khối cột phía trước, chia nhỏ polygon để giống thực tế |
| Dương Nguyễn Nhật Quang | 23521278 | Hai bên công trình, extrude với height khác khối chính |
| Trần Nguyễn Ngọc Hùng | 23520578 | Cửa chính, cửa sổ (polygon nhỏ), height thấp (5–10m) |
| Nguyễn Trần Bảo Anh | 22520066 | Tô màu từng phần , thêm popup |

## Yêu cầu bài tập

- Thu thập dữ liệu công trình dưới dạng **GeoJSON**
- Biểu diễn công trình ở **mức độ chi tiết LOD3**
- Hiển thị trên **bản đồ 3D ArcGIS JS**

## Liên kết

- [ArcGIS JS API Docs](https://developers.arcgis.com/javascript/latest/)
- [Resources Lab](https://github.com/vu-pt/arcgis-sample)
