# WordPress - Standard

## Sử dụng `.editorconfig` cài trên IDE

Các project đều có file `.editorconfig` để đảm bảo tab indent trong code giống nhau. Developer làm trên các project đều cần đảm bảo IDE (trình soạn thảo code) đã hỗ trợ plugin này.

File `.editorconfig` mẫu từ WordPress project:

```
# This file is for unifying the coding style for different editors and IDEs
# editorconfig.org

# WordPress Coding Standards
# https://make.wordpress.org/core/handbook/coding-standards/

root = true

[*]
charset = utf-8
end_of_line = lf
insert_final_newline = true
trim_trailing_whitespace = true
indent_style = tab

[*.yml]
indent_style = space
indent_size = 2

[*.md]
trim_trailing_whitespace = false

[{*.txt,wp-config-sample.php}]
end_of_line = crlf
```

## Điều kiện

Không thể output ra 1 HTML rỗng mà nên kiểm tra xem có tồn tại không đã.

```php
<?php
$hero_title = get_field('hero_title'); // String...
...
$hero_enable_cta = get_field('hero_enable_cta'); // Boolean true/false
?>

<?php if( !empty($hero_title) ) : ?>
  <h1 class="hero__title"><?php echo $hero_title; ?></h1>
<?php endif; ?>
<?php if( isset($hero_enable_cta) && $hero_enable_cta ) : ?>
  <footer class="hero__footer">
    <a class="button hero__button" href="<?php echo $hero_button_url; ?>"><?php echo $hero_button_text; ?></a>
  </footer>
<?php endif; ?>
```
