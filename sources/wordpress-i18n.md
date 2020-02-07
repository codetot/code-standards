# WordPress i18n

`i18n` thực chất là viết tắt của `Internationalization`, tức là khả năng bản địa hóa (được dịch) của nội dung trong code.

Tài liệu tham khảo:

- [Internationalization](https://developer.wordpress.org/themes/functionality/internationalization/)

Quy tắc này thực ra đảm bảo các dòng code viết trong theme, plugin nên là tiếng Anh, và cho phép dịch nó sang ngôn ngữ khác thông qua các .pot. mo.

# Text Domain

Thường là tên thư mục theme/plugin.

Ví dụ

```php
# wp-content/themes/codetot/ => 'codetot' là text domain trong các ví dụ.
<?php _e('Header menu', 'codetot'); ?>
```

## Xử lý chuỗi

**`_e()` sẽ echo string**

```php
<button class="button" aria-label="<?php _e('Toggle a button', 'text-domain'); ?>"></button>
```

**`__()` chỉ return string**

```php
<?php
$default_button = __('Submit', 'text-domain');

// Muốn hiển thị thì cần echo
echo $default_button;
?>
```

**Dịch cả 2 trường hợp số ít (1) và số nhiều**

```php
$post_meta = _n( 'One post', '%s posts', $post_count, 'text-domain' );
```
