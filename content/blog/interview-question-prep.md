
>--
title: "Interview Question Prep"
date: 2023-01-07T05:34:35Z
tags: ["learning", "meta"]
draft: True

>--

## General


> what programming languages do you prefer to work with and why?

python, bc it's powerful, easy to prototype with, easy to write quick scripts with, and have robust libraries for working with data
since it's a popular language, it makes it easy to collaborate with other programmers

> sofware development methodologies?

agile, waterfall

> ci/cd?

ci: devops practice where developers regularly merge code changes to central repository, after which builds and tests are run
cd: deployment after ci
helps automate things that would have to be done manually
detects problems early
higher code quality

> duck typing

Duck typing is a concept related to dynamic typing, where the type or the class of an object is less important than the methods it defines. When you use duck typing, you do not check types at all. Instead, you check for the presence of a given method or attribute.
runtime duck typing with hasattr() vs runtime goose typing with isinstance() vs static type checking with external tools

> software development life cycle?

> concurrency vs parallel

> multithreading vs multiprocess

## Design and Development


> what are GOF design patterns?

> what is domain driven design?

> what is test driven development?

> what is CQRS?

> what is event sourcing?

## Architecture


> what is a monolithic app?

> what are microservices?

> what is SOA?

> what does serverless actually mean?

> what is a service mesh?

> what are twelve factor apps?

## OOP


> what is object oriented programming

> what are the differences between OOP and functional programming?

> what is a class?

> what is an object?

> what is a constructor?

> what is an attribute?

> what is a class method?

> what is a static method?

> what is multi-inheritence?

> what is self?

> what problems can arise from multi-inheritence?

## Python

> Can you explain the difference between a tuple and a list in Python?

- both are used to store a collection/series of items
- in both, elements are accessed via index with `a[i]`
- both support slicing
- a tuple is immutable (meaning its elements cannot be modified) while a list is mutable
- tuple may use slightly less memory since it does not need to reserve for potential changes
- tuple usually used for related data like name, age or lat, lon, while lists usually store collections / lists of items

> How do you define a function in Python?

`def function_name(param: type = default_val) -> return_type:`

> Can you explain the difference between a local and a global variable in Python?

- a variable can be local or global depending on where it is defined and how it is used
- a global var is defined outside of any function or class and can be accessed from anywhere within
- a local var is defined within a function or class or block and can only be accessed from within
- to modify a global var from within a function, it must be declared from within the func with `global x`

> How do you check if a particular element is present in a list or not?

use the `in` keyword, like `if 4 in nums:`

> Can you explain how you would use a "while" loop in Python?

use a while loop to iterate until a condition is met. for example, `while stack: stack.pop()`

> How do you use the "zip" function in Python?

`zip` function combines elements from two or more iterables into an iterable of tuples

```python
a = [1, 2, 3]
b = [4, 5, 6]
list(zip(a, b))  # [(1, 4), (2, 5), (3, 6)]
```

> How do you use the "map" function in Python?

`map(function, iterable)` is used to apply a given function to each element of an iterable

```python
numbers = [1, 2, 3, 4, 5]
squared_numbers = map(lambda x: x**2, numbers)
squared_numbers = map(pow, numbers, [2]*len(numbers))
```

> How would you use a "list comprehension" in Python?

used when i want to write a quick iteration
```python
jnames = [name for name in names if name.startswith('j')]
```

> Can you explain the difference between the "append" and "extend" methods in a Python list?

- append adds one element to the end of the list
- extend adds the element of another list or iterator to the end of the list


> How do you create a class in Python?

```python
class ClassName(BaseClass):
    def __init__(self, param):
        self.something = param
```

> What is the difference between a shallow copy and a deep copy in Python?

- when you create a copy of a list or a dictionary, you can create either a shallow copy or a deep copy
- a shallow copy copies references to the nested objects
- a deep copy copies the nested objects
- in the case of a list of lists, a deep copy will create new copies of the inner lists, rather than just copying the references
- if the nested lists of original are modified, changes are reflected in shallow copies, but not in deep copies

```python
original_list = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
shallow_copy = original_list.copy()

print(shallow_copy) # [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
print(original_list == shallow_copy) # True
print(original_list is shallow_copy) # False

import copy
original_list = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
deep_copy = copy.deepcopy(original_list)

print(deep_copy) # [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
print(original_list == deep_copy) # True
print(original_list is deep_copy) # False

```

> How do you check the type of a variable in Python?

use the built-in `type()` function

it is also possible to do type narrowing with functions like `isinstance()`

> How do you handle missing values in a Python dataframe?

