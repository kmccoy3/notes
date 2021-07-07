
# Help

help(FUNCTION_NAME)

# Docstring Format
[pep 257 style guide](https://www.python.org/dev/peps/pep-0257/)

one-line docstring
```python
def my_func(in1):
    """Returns the square of the input."""
    return in1 ** 2
```

multi-line docstring
```python
def my_func2(in1=5, in2=6.0):
    """Multiply inputs together.
    
    Keyword arguments:
    in1 -- first input (default 5)
    in2 -- second input (default 6.0)
    """
    return in1 * in2
```

# Operations

### Arithmetic Operations
operator | name | description
-------- | ---- | -----------
a + b |	Addition |	Sum of a and b
a - b |	Subtraction |	Difference of a and b
a * b |	Multiplication |	Product of a and b
a / b |	True division |	Quotient of a and b
a // b |	Floor division |	Quotient of a and b, removing fractional parts
a % b |	Modulus |	Integer remainder after division of a by b
a ** b |	Exponentiation |	a raised to the power of b
-a |	Negation |	The negative of a

### Logical Operations
Operation |	Description | Operation | Description
--------- | ----------- | --------- | -----------
a == b |	a equal to b |	a != b |	a not equal to b
a < b |	a less than b |	a > b |	a greater than b
a <= b |	a less than or equal to b |	a >= b |	a greater than or equal to b

# Data Types

```Python
list = [1, True, 'hello']
tuple = (1, 2, 3)
dictionary = {'key':value, 'key2':value2}
```

# Helpful functions

type()
dir() # to see all attributes and methods of import
