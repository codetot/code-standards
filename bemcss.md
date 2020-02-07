# BEM CSS

Đặt tên class theo tiêu chuẩn BEM CSS là điều quan trọng giúp các dự án của Code Tốt hạn chế khả năng khó sửa code và giảm thiểu rủi ro do xử lý đa tầng khi tái sử dụng module.

Tham khảo bài viết: [Toàn tập về BEM CSS](https://codetot.net/toan-tap-ve-bem-css/)

Các điểm cần nắm

## Cấu trúc `module__block` luôn đảm bảo

- `module`: tên của section
- `block`: tên của div hoặc element bố cục

## Các element được xử lý linh hoạt hơn

Nếu là element cấp độ trực tiếp, tức block bọc ngoài là duy nhất.

```
hero-title
- hero-title__wrapper
-- hero-title__title
```

Nếu là element nằm trong các block nhỏ hơn, có tính chất lặp lại element hơn 1 lần

```
two-up-intro
- two-up-intro__title # bị trùng title
- two-up-intro__grid
-- two-up-intro__col (x3)
---- two-up-intro__col-title # bị trùng title
---- two-up-intro__col-description
```

Trường hợp element không bị trùng giữa các level, có thể bỏ qua block

```
three-up
- three-up__headline
- three-up__grid
-- three-up__col (x3)
--- three-up__title (title #headline)
```
