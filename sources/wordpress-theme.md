# Tài liệu hướng dẫn cài đặt và phát triển theme SHAC

## Yêu cầu

Trên máy có

- NodeJS phiên bản 12.0+
- Sử dụng 1 web server nào đó chạy được virtual domain
- IDE hỗ trợ editorconfig
- Cài sẵn Git (để đẩy lên branch theo Git Flow).

## Cài đặt theme

- Clone dự án về máy
- Cài virtual domain theo dự án, ví dụ `codetot.test`
- Import database và (1) update url trong table `wp_options` về domain `codetot.test`, (2) đổi username về mật khẩu để access vào backend.
- Vào thư mục `wp-content/themes/<tên theme>/`, chạy `npm install`

## Dev

- Gõ lệnh `npm run watch`, truy cập vào `https://localhost:3000`

## Cấu trúc

```
src/postcss/**.css
```

- Viết theo syntax của postCSS, hỗ trợ custom media `@media (--m) {}`, viết mobile first
- Đặt tên class theo BEM cho các khu vực section/block dùng chung.

```
src/js/blocks/*.js
```

Là các JS file được viết riêng cho mỗi block, viết bằng ECMA5+ (hỗ trợ ES6).

Để thêm mới thì cần tạo file trùng tên, ví dụ `hero-slider.js`, và gắn `data-block="hero-slider"` vào 1 block nào đó. Tham khảo cách tạo header, mobile menu,... để biết cách tổ chức này. Khi gán xong thì chạy lại `npm run watch`.

```
export default el => {
  console.log(el) // => chính là Node "<div class="hero-slider"></div>"
}
```

**Blocks**

```
blocks/*.php
```

Dùng độc lập, có thể truyền biến vào từng block thông qua function helper `the_block()`

```
<?php
the_block('hero-slider', array(
  'title' => get_sub_field('title') // String
  'items' => get_sub_field('items') // Array
));

// Bên trong blocks/hero-slider.php

if (!empty($title)) :
  echo $title;
endif;
?>
```

## Quy tắc Git

- Khi dev, tạo branch từ nhánh develop ra, đặt tên:

```
feature/<block-name> // nếu làm 1 block mới
bugfix/<block-name> // nếu sửa lỗi 1 block cũ, hoặc feature/ được merge vào develop/master rồi
```

Khi đẩy lên `git push`, nhánh sẽ được tạo Pull Request tự động vào branch `develop`, và được test trên CircleCI. Nếu báo lỗi thì kiểm tra trên máy bằng cách gõ lệnh `npm run test`.
