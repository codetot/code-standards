# SCSS Standards

## Không nesting class mặc định

Các lớp cha-con mặc định (không bi override) thì không cần lồng trong - ngoài.

```scss
/** Correct **/
.hero-title {}
.hero-title__inner {}
.hero-title__button {}

/** Incorrect **/
.hero-title {
  .hero-title__inner {}
  .hero-title__button {}
}
```

## Viết Media query bên trong class

Giữ 1 line spacing để trông dễ nhìn hơn.

```scss
.hero-title {
  margin-top: 20px;
  
  @include from('m') {
    margin-top: 40px;
  }
  @include from('l') {
    margin-top: 80px;
  }
}
```
