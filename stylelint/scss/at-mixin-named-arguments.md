Pattern: Malformed named parameter for `@include`

Issue: -

## Description

Require or disallow named parameters in at-mixin call rule.

```scss
@include animation($duration: 250ms) {
//                 ↑
// Require or disallow this
```

## Examples

`string`: `"always"|"never"`

### `always`

The following patterns are considered warnings:

```scss
.foo {
  @include animation(250ms, 100ms, infinite);
} 
```

```scss
.foo {
  @include animation(250ms);
} 
```

```scss
.foo {
  @include reset($value: 20, 'bar', $color: #FFF);
}
```

The following patterns are *not* considered warnings:

```scss
.foo {
  @include animation($duration: 250ms);
}
```

```scss
.foo {
  @include animation($duration: 250ms, $delay: 100ms, $direction: infinite);
}
```

### `never`

The following patterns are considered warnings:

```scss
.foo {
  @include reset($value: 20);
}
```

```scss
.foo {
  @include animation($duration: 250ms, $delay: 100ms, $direction: infinite);
}
```

```scss
.foo {
  @include reset($value: 20, 'bar', $color: #FFF);
}
```

The following patterns are *not* considered warnings:

```scss
.foo {
  @include animation(250ms, 100ms, infinite);
} 
```

## Configuration

### `"ignore": ["single-argument"]`

Given:
```json
{ "ignore": ["single-argument"] }
```

The following patterns are *not* considered warnings:

```scss
.foo {
  @include animation($duration: 250ms);
}
```

```scss
.foo {
  @include reset(20);
}
```

## Further Reading

* [stylelint-scss - at-mixin-named-arguments](https://github.com/kristerkari/stylelint-scss/blob/master/src/rules/at-mixin-named-arguments)