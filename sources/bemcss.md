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

## Extending luôn gán cho class ngoài cùng (module)

Cần đảm bảo việc class ngoài cùng sẽ sửa các element bên trong.

```html
<section class="hero-title"></section>
<section class="hero-title hero-title--center"></section>
```

```scss
.hero-title {}
.hero-title__inner {}

/** Extending **/
.hero-title--center {
  .hero-title__inner {
    text-align: center;
  }
}
```

## Mỗi class thực hiện một tính năng

Tận dụng tối đa thế mạnh tái sử dụng bằng việc các class xử lý riêng, giúp 1 module có thể có nhiều layout/style khác nhau.

```html
<section class="hero-title"></section>
<section class="hero-title hero-title--center"></section>
<section class="hero-title hero-title--dark-bg hero-title--white-text"></section>
<section class="hero-title hero-title--center hero-title--dark-bg"></section>
```

## Kết hợp giữa global class và module class

Global class chủ yếu là layout (`.container`, `.grid`, .`grid__col`) hay typography (`.h1`, `.h2`, `.section-title`, .`label-text`) giúp design nhất quán cho tất cả module.

```html
<section class="hero-title">
  <div class="container hero-title__container">
    <h1 class="h1 hero-title__headline">Hero Headline</h1>
  </div>
</section>
```

```scss
/** Global class (no module, reusable) **/
.container {
  margin: 0 auto;
  padding: 0 20px;
  max-width: 1440px;
}

/** Typography class **/
.h1 {
  font-family: '';
  font-size: '';
  line-height: '';
  letter-spacing: '';
  text-transform: '';
}

/** Module classes: Hero Title **/
.hero-title__container {
  max-width: 800px;
}
.hero-title__headline {
  color: $c-dark;
}
```
