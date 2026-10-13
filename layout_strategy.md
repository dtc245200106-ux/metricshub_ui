# Chiến lược Layout - MetricsHub Dashboard

## 🎯 Nguyên tắc: "Grid làm Layout, Flexbox làm Component"

### 1. Navbar → **Flexbox** (1D)
- **Lý do:** Các phần tử xếp theo **1 chiều ngang**, cần tự động giãn theo nội dung.
- **Kỹ thuật:** `display: flex; justify-content: space-between; align-items: center;`
- **Ưu điểm:** Khi đổi ngôn ngữ sang tiếng Đức (từ dài), navbar tự động điều chỉnh mà không bị tràn.

### 2. Dashboard → **CSS Grid** (2D)
- **Lý do:** Các widget có **kích thước khác nhau** (span 2 hàng, span 2 cột) → cần không gian **2 chiều**.
- **Kỹ thuật:** `display: grid; grid-template-columns: repeat(3, 1fr);` + `grid-column: span 2; grid-row: span 2;`
- **Ưu điểm:** Loại bỏ hoàn toàn các thẻ `<div class="column">` lồng nhau (Div Soup) → DOM phẳng, dễ đọc.

### 3. Pricing → **Bootstrap Grid** (12 cột)
- **Lý do:** Layout **3 cột bằng nhau** chuẩn → không cần viết CSS thuần.
- **Kỹ thuật:** `<div class="row">` + `<div class="col-12 col-md-4">`
- **Ưu điểm:** Tự động responsive (3 cột trên desktop → 1 cột trên mobile) mà không cần viết Media Query.

## 💡 Kết luận

- **Flexbox** = công cụ cho **1 chiều** (Navbar, button group, card footer).
- **CSS Grid** = công cụ cho **2 chiều** (Bento Dashboard, gallery, layout tổng).
- **Bootstrap** = công cụ cho **layout chuẩn 12 cột** cần tốc độ triển khai.