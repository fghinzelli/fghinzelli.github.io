# SCSS

## Sintax and commands
```scss
/* Nested items */
.container {
  nav {
    ul {
      li {
        display: inline-block;
      }
    }
  }
}


/* Include from another file */
@import './file';

/* Variables */
$my-color: #000000;

h1 {
  color: $my-color;
}

/* Functions */
@mixin color-and-size {
  color: $mycolor;
  font-size: 14px;
}

@mixin with-parameters ($type) {
  @if $type == 'foo' {
    color: #000000;
  }
  @else {
    color: #010101;
  }
}

h1 {
  @include color-and-size;
}

h2 {
  @include $with-parameters('bar');
}




```

# SASS