1. **Drop missing values**: One way to handle missing values is to simply drop them from the dataframe using the dropna() method. This method removes any row or column that contains at least one missing value. You can specify whether to drop rows or columns that contain missing values by setting the axis parameter to 0 for rows or 1 for columns.

```python
df = pd.DataFrame({'A': [1, 2, 3, 4], 'B': [5, 6, None, 8]})
df = df.dropna()
```

2. **Fill missing values**: Another way to handle missing values is to fill them with a specific value using the fillna() method. You can specify the value to fill missing values with, such as a constant value, the mean or median of the column, or the value of the previous or next non-null value.

```python
df = pd.DataFrame({'A': [1, 2, 3, 4], 'B': [5, 6, None, 8]})
df = df.fillna(0)
# or 
df = df.fillna(df.mean())
```

3. **Interpolate missing values**: You can also use interpolation to estimate the missing values based on the values of other rows. The interpolate() method uses different interpolation methods, such as linear interpolation, polynomial interpolation, and spline interpolation.

```python
df = pd.DataFrame({'A': [1, 2, 3, 4], 'B': [5, 6, None, 8]})
df = df.interpolate()
```

4. **Replace missing values**: You can also use the replace() method to replace a specific value with another value. This can be useful if you want to replace missing values with a specific value, or if you want to replace a specific value with a missing value.

```python
df = pd.DataFrame({'A': [1, 2, 3, 4], 'B': [5, 6, None, 8]})
df = df.replace(None, 0)
```

5. **Perform operations on non-missing values**: You can also use the notna() method to select only non-missing values and perform operations on them.

```python
df = pd.DataFrame({'A': [1, 2, 3, 4], 'B': [5, 6, None, 8]})
print(df['B'].sum()) # will return a nan
print(df['B'].notna().sum()) # will return the number of non-missing values
```

> How do you perform string formatting in Python?

- there are a few different string formatting options
- use string methods like `.upper()`
- slicing, concatenation
- use `.format()`
- use f-strings

> How do you use the with statement in Python?

The with statement in Python is used to create a context in which a certain block of code is executed. The main advantage of using the with statement is that it automatically takes care of *acquiring and releasing resources*, such as *file handles* or *network connections*, without the need for try-except-finally blocks.

```python
with expression [as variable]:
    code block
```

Where expression is an object that has an `__enter__()` method and an `__exit__()` method, and variable is an optional variable that will hold the result of the `__enter__()` method.

```python
with open('file.txt', 'r') as f:
    data = f.read()
    # do something with data
    print(data)
# file is automatically closed here, even if an exception was raised
```

The with statement is particularly useful when working with resources that need to be acquired and released in a specific order, such as file handles, network connections, and database transactions, as it ensures that the resources are acquired and released in the correct order, even if an exception occurs.


> How do you use the os module in Python to interact with the file system?

```python
# get current working directory
os.getcwd()
# change current working directory
os.chdir('/path/to/directory')
# list contents of directory
os.listdir('/path/to/directory')
# create a directory
os.mkdir('/path/to/new/directory')
```

> How do you use the pathlib module to interact with the file system?

```python
# create a path obj
path = Path('/path/to/file')
# get cwd
path = Path.cwd()
# list contents of dir
for file in path.iterdir():
    print(file)
# create dir
path = Path('/path/to/new/directory')
```


> Can you explain the difference between a generator and a list in Python?

- **Memory usage**: A generator is a memory-efficient way to iterate over a large collection of items, because it only generates the next item in the collection when it is requested, and does not store all items in memory at once. In contrast, a list stores all items in memory at once, which can consume a large amount of memory for large collections.

- **Creation**: Lists are created by placing a comma-separated sequence of items within square brackets [], while generator can be created by using generator expressions or writing a generator function using yield statement.

```python
# list
my_list = [x*x for x in range(10)]

# generator
my_gen = (x*x for x in range(10))
```

- **Accessing elements**: Lists can be accessed by index, just like arrays, but generators can only be iterated over once, meaning that you cannot access any specific element in a generator. Once you have iterated over a generator, you cannot go back and access previous elements.

- **Performance**: When working with large collections of items, generators can be faster and more memory-efficient than lists, because they only generate the items that are needed, rather than storing all items in memory at once.

- **Modification**: Lists are mutable, which means you can add, remove or change elements after the list is created. Generators, on the other hand, are not mutable, you can't change the values of generator after it's been created.

> How would you implement a stack data structure using Python?

A stack is LIFO. A Python list works well as a stack where the last element in the list represents the top of the stack. 

