# Javascript

## Sử dụng ES6 trong các project

Một quy ước là trong các project có sử dụng `babel` để dịch code từ ES6+, thì trên các phần sử dụng sẽ đều cần viết bằng ES6.

## Sử dụng thư viện có sẵn để tái sử dụng cao

```javascript
/** dom.js **/
const selectAll = (selector) => Array.prototype.slice.call(document.querySelectorAll(selector))

/** hero-title.js **/
import { selectAll } from 'lib/dom'

export default el => {
  const items = selectAll('.js-item', el)
}
```

## Quy tắc tạo Javascript theo từng module

Trên các project, cách thức tạo module thường như sau:

```html
<div class="faq" data-module="faq">
  <div class="faq__items">
    <div class="faq__item js-item">
      <button class="faq__item-header" role="switch" aria-checked="false" data-toggle>
        <h3 class="faq__item-title"></h3>
        <span class="faq__icon"></span>
      </button>
      <div class="faq__item-content" data-body></div>
    </div>
  </div>
</div>
```

**Các đặc điểm:**

- Sử dụng `data-module=""` để gọi tới file `/src/js/modules/*.js` hoặc `/modules/*/*.js`
- Các selector được gọi thông qua prefix `.js-`. hoặc `data-x`

## Đặt tên biến

```javascript
# Nếu biến được gọi ngoài module, viết ngoài `export default el => {}`

const body = document.body
const popups = selectAll('[data-module="popup"]')

# Nếu biến là static class, viết hoa + dấu `_` giữa các từ

const ACTIVE_CLASS = 'modal--active'

# Nếu biến nằm trong 1 module cố định, viết trong `export default el => {}`
# Sử dụng biến với scope nhỏ (trong chỉ module đó) giúp module đó hoạt động độc lập và có performance cao hơn so với dùng jQuery

export default el => {
  const buttonEl = select('.js-button', el)
}
```

## Tránh các Regression xảy ra do chưa check điều kiện của element thực thi có tồn tại hay không

```javascript
import { select, on } from 'lib/dom'

export default el => {
  const buttonEl = select('.js-scroll-down-button', el)
  
  /** Missing check `if (buttonEl) {}`
  on('click', () => {}, buttonEl)
}
```
