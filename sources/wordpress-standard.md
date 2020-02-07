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