```python
class Stack:
    def __init__(self):
        self.items = []
        
    def push(self, item):
        """Add an item to the top of the stack."""
        self.items.append(item)
        
    def pop(self):
        """Remove and return the top item of the stack."""
        if self.is_empty():
            return None
        return self.items.pop()
    
    def peek(self):
        """Return the top item of the stack without removing it."""
        if self.is_empty():
            return None
        return self.items[-1]
    
    def is_empty(self):
        """Return True if the stack is empty, False otherwise."""
        return len(self.items) == 0
```

- O(n) for push, pop, and peek

> How would you implement a queue data structure using Python?

A queue is FIFO. A Python list also works where first element is the front of the queue and last element is the end of the queue. 

```python
class Queue:
    def __init__(self):
        self.items = []
        
    def enqueue(self, item):
        """Add an item to the rear of the queue."""
        self.items.append(item)
        
    def dequeue(self):
        """Remove and return the front item of the queue."""
        if self.is_empty():
            return None
        return self.items.pop(0)
    
    def peek(self):
        """Return the front item of the queue without removing it."""
        if self.is_empty():
            return None
        return self.items[0]
    
    def is_empty(self):
        """Return True if the queue is empty, False otherwise."""
        return len(self.items) == 0
```

- O(1) for enqueue
- O(n) for dequeue and peek

Alternatively, you can use the `collections.deque` class which is a double-ended queue, it provides a `append()` and `popleft()` method that can be used to implement queue operations in O(1) time complexity for both enqueue and dequeue operation.


> How do you handle exceptions in Python?

In Python, exceptions are raised when something unexpected or exceptional happens in the code, such as a division by zero, a missing file, or an illegal operation. To handle exceptions, you can use the `try`-`except` statement, which allows you to catch and handle exceptions that might occur in a specific block of code.

```Python
try:
    x = 1/2
except ZeroDivisionError:
    print("division by zero, please check the denominator")
else:
    print("computation successful")
finally:
    print("cleanup code")
```

It's also possible to raise an exception explicitly using the `raise` statement. This can be useful when you want to signal that an error has occurred, and you can also include a message describing the error.

It's a good practice to *catch only the specific exception you expect*, rather than catching the general exception.

Also, it's important to handle exceptions, to *prevent the program from crashing* and *providing the user with a meaningful message to understand what went wrong*.

> How do you use the itertools module in Python?

- The itertools module provides functions to work with iterators in a more efficient way. 
- use `chain` to combine elements
- use `filterfalse` to filter elements
- use `repeat` to repeat
- use `groupby` to group elements by a key
- use `permutations` and `combinations`

> How do you use the functools module in Python?

- decorate functions with `wraps`; a powerful way to add functionality, such as logging, caching, and memoization, to existing functions

```python
from functools import wraps

def my_decorator(f):
    @wraps(f)
    def wrapper(*args, **kwds):
        print("Calling decorated function")
        return f(*args, **kwds)
    return wrapper

@my_decorator
def example():
    print("Called example function")
```

- cache function results with `lru_cache`; it doesn't have to recalculate them each time it is called; useful when a function has a significant performance cost, but its inputs are deterministic

```python
from functools import lru_cache

@lru_cache(maxsize=None)
def expensive_function(n):
    return n**2

print(expensive_function(4))
print(expensive_function(4))
```

- partially apply function with `partial`; useful when you want to create a new function with specific arguments, without having to define a new function.

```python
from functools import partial

def add(a, b):
    return a + b

add_five = partial(add, 5)
print(add_five(3))
```

> How do you use the operator module in Python?

- provides a set of functions that work with basic operators such as addition, subtraction, and comparison
- add, sub, mul, floordiv
- lt, le, eq, ne, ge, gt

> How do you sort a list of dictionaries by a particular key in Python?

```python
data = [
    {"name": "Alice", "age": 30},
    {"name": "Bob", "age": 25},
    {"name": "Charlie", "age": 35},
]
sorted_data = sorted(data, key=itemgetter("age"))
```

> What is PEP8 and why is it important?

PEP8 is a style guide for writing python code. It defines a set of guidelines for formatting code so that it is readable, consistent, and maintainable. It covers things like indentation, naming conventions, and organization of code. It is important since it promotes consistency across the Python codebase. This makes it easy for developers to read and understand code written by others, making collaboration, code reviews, and maintenance of the codebase much more efficient. 

> what is a PEP?

A PEP stands for Python Enhancement Proposal. It is a *document that describes a new feature or improvement for the Python language*. PEPs are created by members of the Python community and are reviewed and discussed by the Python community before being accepted and implemented.

