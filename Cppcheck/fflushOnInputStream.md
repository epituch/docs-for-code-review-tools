Pattern: `fflush()` on input stream

Issue: -

## Description

`fflush()` called on input stream `stdin` may result in undefined behaviour on non-Linux systems.

## Further Reading

* [Common Weakness Enumeration (CWE) - 398](https://cwe.mitre.org/data/definitions/398.html)