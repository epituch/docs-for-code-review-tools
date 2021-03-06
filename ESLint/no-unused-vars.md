Pattern: Disallow Unused Variables

Issue: -

## Description

Variables that are declared and not used anywhere in the code are most likely an error due to incomplete refactoring. Such variables take up space in the code and can lead to confusion by readers.

## Rule Details

This rule is aimed at eliminating unused variables, functions, and parameters of functions.

A variable is considered to be used if any of the following are true:

* It represents a function that is called (`doSomething()`)
* It is read (`var y = x`)
* It is passed into a function as an argument (`doSomething(x)`)
* It is read inside of a function that is passed to another function (`doSomething(function() { foo(); })`)

A variable is *not* considered to be used if it is only ever assigned to (`var x = 5`) or declared.

Examples of **incorrect** code for this rule:

```js
/*eslint no-unused-vars: "error"*/
/*global some_unused_var*/

// It checks variables you have defined as global
some_unused_var = 42;

var x;

// Write-only variables are not considered as used.
var y = 10;
y = 5;

// A read for a modification of itself is not considered as used.
var z = 0;
z = z + 1;

// By default, unused arguments cause warnings.
(function(foo) {
    return 5;
})();

// Unused recursive functions also cause warnings.
function fact(n) {
    if (n < 2) return 1;
    return n * fact(n - 1);
}

// When a function definition destructures an array, unused entries from the array also cause warnings.
function getY([x, y]) {
    return y;
}
```

Examples of **correct** code for this rule:

```js
/*eslint no-unused-vars: "error"*/

var x = 10;
alert(x);

// foo is considered used here
myFunc(function foo() {
    // ...
}.bind(this));

(function(foo) {
    return foo;
})();

var myFunc;
myFunc = setTimeout(function() {
    // myFunc is considered used
    myFunc();
}, 50);

// Only the second argument from the descructured array is used.
function getY([, y]) {
    return y;
}
```

### exported

In environments outside of CommonJS or ECMAScript modules, you may use `var` to create a global variable that may be used by other scripts. You can use the `/* exported variableName */` comment block to indicate that this variable is being exported and therefore should not be considered unused.

Note that `/* exported */` has no effect for any of the following:

* when the environment is `node` or `commonjs`
* when `parserOptions.sourceType` is `module`
* when `ecmaFeatures.globalReturn` is `true`
