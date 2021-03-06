Pattern: Malformed quotes for _URL_

Issue: -

## Description

Require or disallow quotes for urls. This rule ignores `@import` in Less.

## Examples

### `"always"`

Urls *must always* be quoted.

The following patterns are considered violations:

```css
@import url(foo.css);
```

```css
@document domain(http://www.w3.org/);
```

```css
@font-face { font-family: 'foo'; src: url(foo.ttf); }
```

```css
@-moz-document url-prefix() {}
```

The following patterns are *not* considered violations:

```css
a { background: url('x.jpg'); }
```

```css
@import url("foo.css");
```

```css
@document domain('http://www.w3.org/');
```

```css
@font-face { font-family: "foo"; src: url("foo.ttf"); }
```

```css
@-moz-document url-prefix('') {}
```

### `"never"`

Urls *must never* be quoted.

The following patterns are considered violations:

```css
a { background: url('x.jpg'); }
```

```css
@import url("foo.css");
```

```css
@font-face { font-family: "foo"; src: url('foo.ttf'); }
```

The following patterns are *not* considered violations:

```css
a { background: url(x.jpg); }
```

```css
@import url(foo.css);
```

```css
@font-face { font-family: 'foo'; src: url(foo.ttf); }
```

# Configuration

### `except: ["empty"]`

Reverse the primary option if the function has no arguments.

For example, with `"always"`.

The following pattern is *not* considered violations:

```css
@-moz-document url-prefix() {}
```

## Further Reading

* [stylelint - function-url-quotes](https://stylelint.io/user-guide/rules/function-url-quotes)