# Front End Masters Python Fundamentals Notes


# Table of Contents
- [Variables](#variables)
- [Data Types](#data-types)
  - [Integers](#integers)
  - [Float](#float)
  - [Strings](#strings)
  - [How to format a string using `f""`](#how-to-format-a-string-using-f"")
  - [String Errors](#string-errors)

- [Functions](#functions)
  - [Function Arguments](#function-arguments)
  - [Empty Default Lists](#empty-default-lists)
  - [Function Scope](#function-scope)

- [Lists](#lists)
  - [How to Sort a List](#how-to-sort-a-list)
  - [Add Items to List](#add-items-to-list)
  - [List Lookups](#list-lookups)
  - [Remove Items From a List](#remove-items-from-a-list)

- [Tuples](#tuples)
  - [Unpacking Tuples](#unpacking-tuples)

- [Sets](#sets)
  - [Add, Remove, Updating Sets](#add-remove-updating-sets)
  - [Combining, Comparing, Contrasting Sets](#combining-comparing-contrasting-sets)

- [Dictionaries](#dictionaries)
  - [Adding, Removing, Accessing Keys or Values](#adding-removing-accessing-keys-or-values)

  - [Looping Over Dictionaries](#looping-over-dictionaries)

- [Boolean Logic](#boolean-logic)
  - [Comparisons](#comparisons)
  - [and, or, & not](#and-or-&-not)
  - [Control Flow](#control-flow)

- [Loops and Control Statements](#loops-and-control-statements)

- [Useful Methods](#useful-methods)
-[Additional Notes](#additional-notes)


# Variables
- Variables names should be lower case, whole words, separated by an `_` underscore.

[[↑] Back to top](#table-of-contents)

# Data Types

In Python, None is null

```
>>> x = None
>>> x
>>> type(x)
<class 'NoneType'>

```

`type(my_name)` // gives you the type of a variable


Integers
--------
x = 4 
y = -3938
z = 0
x = 5.0
y = -3484.5

x = 42j //j is a complex number



In Python, integers and simple data types are objects under the hood. That means you can just create new ones by calling the methods associated with their types.

- <strong>IMPORTANT:</strong> When you divide two integers in Python, the end result is a floating number.

[[↑] Back to top](#table-of-contents)

Float
-----

x = 5.0
y = -3484.5
z = 0.0


In Python, integers and simple data types are objects under the hood. So you can just create new ones by calling the methods associated with their types.

```
<class 'int'>
<class 'float'>
```

You can type:

```
int(5)

float(3.0)
```

[[↑] Back to top](#table-of-contents)


Strings
-------
It's best practice to use double quotes in Python because if you need to put a single quote in your string, you'll prematurely close the string unless you escape it with a `\` slash.

You can concat a string with the `+` symbol, like JavaScript.

You can make a long string by typing 3 `"""` double quotations:

```
long_string = """
... a very
... very
... very very long
... string"""
>>> long_string
'\na very\nvery\nvery very long\nstring'
```

[[↑] Back to top](#table-of-contents)



How to format a string using `f""`
----------------------------------
You reference a variable with `{}` braces.

name = "James"

```
f"Hello, {name}"

'Hello James'
```

[[↑] Back to top](#table-of-contents)

String Errors
-------------

If you mismatch string quotes, you'll get a SyntaxError like so:

```
name = "James'

SyntaxError: EOL while scanning string literal
```
EOL means "End of Line."




If you try to concatenate a string and an integer, we'll get an exception:

```
>>> "Hello " + 1
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: can only concatenate str (not "int") to str
```


[[↑] Back to top](#table-of-contents)



# Functions

Always start with keyword `def`.

We always need the `()` parenthesis in Python.

Finally, we need a colon `:`.

Python doesn't use brackets `{}` to differentiate between the scope, what belongs to a function and what doesn't. Instead, Python indicates that with indentation.

```
def foo():
    print("Hello!")

```

`print()` is the Python version of `console.log()`.

Functions can accept no arguments. It can also return nothing.

```
def meaning_of_life():
    return 42
```


To add more content to the function, you have to indent. Everything that is indented one level under the function belongs to it:

```
def greeting(name):
    greeting = "Hello"

    return greeting + name

```

The `return` in a function is optional. If you don't return anything, it returns `None`.

You can use a return statement that has no value. 

[[↑] Back to top](#table-of-contents)


Function Arguments
------------------

If you forget to pass in an argument to a function, you'll get an error:

```
def add(a,b):
    return a + b

add(7)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: add() missing 1 required positional argument: 'b'

```

Python also has default values for function arguments:

Arguments with default values always come last.
```
def say_greeting(greeting, name="World"):
    print(f"{greeting}, {name}")

>>> say_greeting("Hello")
Hello, World

```

You can also pass in the arguments in any order if they're labeled:

```
def create_query(language="JavaScript", num_stars=50, sort="desc"):

create_query(language="Python", sort="50", num_stars=1)
```


In Python, to be extra explicit, you can pass in the keyword of the label and the value:

```
add(a = 5, b = 10)
```

[[↑] Back to top](#table-of-contents)

Empty Default Lists
-------------------
You never want to use mutable types like lists as your default arguments.

If you use an argument that can be changed as your default argument (like a list), because you would think these default arguments get created/instantiated everytime you call the function, but that's not true. <strong>They get created the first time the function is called, and then the value is shared</strong>.


The reason b is the same list everytime you call the function is because these default arguments <strong>get instantiated once when the function is defined</strong>. With an empty list, there is one handle on this empty list. It won't create a new empty list everytime the function is called, and there won't be a syntax error or hint. 


```
# a is a positional argument
# b is a list

def foo(a, b = []):
    b.append(a)
    print("B is: ", b)

>>> foo(4)
B is  [4]
>>> foo(5)
B is  [4, 5]
>>> foo(6)
B is  [4, 5, 6]

```


Because Python is a dynamic language, we have to be mindful of how we name things. Sometimes it's called `duck typed`.


[[↑] Back to top](#table-of-contents)

Function Scope
--------------

In Python, <strong>functions have scope</strong>. When we're inside a Python funciton, the scope changes. 

You can think of it this way:

Python scoping happens with white space. When we delineate the code block for a function, we indent it under the function deifnition. Within that block of indented code, its scope changes to a new inernal scope that just exists for the function. 

In that internal scope, the function has access to variables that are defined outside of it, but <strong>it can't actually change them</strong> (unlike JavaScript).

Like JavaScript, you can't access variables that are in the scope of a function:
```
def twitter_info():
    account = "nnja"
    print(f"account inside the function is: {account}")


>>> twitter_info()
Account inside the function is: nnja

>>> account
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'account' is not defined
```


Python shadows variables inside a function that have the same labels outside the function scope:

```
name = "Nina"

def try_change_name():
    name = "Max"
    print(f"Name inside the function is {name}")

>>> try_change_name()
'Name inside function is: Max'

```

In Production Python, you don't want change defined variables outside of their defined scope. You don't want a bunch of floating variables outside a defined scope.


Example with Control Statements
```
def foo(a, b=None):
    if b is None:
        b = []
    b.append(a)
    print(b)

```

[[↑] Back to top](#table-of-contents)


# Lists

An empty list in Python can be created with 2 square brackets `[]`.

Because everything is an object in Python, you can also call `list()` with no parameters to get an empty list.

You'll get an error if you try to access a value in a list that doesn't exist:

```
names[2]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: list index out of range

```

[[↑] Back to top](#table-of-contents)


How to Sort a List
------------------
Two ways to sort in Python:

```
lottery_numbers = [1, 4, 34242, 78, 11]

>>> sorted(lottery_numbers)
[1, 4, 11, 78, 34242]

>>> sorted(lottery_numbers, reverse=True)
[34242, 78, 11, 4, 1]


>>> lottery_numbers
[1, 4, 34242, 78, 11]

>>> lottery_numbers.sort()

>>> lottery_numbers
[1, 4, 11, 78, 34242]


```

 - sorted(list_name, reverse=True), also takes a second boolean argument to return the list sorted in reverse.
  - calling sorted returns a copy
 - list_name.sort() <strong>sorts the list in place</strong>.
  - list_name.reverse() <strong>reverses in place</strong>.

[[↑] Back to top](#table-of-contents)

Add Items to List 
-----------------

- list.append()
- list.insert(position, value) // inserts in arbitrary position
- list.extend(list) // appends values to a target list from a source list. The target list gets altered.

```

>>> names
['Max', 'Nina', 'Maximus']

>>> names.insert(3, "Julia")

>>> names
['Max', 'Nina', 'Maximus', 'Julia']


>>> lottery_numbers
[1, 4, 11, 78, 34242]

>>> names.extend(lottery_numbers)

>>> names
['Max', 'Nina', 'Maximus', 'Julia', 'Betty', 1, 4, 11, 78, 34242]

```

[[↑] Back to top](#table-of-contents)

List Lookups
------------

```
>>> names
['Max', 'Nina', 'Maximus', 'Julia', 'Betty', 'Max']

>>> "Rose" in names
False


>>> names.index("Max")
0

>>> names.count("Betty")
1

>>> names.count("Max")
2


>>> names
['Max', 'Nina', 'Maximus', 'Julia', 'Betty', 'Max']

>>> names[7] = "Alex"
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: list assignment index out of range

```

- `in` keyword asks the list if the item is included.
- list.index() gives you the first result
- list.count() gives you the number of times the item appears in the list.
- You can assign/update lists by index, but an out of bounds index assignment/update will give you an error
 - However, if you use `insert()` and you provide an out of bounds index, the item gets inserted as the last item.

[[↑] Back to top](#table-of-contents)

Remove Items From a List
------------------------

- list.remove(value) // does not remove duplicates, only the first value found
  - You'll get an error if you try removing a non-existent item
- list.pop(index) // either removes and returnsthe last item or removes the value by passing the index argument

```
>>> names
['Max', 'Nina', 'Maximus', 'Julia', 'Betty', 'Max', 'Alex']

>>> names.remove("Max")

>>> names
['Nina', 'Maximus', 'Julia', 'Betty', 'Max', 'Alex']


>>> names.remove("Sir John")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: list.remove(x): x not in list


>>> names
['Nina', 'Maximus', 'Julia', 'Betty', 'Max', 'Alex']

>>> popped_val = names.pop()

>>> popped_val
'Alex'

>>> names
['Nina', 'Maximus', 'Julia', 'Betty', 'Max']

>>> names
['Nina', 'Maximus', 'Julia', 'Betty', 'Max']

>>> names.pop(2)
'Julia'

>>> names
['Nina', 'Maximus', 'Betty', 'Max']

```

Note: Items in a list don't have to be the same type in Python.


[[↑] Back to top](#table-of-contents)



# Tuples

Tuples are immutable, once created, the items can't change.

Tuples are useful for containing a snapshot of data.

You want to represent a spreadhsheet in your code, a tuple might represent each row in the spreadsheet.

Tuples can't continually be changed, they can't be added to or removed from, the way you could with a list. This provides added security with your data.

Empty `()` creates a tuple.

```
>>> a = ()
>>> type(a)
<class 'tuple'>

```

Things get tricky when we make a tuple with one item. Tuples are not just parenthesis `()`, they're about commas "`,`". It's about the combination of optional `()` parenthesis, but the comma `,` is the important part. 

```
>>> c = (1,)
>>> type(c)
<class 'tuple'>

```


You can access value in a tuple by index.

```
>>> a = (1, 2, 3, 4)
>>> type(a)
<class 'tuple'>
>>> a[2]
3
```

Changing the value in a tuple gives you an error.



```
>>> student = ("Marcy", 8, "History", 3.5)

>>> student[0] = "Alex"
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment


```


Tuples are great when you depend on your data staying unchanged. You can then use tuples in other types of containers where the container needs a key that is immutable. A dictionary key needs to be immutable. You can use a tuple as long as the tuple contains all immutable data.

[[↑] Back to top](#table-of-contents)

Unpacking Tuples
----------------

Tuples are a great way of consolidating information because of tuple unpacking.

We can unpack it by declaring variable names on the left side of the expression, and matching them up with the number of items in the tuple, and separating them with a comma.

```

>>> student = ("Marcy", 8, "History", 3.5)

>>> name, age, subject, gpa = student
>>> name
'Marcy'
>>> age
8
>>> subject
'History'
>>> gpa
3.5
>>>
```


Generally we want the number of variables we declare to match up to the number of items in the tuple. If you don't, you'll see an error. You can use an `_` underscore to tell signify, "Throw away the value, I don't care about it."

```
>>> foo, bar, baz = student
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: too many values to unpack (expected 3)
>>> foo, bar, baz, _ = student
>>> foo
'Marcy'
>>> bar
8
>>> baz
'History'
>>> _
3.5
>>>

```

*`()` parenthesis signify the tuple, that's not entirely true. It's really the `,` comma:

```
>>> x = 1, 2, 3
>>> type(x)
<class 'tuple'>

```


You can return tuples from functions and use unpacking.

```
>>> def http_status_code():
...     return 200, "OK"
...
>>> http_status_code()
(200, 'OK')
>>> status_code, status_message = http_status_code()
>>> status_code
200
>>> status_message
'OK'
>>>

```

[[↑] Back to top](#table-of-contents)

# Sets

Sets are a data type that allow you to store other immutable types in an unsorted way.

An item can only be stored in a set once, no dupes.

A set has no order, you can't access values by position.

*Note: `{}` curly braces are used by both `sets` and `dictionaries`.

```
>>> type({})
<class 'dict'>
```

If you want to make an empty set, you have to be explicit:

```
>>> set()
set()

>>> type({1})
<class 'set'>

```

Duplicates are ignored in Python
```
>>> names = {"Nina", "Max", "Nina"}
>>> type(names)
<class 'set'>
>>> names
{'Max', 'Nina'}

```

We can check the length of the set

```
>>> len(names)
2

```
<strong>IMPORTANT</strong>: Sets CAN'T contain mutable data types.

The way sets allow you to quickly check that an item is contained is with a hashing algorithm. There's a built-in hashing function in Python, you're not going to call it manually, but we can call it to see what the hash of an item will be:

```

>>> hash("Max")
-1915283605762764312
>>> names
{'Max', 'Nina'}
>>> hash(names)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unhashable type: 'set'

```


You can use a set to de-duplicate a list.

```
>>> names = ["Nina", "Max", "Rose", "Max", "Nina"]
>>> unique_names = set(names)
>>> unique_names
{'Max', 'Nina', 'Rose'}

```

Sets don't have order, so the values inside the set won't be printed out by the order of insertion.

If you try to access a set by index, you'll get an error.

```

>>> names = ["Nina", "Max", "Rose", "Max", "Nina"]
>>> unique_names = set(names)
>>> unique_names
{'Max', 'Nina', 'Rose'}
>>> unique_names[1]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'set' object does not support indexing


```


[[↑] Back to top](#table-of-contents)


# Add, Remove, Updating Sets

Use `add` to add to set:
```

>>> colors = {"Red", "Green", "Pink"}
>>> type(colors)
<class 'set'>
>>> colors.add("Blue")
>>> colors
{'Red', 'Blue', 'Green', 'Pink'}


```

Remove items with `discard`:

```
>>> colors.discard("Green")
>>> colors
{'Red', 'Blue', 'Pink'}

```


You can also use `remove`. 

```
>>> colors.remove("Blue")
>>> colors
{'Red', 'Pink'}

```



But the nice thing about using `discard` is that if you try to discard a non-existing value, you WONT'T get an error.

```

>>> colors
{'Red', 'Blue', 'Pink'}
>>> colors.discard("Yellow")
>>> colors
{'Red', 'Blue', 'Pink'}



>>> colors.remove("Aqua Marine")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'Aqua Marine'



```


To update a set, you can combine sets by using `update`:

```

>>> colors
{'Red', 'Pink'}
>>> nums = {1, 2, 3, 4}
>>> nums
{1, 2, 3, 4}
>>> type(nums)
<class 'set'>
>>> colors.update(nums)
>>> colors
{1, 2, 3, 4, 'Pink', 'Red'}
>>> nums
{1, 2, 3, 4}

```


One caveat with `update` is that it expects a sequence. If you pass in one value, you'll get a surprising result:

```

>>> colors.update("John")
>>> colors
{1, 2, 3, 4, 'n', 'Pink', 'Red', 'J', 'o', 'h'}

```

[[↑] Back to top](#table-of-contents)




# Combining, Comparing, Contrasting Sets

union() - creates a new set with all the items <strong>from both `s` and `t`</strong>

```
s.union(t)

s | t # same as above
```

intersection() - creates a new set containing only items that are <strong>both in `s` and `t`</strong>

```
s.intersection(t)

s & t # same as above

```


difference() - creates a new set with items <strong>in `s` but not in `t`</strong>

```
s.difference(t)

s ^ t # same as above

```


How to find out if value is in a set? => Use `in` keyword.

```
>>> colors
{'Red', 'Orange', 'Blue', 'Pink'}
>>> "Red" in colors
True
>>> "Yellow" in colors
False
>>>

```

[[↑] Back to top](#table-of-contents)


# Dictionaries

Dictionaries are a useful type that allow us to store our data in key, value pairs. Dictionaries themselves are mutable, but, dictionary keys can only be immutable types.

How to create a dictionary:

```
>>> {}
{}
>>> type({})
<class 'dict'>
>>> dict()
{}

```

A one item dictionary:

```
>>> {1: "one"}
{1: 'one'}

```

You can have mutable type as the value in a dictionary. But only immutable types can be used as dictionary keys.

```
>>> {1: []}
{1: []}

```
Trying to access a non-existant key in a dictionary results in an error:
```
>>> nums_dict[10]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 10

```


Use `get()` to access a dictionary key and get no-error if key doesn't exist:
```
>>> nums_dict.get(10)

```


You can also provide an optional 2nd argument to `get()` which shows the default value if the key is not found:

```
>>> nums_dict.get(10, "Couldn't find num")
"Couldn't find num"

```


[[↑] Back to top](#table-of-contents)


# Adding, Removing, Accessing Keys or Values

Assignment
```
>>> nums_dict
{0: 'zero', 1: 'one', 2: 'twooooooooooo', 3: 'three'}

```


Accessing Keys with `in` keyword:

```

>>> "foo" in nums_dict
False
>>> 1 in nums_dict
True

```


Overwriting
```
>>> nums_dict
{0: 'zero', 1: 'one', 2: 'two'}
>>> nums_dict[2] = "twooooooooooo"
>>> nums_dict
{0: 'zero', 1: 'one', 2: 'twooooooooooo'}


```


Combine two dictionaries:

```
# YOU MUST put string keys in quotes ""
>>> colors = {r: "red", g: "green", y: "yellow"}
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'r' is not defined



>>> colors
{'r': 'red', 'g': 'green', 'y': 'yellow'}
>>> nums_dict.update(colors)
>>> nums_dict
{0: 'zero', 1: 'one', 2: 'twooooooooooo', 3: 'three', 'r': 'red', 'g': 'green', 'y': 'yellow'}


```


You can store lists as a value in a dictionary key:

```

>>> veggies = {"green": ["Spinach"]}
>>> veggies["green"]
['Spinach']

```

You can add to list in dictionary:

```
>>> veggies["green"].append("Lettuce")
>>> veggies["green"]
['Spinach', 'Lettuce']


```

<strong>3 important methods</strong> to remmember when using dictionaries:
  - `.keys()`gives you all the keys in the dictionary
  - `.values()` gives you all the values in the dictionary
  - `.entries()` gives you a list of tuples `(key, value)`


```
>>> veggies.items()
dict_items([('green', ['Spinach', 'Lettuce'])])

>>> veggies.keys()
dict_keys(['green'])

>>> veggies.values()
dict_values([['Spinach', 'Lettuce']])

```



[[↑] Back to top](#table-of-contents)


# Boolean Logic

In Python, truthiness for a particular type, is the value represented as `true` or `false` under the hood?


There's a built-in `True` and `False`

```
>>> True
True

>>> False
False

```

The shorthand for figuring out the truthiness of a value is with `bool()`:

```
>>> bool(0) # 0 is falsy
False


>>> bool(-1) # negative nums are truthy
True


>>> bool([]) # empty lists are falsy
False

>>> bool({}) # empty dictionary
False


>>> bool(()) # empty tuple
False


>>> bool('') # empty string
False
```


[[↑] Back to top](#table-of-contents)


# Comparisons

```
<

>

<=

>=

```


In Python, strings are compared lexicographically (by underlying ascii value). Capital letters come before lower-case letters.


Equality: do these two values have the same values within them?

In Python, `is` keyword means identity. It asks, are these the same objects in memory? The opposite of `is` => `is not`.

```
>>> 3 == 3
True

>>> "hello" == "Hello"
False

>>> "hello" == "hello"
True

>>> [1, 2, 3] == [1, 2, 3]
True


>>> a = [1, 2, 3]
>>> b = [1, 2, 3]
>>> c = [4, 5, 6]

>>> a != b
False

>>> a != c
True

```


[[↑] Back to top](#table-of-contents)

# and, or, & not

When comparing truthy values, using `and`, we return the value on the right side of the `and` keyword:

```
>>> a = [1]
>>> b = [2]
>>> a and b
[2]

```

If either value is falsy, we get back the first falsy value:

```

>>> False and True
False

>>> a = []
>>> b = [1]

>>> a and b
[]

>>> a = [1]
>>> b = []

>>> a and b
[]


```

If one of the items is truthy, we get back a truthy value:

```

>>> a = True
>>> b = False

>>> a or b
True

>>> [1] or [2]
[1]

>>> [] or [1]
[1]

```

`not` returns the inversion

```
>>> not False
True

>>> not True
False

```

[[↑] Back to top](#table-of-contents)




# Loops and Control Statements

<strong>IMPORTANT</strong>: 
  - the `for in` loop is not a function, so there's no scope. So the variable `color` will exist in your scope as the last color it was set to.

  - Just like functions, indentation defines what belongs to the for loop.

```
colors = ["Red", "Green", "Blue", "Orange"]

>>> for color in colors:
...     print(f"the current color is {color}")
...
the current color is Red
the current color is Green
the current color is Blue
the current color is Orange

```


If you want to go through a sequence of numbers, you can use `range()`

```

# range() is exclusive

>>> list(range(5))
[0, 1, 2, 3, 4]

>>> for num in range(5):
...     print(f"The current num is {num}")
...
The current num is 0
The current num is 1
The current num is 2
The current num is 3
The current num is 4

```


The first arg to `range()` is where to start, the second is where to end. The second argument is exclusive:

```

>>> list(range(1, 5))
[1, 2, 3, 4]


```


You can also pass a third argument to `range()`.

```
>>> for num in range(1, 11, 2):
...     print(f"the current num is {num}")
...
the current num is 1
the current num is 3
the current num is 5
the current num is 7
the current num is 9

```




[[↑] Back to top](#table-of-contents)


# Looping Over Dictionaries

Looping over dictionaries only gives you the key:
```
>>> hex_colors = {"Red": "#FF", "Green": "#008"}
>>> for key in hex_colors:
...     print(f"the current key is {key}")
...
the current key is Red
the current key is Green

```

Use the key in the for loop to access the dictionary value:

```
>>> for key in hex_colors:
...     print(f"the current color is {hex_colors[key]}")
...
the current color is #FF
the current color is #008

```


To loop over the keys and values in the dictionary at once, use the `.items()` to get the list of tuples, and then unpack them:

```
>>> hex_colors.items()

dict_items([('Red', '#FF'), ('Green', '#008')])

>>> for color, hex_code in hex_colors.items():
...     print(f"the color {color} has a hex code of {hex_code}")
...
the color Red has a hex code of #FF
the color Green has a hex code of #008


```


`enumerate()`: passing a list argument gives you a list of tuples

```
>>> colors_list
['Red', 'Green', 'Blue']

>>> for i, color in enumerate(colors_list):
...     print(f"the index is {i} and the color is {color}")
...
the index is 0 and the color is Red
the index is 1 and the color is Green
the index is 2 and the color is Blue

```


[[↑] Back to top](#table-of-contents)


# Control Flow


[[↑] Back to top](#table-of-contents)

# Useful Methods
- print()
- type() // tells you the type of something
- list()
  - append() //adds to list `[]`
- len() //built-in method in Python for multiple types

- str.lower() // lowercases string
- sorted(my_list)
- dir(list) //dirctory listing of all the methods available to the argument you pass in
- help(type) // gives you the helper methods for the type argument you pass in


[[↑] Back to top](#table-of-contents)


# Additional Notes

You use the pound `#` sign to make a comment in Python.

You use `"""` 3 quotations to make a multi-line comment:

```
"""
This is a Python
Multiline comment.
"""

```

[[↑] Back to top](#table-of-contents)