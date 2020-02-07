# Section

Section là khái niệm xác định một module hoặc nhiều module được nằm trong 1 bố cục tràn ngang màn hình.

Chẳng hạn, đây có thể là 1 và cũng có thể là 2 section. Điều này tùy thuộc vào nội dung có tính chất liên quan giữa các nội dung.

![Hero Intro](media/hero-intro.png)

## Đặt tên module

Đọc bài viết: [Cách đặt tên class cho element trong markup HTML](https://codetot.net/dat-ten-class-section-html/)

Các module nên theo quy tắc đặt tên tiếng Anh và có tính tái sử dụng cao.

### Đặt tên tiếng Anh

**Các module trên cùng**

```
hero-title (có ảnh nền, kèm title)
hero-two-up (chia 2 cột, gồm cả title và ảnh)
page-title (tương tự hero-title, nhưng cho page, không có ảnh nền)
```

**Các module dưới cùng**

```
bottom-cta (tương tự hero, có ảnh nền, nhưng nằm dứoi cùng, có title + button)
newsletter (chứa form submit vào mailing list)
```

**Các module theo layout (bố cục chia cột)**

Có thể thay đổi thành `three-up`, `four-up` tùy theo layout nào hiển thị trên màn hình desktop.

```
two-up
two-up-image
two-up-intro
two-up-info
two-up-cards
```

### Tính tái sử dụng và mở rộng của module

Chẳng hạn, có nhiều module mang tính chất **Hero** (thường nằm đầu trang, có Heading 1, có button), nhưng sẽ có các style khác nhau.

- **Hero Title**: class `hero-title` section đơn thuần là nền màu xám + chữ màu đen, cân trái
- **Hero Title (Dark Version)**: class `hero-title hero-title--dark-bg` section như trên, màu nền tối và chữ trắng
- **Hero Center**: class `hero-title hero-title--center` thêm khả năng cân giữa cho hero title 1 và 2.

Thật thú vị, phải không? Nếu bạn tùy biến nó bằng cách chỉ gán class vào module và sửa các element bên trong, mọi thứ dễ theo dõi hơn nhiều.

Hãy thử nhìn trong code SaSS:

```scss
/** Nguyên bản **/
.hero-title {}
.hero-title__inner {}

/** Mở rộng tính năng **/
.hero-title--dark-bg {
  .hero-title__inner {
    background: $c-dark;
  }
}
.hero-title--center {
  .hero-title__inner {
    justify-content: center;
  }
}
```

Demo:

![Hero Title](media/hero-title.png)

![Hero Title - Version 2](media/hero-title-2.png)

