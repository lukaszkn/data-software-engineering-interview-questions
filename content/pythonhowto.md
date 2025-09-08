# Python How-To
How-to's

* [How to reverse binary file?](#How-to-reverse-binary-file)
* [Convert string of space separated integers to list of integers](#Convert-string-of-space-separated-integers-to-list-of-integers)
* [How to install packages with `pip` and `requirements.txt`](#How-to-install-packages-with-pip-and-requirements-txt)
* [Creating a `requirements.txt` file using `pip`](#Creating-a-requirements-txt-file-using-pip)
* [How to pad a number?](#How-to-pad-a-number)
* [How to get the lowercase English alphabet?](#How-to-get-the-lowercase-English-alphabet)
* [How to compute the Cartesian product of two lists?](#How-to-compute-the-Cartesian-product-of-two-lists)
* [How to count the occurrences of item in the list?](#How-to-count-the-occurrences-of-item-in-the-list)
* [How to make permutations of items of elements?](#How-to-make-permutations-of-items-of-elements)
* [How to convert the timestamp to a `datetime` object?](#How-to-convert-the-timestamp-to-a-datetime-object)
* [Decorator function time_decorator which has to calculate decorated function execution time](#Decorator-function-time-decorator-which-has-to-calculate-decorated-function-execution-time)
* [Descriptor which don't allow to set price](#Descriptor-which-don-t-allow-to-set-price)
* [Descriptor which don't allow to change field value after initialization](#Descriptor-which-don-t-allow-to-change-field-value-after-initialization)

## How to reverse binary file?
To reverse the contents of a binary file in Python, you can read the file into memory, reverse the bytes, and then write the reversed bytes back to a file. Here's a step-by-step guide on how to do that:

1. Read the binary file into memory.
2. Reverse the bytes.
3. Write the reversed bytes to a new file.

```python
def reverse_binary_file(input_file_path, output_file_path):
    # Open the input binary file in read mode and read the content
    with open(input_file_path, 'rb') as input_file:
        data = input_file.read()

    # Reverse the content
    reversed_data = data[::-1]

    # Write the reversed content to the output binary file
    with open(output_file_path, 'wb') as output_file:
        output_file.write(reversed_data)

# Example usage
input_file_path = 'example.bin'
output_file_path = 'reversed_example.bin'
reverse_binary_file(input_file_path, output_file_path)
```
Explanation:
- `rb` mode: Opens the file in binary read mode.
- `wb` mode: Opens the file in binary write mode.
- `data[::-1]`: Slices the data to reverse it.

Example:
If `example.bin` contains `b'\x01\x02\x03\x04'`, after running the script, `reversed_example.bin` will contain `b'\x04\x03\x02\x01'`.

This approach reads the entire file into memory, so it's suitable for relatively small files. If the file is very large, you might want to handle it in chunks, but that complicates the reversal process.

[Top](#top)

## Convert string of space separated integers to list of integers
Here's example using `map`
```
integer_list = map(int, input().split())
```

[Top](#top)

## How to install packages with `pip` and `requirements.txt`
To install all the packages listed in a requirements.txt file, use:

```bash
pip install -r requirements.txt
```
This will install each package listed in the file with the specified version (if provided).

[Top](#top)

## Creating a `requirements.txt` file using `pip`
To generate a `requirements.txt` file that includes all currently installed packages, use the following command:

```bash
pip freeze > requirements.txt
```
This command writes the list of installed packages and their versions to requirements.txt.

[Top](#top)

## How to pad a number?
To pad a number in Python, you can use different methods, depending on the format you need. Below are a few common ways:

### 1. Using `zfill()` for zero-padding
This method adds leading zeros to the number until it reaches the desired length:

```python
num = 42
padded_num = str(num).zfill(5)  # Pads to 5 digits
print(padded_num)  # Output: 00042
```

### 2. Using `format()` or f-strings
You can use Python's string formatting methods to pad numbers with any character, including zeros or spaces:

- **With zeros**:
```python
num = 42
padded_num = "{:05}".format(num)  # Pads to 5 digits with leading zeros
print(padded_num)  # Output: 00042
```

Or using f-strings (Python 3.6+):
```python
num = 42
padded_num = f"{num:05}"
print(padded_num)  # Output: 00042
```

- **With spaces**:
```python
num = 42
padded_num = "{:>5}".format(num)  # Pads with spaces, right-aligned to width 5
print(padded_num)  # Output: "   42"
```

### 3. Using `rjust()` for space-padding
This method right-aligns the string and pads with spaces (or another character):

```python
num = 42
padded_num = str(num).rjust(5, '0')  # Pads with zeros to width 5
print(padded_num)  # Output: 00042
```

You can adjust the padding width and the padding character based on your requirements.

[Top](#top)

## How to get the lowercase English alphabet?
In Python, you can get the lowercase English alphabet using the `string` module, which provides a convenient way to access alphabet-related constants.

Here’s how you can do it:
```python
import string

# Get lowercase English alphabet
alphabet = string.ascii_lowercase
print(alphabet)
```

### Output:
```
abcdefghijklmnopqrstuvwxyz
```

### Explanation:
`string.ascii_lowercase`: This is a string containing all lowercase letters from a to z.

[Top](#top)

## How to compute the Cartesian product of two lists?
You can use `itertools.product()` to compute the Cartesian product of two lists. The function generates all combinations of elements from the two input iterables. Each combination is returned as a tuple.

### Steps:
1. Parse the input lists from the user.
2. Use itertools.product() to compute the Cartesian product of the two lists.
3. Print the result as space-separated tuples.

### Code implementation:
```python
import itertools

# Read the input lists
A = list(map(int, input().split()))
B = list(map(int, input().split()))

# Compute the Cartesian product
cartesian_product = itertools.product(A, B)

# Print the result as space-separated tuples
print(*cartesian_product)
```

### Explanation:
- `input().split()` Reads the space-separated input and splits it into individual elements.

- `map(int, ...)` Converts the input strings into integers.

- `itertools.product(A, B)` Computes the Cartesian product of the two lists.

- `print(*cartesian_product)` Prints the result in the required format, where the * unpacks the tuples and separates them by spaces.

[Top](#top)

## How to count the occurrences of item in the list?
### Using `collections.Counter`
The `Counter` class from the `collections` module provides a convenient way to count occurrences of items in a list.

```python
from collections import Counter

# Example list
my_list = [1, 2, 3, 1, 2, 1]

# Use Counter to count occurrences
counts = Counter(my_list)

print("Occurrences:", counts)  # Output: Counter({1: 3, 2: 2, 3: 1})
```

[Top](#top)

## How to make permutations of items of elements?
To generate permutations of elements in Python, you can use the `itertools.permutations()` function. This function generates all possible ordered arrangements (permutations) of elements from a given iterable (e.g., a list or string).

### Syntax:
```python
itertools.permutations(iterable, r=None)
```
- `iterable`: The input iterable (e.g., list, string).
- `r`: The length of the permutation tuples (optional). If not provided, `r` defaults to the length of the iterable.

### Example 1: Permutations of all elements
To generate all permutations of a list:
```python
import itertools

# Example list
items = [1, 2, 3]

# Generate all permutations of length 3 (same as the length of the list)
perms = itertools.permutations(items)

# Print each permutation
for p in perms:
    print(p)
```

Output:
```
(1, 2, 3)
(1, 3, 2)
(2, 1, 3)
(2, 3, 1)
(3, 1, 2)
(3, 2, 1)
```

### Example 2: Permutations of length `r`
You can also specify the length r of the permutations. For example, to generate permutations of length 2 from a list of 3 elements:

```python
import itertools

# Example list
items = [1, 2, 3]

# Generate permutations of length 2
perms = itertools.permutations(items, 2)

# Print each permutation
for p in perms:
    print(p)
```

Output:
```
(1, 2)
(1, 3)
(2, 1)
(2, 3)
(3, 1)
(3, 2)
```

### Example 3: Permutations of characters in a string
You can also generate permutations of characters in a string:

```python
import itertools

# Example string
s = 'ABC'

# Generate all permutations of the string
perms = itertools.permutations(s)

# Print each permutation
for p in perms:
    print(''.join(p))  # Join characters to form a string
```

Output:
```
ABC
ACB
BAC
BCA
CAB
CBA
```

Summary
- `itertools.permutations()` generates all possible ordered combinations of the elements in an iterable.
- By default, it generates permutations of the same length as the iterable, but you can specify a different length `r`.

[Top](#top)

## How to convert the timestamp to a `datetime` object?
To convert a timestamp string to a `datetime` object in Python, you can use the strptime() function from the datetime module. The `strptime()` function parses a string representing a date and time according to a specified format and returns a `datetime` object.

Here's how to convert a timestamp to a datetime object:

### Steps:
1. Import the `datetime` module.
2. Use `strptime()`: Provide the timestamp string and a format string that specifies how the date and time are structured.

### Example:
Let's say you have the following timestamp string:
```
Sun 10 May 2015 13:54:36 -0700
```

To convert this string to a datetime object, you can do the following:

```python
from datetime import datetime

# Sample timestamp
timestamp = "Sun 10 May 2015 13:54:36 -0700"

# Convert the timestamp to a datetime object
dt_object = datetime.strptime(timestamp, '%a %d %b %Y %H:%M:%S %z')

# Print the resulting datetime object
print(dt_object)
```

Output:
```
2015-05-10 13:54:36-07:00
```

### Explanation of the format:
- `%a`: Abbreviated weekday name (e.g., "Sun" for Sunday).
- `%d`: Day of the month as a zero-padded decimal number (e.g., "10").
- `%b`: Abbreviated month name (e.g., "May").
- `%Y`: Year with century as a decimal number (e.g., "2015").
- `%H`: Hour (24-hour clock) as a zero-padded decimal number (e.g., "13").
- `%M`: Minute as a zero-padded decimal number (e.g., "54").
- `%S`: Second as a zero-padded decimal number (e.g., "36").
- `%z`: UTC offset in the form ±HHMM (e.g., "-0700").

The `strptime()` method converts the string into a datetime object, taking care of time zones via `%z`.

Example with multiple time zones:
```python
timestamp_1 = "Sun 10 May 2015 13:54:36 -0700"
timestamp_2 = "Sun 10 May 2015 13:54:36 -0000"

dt1 = datetime.strptime(timestamp_1, '%a %d %b %Y %H:%M:%S %z')
dt2 = datetime.strptime(timestamp_2, '%a %d %b %Y %H:%M:%S %z')

print(dt1)  # 2015-05-10 13:54:36-07:00
print(dt2)  # 2015-05-10 13:54:36+00:00
```
In this case, `dt1` is represented in UTC-7, while `dt2` is represented in UTC (±00:00). This ensures that the time zone is taken into account when performing any datetime arithmetic.

[Top](#top)

## Decorator function time_decorator which has to calculate decorated function execution time
```python
def time_decorator(func):
    """
    Decorator that measures execution time of a function and stores it
    in the execution_time dictionary with the function name as the key.
    """
    @wraps(func)
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        execution_time[func.__name__] = end - start
        return result
    return wrapper

@time_decorator
def func_add(a, b):
    sleep(0.2)
    return a + b

print(func_add(10, 20))  # Output: 30
print(execution_time['func_add'])  # Output: ~0.2 (exact time may vary)
```

[Top](#top)

## Descriptor which don't allow to set price
```python
class PriceControl:

    def __get__(self, instance, owner):
        if instance is None:
            return self

        return instance._price

    def __set__(self, instance, value):
        if not isinstance(value, (int, float)):
            raise TypeError("Price must be a number")

        if not 0 <= value <= 100:
            raise ValueError("Price must be between 0 and 100.")

        instance._price = value
```

[Top](#top)

## Descriptor which don't allow to change field value after initialization
```python
class NameControl:

    def __init__(self, field_name):
        self.field_name = field_name
        self.private_name = f"_{field_name}"

    def __get__(self, instance, owner):
        if instance is None:
            return self

        return getattr(instance, self.private_name)

    def __set__(self, instance, value):

        if hasattr(instance, self.private_name):
            raise ValueError(f"{self.field_name.capitalize()} can not be changed.")

        setattr(instance, self.private_name, value)
```

[Top](#top)