- PEP 8, which is the style guide for Python code
- PEP 20, also known as "The Zen of Python", which provides guiding principles for writing good Python code
- PEP 257, which describes the conventions for docstrings in Python
- PEP 3107, which added support for function annotations
- PEP 3134, which introduced the "raise ... from" statement to improve exception handling

> multiprocessing, multithreading?

> What is a class in Python? How is it different from an object?
> What is inheritance in Python? How is it used?
> What is polymorphism in Python? How is it implemented?
> What is encapsulation in Python? How do you achieve encapsulation in a Python class?
> What is the difference between a class variable and an instance variable in Python?
> How do you create a class in Python? How do you create an object of a class?
> How do you define a constructor in Python? What is the purpose of a constructor?
> How do you define and override class and static methods in Python?
> How do you use the "super" function in a Python class? What is its purpose?
> How do you implement abstract classes and methods in Python? How do you use the "ABC" and "abstractmethod" classes?
> How do you use the "isinstance" and "issubclass" functions in Python? What are their purposes?
> How do you handle exceptions in an object-oriented Python program?

## HTTP

> what is http?

> what are http methods?

> http status codes?

> components of http requests and responses

> is it possible to send a payload in get or delete methods?

> what is the max payload size for post?

## Databases

> what is a database?

> what are some popular relational databases?

- MySQL
- PostgreSQL
- SQLite
- MS SQL

> what kind of nosql databases exist?

- document: MongoDB
- time series: InfluxDB
- realtime: Firebase
- column: Cassandra
- key-value: Redis
- graph: Neo4j

> nosql vs relational?

relational
- structured, tables and columns
- consistency, data fits models, easy to understand what is in the db
- relations between objects in multiple tables
- security, ensure field constraints, apply encryption or uniqueness to columns
- ease of backup and recovery
- storage is concentrated
- scale vertically, better machine (horizontal can only have read replicas, not write)
- more traditional workloads
- accessed through raw queries or ORMs with direct db connections
- used when:
    - access patterns aren't defined
    - perform flexible queries
    - perform relational queries
    - enforce field constraints
    - you want to use well documented access language SQL

nosql
- key-value, each key maps to one value, simple
- column store, data organized into columns, optimized for performance
- graph, shows network rep of obj in db
- document store, group of documents is collection
- structure more flexible, queries are less flexible
- need to know the key when performing query
- high scalability, add more partitions
- access through rest apis or crud in vendor specific languages
- cost effective
- use when:
    - access pattern is defined
    - primary key is known
    - data model fits (graphs)
    - high performance, low latency

> what are ORMs?

- object relational mappers
- lets you query and manipulate data in db using object-oriented paradigm
- sqlalchemy orm
- tortoise orm

> what is ACID?

> what are transactions?

> what is the N+1 problem?

> what is normalization?

> what are failure modes?

> how do you profile performance?

> what are database indexes?

> data replication?

> sharding strategies?

> CAP theorem?

> what are database migrations?

## APIs

> what is an api and why do we use it?

> what is a rest api?

> what is a soap api?

> what is a restful web service? what are its features?

> what are disadvantages of restful web service?

> what are restful payloads?

> what markup language is used in restful api?

> what is xml? json? diff?

> what is resource in rest? what is a way to represent it?

> what is adv of using rest apis?

> what is statelessness in rest?

> what is URI?

> what is CORS?

> what is postman? why do we use it?

> what is gRPC?

> what is GraphQL?

> what are OpenAPI specs?

> what is HATEOAS?

## Caching


> what is caching?

> what is client-side caching?

> what is server-side caching?

> what is Redis?

> what is Memcached?

> what is a CDN?

## Search


> elasticsearch

## Message Broker


> what is a message broker?

> RabbitMQ

> kafka

## Auth

> what is authentication?

> what is authorization?

> what is a cookie?

> what is OAuth?

> what is HTTP Basic Authentication?

> What is a token?

> what is a JWT?

> what is OpenID?

> what is SAML

## Security


> what is a hash?

> why should you salt your hashed passwords?

> what is TLS?

> what is HTTPS?

> OWASP top 10

> what is CORS?

> what is CSRF? how can we avoid it?

> what is CSP?

> server security?
firewalls
don't expose ports
keep updated
NIPS
HIDS
use encryption for network communication

> what are certificates?

## Containers


> what is a container?

> what are the benefits of containerization?

> what the difference between containerization and virtualization?

> docker

> kubernetes

## WebSockets


> what are websockets?

> what types of applications are they used for?

## Servers


> nginx

## Scale


> horizontal vs vertical scaling

> graceful degredation

> throttling

> backpressure

> loadshifting

> circuit breaker
