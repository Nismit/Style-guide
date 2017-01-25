# CSS / SASS Style Guide

In personal CSS/SASS style guide in 2017, It will be updated constantly.
It is influenced by [BEM](https://en.bem.info/), [OOCSS](http://oocss.org/), [SMACSS](https://smacss.com/) and [FLOCSS](https://github.com/hiloki/flocss)

## Objective

Nowadays, CSS files have been bigger than before.
It's gonna be hard to maintain or expand after that, a new selector will be made. I'd like to avoid this thing, so I made this style guide for CSS/SASS development.

- Consistency
- Maintainable
- Readable
- DRY
- KISS

## CSS

### Formatting

- DO NOT USE ID SELECTOR(S)
- Use 2 spaces for indentation
- Use BEM + SMACSS naming convention for class name
- Put a space between class selector(s) and opening brace `{`
- Put a space after `:` in properties
- Put closing brace `}` on a new line
- Put a blank line between declarations

**Bad**

```css
.block{
    width: 100px;
    border:1px solid #000;}
.block,.block2{
  //
}
#block {
  //
}
```

**Good**

```css
.block {
  width: 100px;
  border: 1px solid #000;
}

.block, .block2 {
  //
}
```

### Comments

- Basically, use double slash `//`
- Write comments, it will help everyone ;)

## Sass

Use partial Sass files, all partial files should include `style.scss`

### Syntax

- Use the `scss` syntax

### Ordering of property declarations

1. Property declarations

  List all standard property declarations, anything that isn't an `@include` or a nested selector.

  ```scss
  .parent {
    border: 1px solid #000;
    background-color: #fff;
    //
  }
  ```

2. `@include` declarations

  Grouping `@include`s at the end makes it easier to read the entire selector.

  ```scss
  .parent {
    border: 1px solid #000;
    background-color: #fff;
    @include transition(background 0.5s ease);
    //
  }
  ```

3. Nested selectors

  Put a whitespace above a nested selector

  ```scss
  .parent {
    border: 1px solid #000;
    background-color: #fff;
    @include transition(background 0.5s ease);

    &__child {
      //
    }
  }
  ```

### Variables

- Dash-cased variable names `$local-variable`
- Global variable names add the prefix `_` and based in filename in variable directory (e.g. `$_filename-variable`).
- Local variable names do not need the prefix but create it in mixin or module directories.

### Mixins

If you repeat the code, you should make a mixin.
Do not forget DRY and KISS principle.

**File Name**
`_mixin-name.scss`

**Directory**
`src/sass/mixin/`

### Nested Selectors

Do not nest selectors more than three levels deep.

```scss
.parent {
  // Block

  &__child {
    // Element

    &--grandchild {
      // Modifier
    }
  }
}
```
 
## Directory Structure

Directory structure is based on　BEM + FLOCCSS

- **foundation** set up for basic in CSS development
  - **base** normalize or reset file and initial file
  - **function** function files for SASS
  - **mixin** mixin files
  - **utility** margin, padding, display etc.
  - **variable** set variables 
- **layout** defines layout for website
- **mixin** uses mixin in locally.
- **module** 

```
src/sass
├── foundation
│   ├── base
│   │   ├── _init.scss
│   │   ├── _normalize.scss
│   │   └── _reset.scss
│   ├── function
│   │   ├── _em-calc.scss
│   │   └── _strip-unit.scss
│   ├── mixin
│   │   ├── _clearfix.scss
│   │   ├── _flex.scss
│   │   ├── _font-size.scss
│   │   └── _mediaquery.scss
│   ├── utility
│   │   ├── _animation.scss
│   │   ├── _bg-color.scss
│   │   ├── _display.scss
│   │   ├── _float.scss
│   │   ├── _margin.scss
│   │   ├── _padding.scss
│   │   └── _text.scss
│   └── variable
│       ├── _breakpoints.scss
│       ├── _color.scss
│       ├── _easing.scss
│       ├── _font.scss
│       └── _others.scss
├── layout
│   ├── _footer.scss
│   ├── _header.scss 
│   └── _section.scss
├── mixin
│   └── _example.scss
├── module
│   └── _example.scss
└── style.scss
```    

## References

- [BEM](https://en.bem.info/)
- [OOCSS](http://oocss.org/)
- [SMACSS](https://smacss.com/)
- [FLOCSS](https://github.com/hiloki/flocss)
- [Airbnb CSS / Sass Styleguide](https://github.com/airbnb/css#ordering-of-property-declarations)
- [Primer](http://primercss.io/)
