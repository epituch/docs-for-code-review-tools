Pattern: Empty line before `@else`

Issue: -

## Description

Disallow empty lines before `@`-else.

```scss
@if ($a == 0) { }
                      /* ← */
@else if ($x == 2) { }   ↑
                         ↑
/**                      ↑
 * This empty line */
```

`@if` and `@else` statements might need to have different behavior than all the other at-rules. For that you might need to set `"ignoreAtRules": ["else"]` for stylelint's core rule [`at-rule-empty-line-before`](http://stylelint.io/user-guide/rules/at-rule-empty-line-before/). But that would make you unable to disallow empty lines before `@else` while forcing it to be on a new line. This rule is designed to solve exactly that.

## Examples

`string`: `"never"`

There is no `"always"`, `"always-single-line"` options, because for such cases stylelint's `at-rule-empty-line-before` would work.

### `"never"`

There *must never* be an empty line before `@else` statements.

The following patterns are considered warnings:

```scss
@if ($x == 1) {
  // ...
}

@else {}
```
```scss
@if ($x == 1) {
  // ...
} @else if ($x == 2) {
  // ...
}

@else { }
```

The following patterns are *not* considered warnings:

```scss
@if ($x == 1) {
  // ...
} @else if ($x == 2) {
  // ...
} @else {}
      
a {
  @if ($x == 1) {
    // ...
  }
  @else ($x == 2) {
    // ...
  }
}
```

## Further Reading

* [stylelint-scss - at-else-empty-line-before](https://github.com/kristerkari/stylelint-scss/blob/master/src/rules/at-else-empty-line-before)