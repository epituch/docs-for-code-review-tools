Pattern: Too many universal selectors

Issue: -

## Description

This rule resolves nested selectors before counting the number of universal selectors. Each selector in a [selector list](https://www.w3.org/TR/selectors4/#selector-list) is evaluated separately.

The `:not()` pseudo-class is also evaluated separately. The rule processes the argument as if it were an independent selector, and the result does not count toward the total for the entire selector.

## Examples

`int`: Maximum universal selectors allowed.

For example, with `2`:

The following patterns are considered violations:

```css
* * * {}
```

```css
* * {
  & * {}
}
```

```css
* * {
  & > * {}
}
```

The following patterns are *not* considered violations:

```css
* {}
```

```css
* * {}
```

```css
.foo * {}
```

```css
*.foo * {}
```

```css
/* each selector in a selector list is evaluated separately */
*.foo,
*.bar * {}
```

```css
/* `*` is inside `:not()`, so it is evaluated separately */
* > * .foo:not(*) {}
```

## Further Reading

* [stylelint - selector-max-universal](https://stylelint.io/user-guide/rules/selector-max-universal)