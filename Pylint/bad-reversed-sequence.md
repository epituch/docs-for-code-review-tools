Pattern: Wrong `reversed()` sequence

Issue: -

## Description

Used when the first argument to `reversed()` built-in isn't a sequence (does not implement `__reversed__`, nor `__getitem__` and `__len__`).
