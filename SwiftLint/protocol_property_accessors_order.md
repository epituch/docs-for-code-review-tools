Pattern: Wrong property accessors order

Issue: -

## Description

When declaring properties in protocols, the order of accessors should be `get set`.

Examples of **correct** code:
```swift
protocol Foo {
 var bar: String { get set }
 }


protocol Foo {
 var bar: String { get }
 }


protocol Foo {
 var bar: String { set }
 }

```
Examples of **incorrect** code:
```swift

protocol Foo {
 var bar: String { ↓set get }
 }

```

## Further Reading

* [SwiftLint - Protocol Property Accessors Order](https://github.com/realm/SwiftLint/blob/master/Rules.md#protocol-property-accessors-order)