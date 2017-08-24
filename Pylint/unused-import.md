Pattern: Unused import

Issue: -

## Description

Imported modules or variables that are declared and not used in the code are most likely an error due to incomplete refactoring. Such arguments take up space in the code and can lead to confusion by readers. Use or remove them to resolve this issue.


Example of **incorrect** code:
```python
import argparse

def some_method(firstArg):
    return firstArg*2
```

Example of **correct** code:
```python
def some_method(firstArg):
    return firstArg*2
```