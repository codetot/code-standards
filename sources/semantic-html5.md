# Semantic HTML5

Các quy ước về semantic HTML5 bao gồm việc sử dụng đúng các thẻ tag.

## Tại sao cần sử dụng Semantic HTML5

Nó là thành phần chính giúp Accessiblity (khả năng tương tác giữa người dùng có khuyết tật hay của các máy đọc - screen read) tăng lên thông qua việc lập trình viên sử dụng code quy ước.

## Bắt đầu từ đâu?

Sử dụng các tag có tính tổng thể bố cục trên website, ví dụ:

```html5
<header></header>
<main></main>
<footer></footer>
```

### Navigation `<nav>`

```html5
<nav>
  <ul>
    <li>
      <a href=""></a>
    </li>
  </ul>
</nav>
```


### Tag `<section>`

```html5
<section>
  <!-- Bên trong phải có ít nhất 1 thẻ Heading, vd H1, H2 thì mới dùng <section> -->
  <h1></h1>
</section>
```

Một web có thể có nhiều `<section>`, quy ước đó là 1 module trong thành phần báo giá.

```html5
<main>
  <section class="hero-title"></section>
  <section class="two-up"></section>
  <div class="intro"></div>
  <section class="intro-cta"></section>
</main>
```

Trong `<section>` có thể có các semantic HTML5 khác

```html5
<section>
  <!-- Khi Heading + paragraph ngay sau thì có thể dùng <header -->
  <header>
    <h2>Title</h2>
    <p>A small paragraph below.</p>
  </header>
  <div></div>
  <footer>
    <a class="button" href="">A CTA button</a>
  </footer>
</section>
```

### Tag `<button>`

Nếu trong `<button>` chỉ có icon, ví dụ, `<span class="fa fa-bar"></span>` thì phải sử dụng `aria-label` để định nghĩa về nút. Nếu không screen read không hiểu nó là cái gì.

```html5
<button class="header__button" aria-label="Toggle a mobile menu">
  <span class="fa fa-bar"></span>
  <span class="fa fa-bar"></span>
  <span class="fa fa-bar"></span>
</button>
```

### Input cần có label (có thể ẩn đi cho giống design bằng class)

```html5
<label for="input-email" class="scr-read-only">Email</label>
<input type="email" id="input-email" value="" placeholder="">
```

### Media

**Bắt buộc sử dụng `alt=""` trong tag `<img>`

Có, hiện.
Không có, để trống `alt=""`

Trong WordPress:

- Khuyến khích dùng `the_post_thumbnail()`.
- Trường hợp cần dùng với ảnh nền, sử dụng `get_the_post_thumbnail_url()`

**Hình ảnh cần đặt trong tag `<figure>` tag**

```html5
<figure class="image-wrapper">
  <img src="" class="" alt="">
  <!-- Nếu ảnh cần caption -->
  <figcaption>Caption text</figcaption>
</figure>
```

**Thời gian trong tag `<time>`

Các bài viết (post) đều cần có thời gian khởi tạo, gọi chung là meta post.

```html5
<p>The concert starts at <time datetime="2018-07-07T20:00:00">20:00</time>.</p>
```

**Trích dẫn sử dụng `<blockquote>`

```html5
<blockquote>
  <!-- Có thể có nhiều dòng -->
  <p></p>
  <p></p>
  <!-- Dòng cuối là tên tác giả trích dẫn -->
  <footer>—Aldous Huxley, <cite>Brave New World</cite></footer>
</blockquote>
```
