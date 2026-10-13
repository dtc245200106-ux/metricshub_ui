# Nhật ký Sử dụng AI
## Dự án: Tái cấu trúc MetricsHub UI

### 🎯 Prompt 1: Flexbox vs Grid cho Bento Layout
**Prompt:** "Khi cần bố cục mà phần tử con chiếm chính xác 2 hàng và 2 cột đan xen với phần tử nhỏ, nên dùng CSS Grid hay Flexbox?"

**Trả lời:** Dùng **CSS Grid** vì:
- Flexbox chỉ xử lý **1 chiều** (row hoặc column).
- Grid xử lý **2 chiều** đồng thời → dễ dàng `span 2 rows, 2 columns`.
- Flexbox phải dùng nested containers + fixed height → tạo "Div Soup".

**Áp dụng:** Chuyển `.bad-dashboard` sang `.grid-dashboard` với `grid-template-columns`.

---

### 🎯 Prompt 2: col-sm-4 vs col-md-4
**Prompt:** "Sự khác biệt giữa col-sm-4 và col-md-4 trong Bootstrap 5?"

**Trả lời:**
- `col-sm-4`: Áp dụng từ **≥ 576px** (mobile ngang).
- `col-md-4`: Áp dụng từ **≥ 768px** (tablet).
- Dưới breakpoint → full-width (`col-12`).

**Áp dụng:** Dùng `col-12 col-md-4` cho Pricing → mobile 1 cột, tablet+ 3 cột.

---

### 🎯 Prompt 3: Bootstrap Grid dùng Flexbox?
**Prompt:** "Tại sao Bootstrap Grid lại dùng Flexbox ngầm bên dưới?"

**Trả lời:**
- Từ Bootstrap 4, `.row` được định nghĩa là `display: flex; flex-wrap: wrap;`.
- `.col-*` là các flex items với `flex: 0 0 auto; width: X%`.
- Bootstrap bọc Flexbox trong API 12 cột → dễ dùng hơn.

**Áp dụng:** Hiểu rằng Bootstrap Grid không phải công nghệ mới, chỉ là wrapper của Flexbox.

---

### 🎯 Prompt 4: gap cho Flexbox và Grid
**Prompt:** "Thuộc tính gap có hỗ trợ cho cả Flexbox và Grid không?"

**Trả lời:**
- **Grid:** `gap` hỗ trợ từ đầu.
- **Flexbox:** `gap` hỗ trợ từ Chrome 84+, Firefox 63+ (2020+).
- Thay thế `margin` lộn xộn → code sạch hơn.

**Áp dụng:** Dùng `gap: 20px` cho `.grid-dashboard` thay vì margin.

---

### 🎯 Prompt 5: Bento Box Grid Syntax
**Prompt:** "Cú pháp CSS Grid để tạo Bento Box: 1 hình vuông lớn 2x2 bên trái, 2 hình nhỏ bên phải?"

**Trả lời:**
```css
.bento {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-auto-rows: 180px;
    gap: 20px;
}
.large { grid-column: span 2; grid-row: span 2; }