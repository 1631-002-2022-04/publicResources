# Strings and Lists
---

## Introduction:  Data Types - More Than Meets The Eye

Up to know we've been discussing Python's built-in 'primitive' data types: 
> `int`, `float`, `bool`, & `str`.

We've used these data types to implicitly or explicitly assign values to variables and to perform some basic operations.
> although `+` and `*` are *overloaded* since:
> - `+` can mean both **add** numbers and **concatenate** strings, 
> - `*` can mean both **multiply** numbers and **repeat** strings.

However, all of these data types are really **Classes**:
> a Class is a programmer defined template for something that has:
> - attributes: characteristics
> - methods: functions that that object can do

As an analogy let's compare *Elephants* with *Strings*
| Class: | Elephant | String|
| ---------- | ---------- | ---------- |
| Attributes: | Sex | Case |
| | mass | length of string |
| Methods: | Drinking with trunk | Convert from upper to lower |
| | Trumpeting | Count sub-strings |


We will investigate **Classes** in much more detail a bit later in the course but for now 

***recognize that every example (instance) of a class can have its own particular attributes, but all instances of the class 'know' the same methods.***

And, although we've assumed that all the data types we've seen up to now are just values,

***each example of a data type is really an instance of its class, as so it will have attributes and methods.***

---

## The String Class

Every time you've defined a string, either implicitly or explicitly:
``` py
a_string = "this that"
b_string = str(98.23)
```

you have created an *instance* of the String class so it 'knows':
- it's contents have an order (index)
  - and then can be *sliced* 
- it works with common Python operators and functions in ways specific to its class
- it has String methods that it 'knows' as soon as the program defines it as a string

---
### String Indexing

All strings number (index) the symbols they contain.
In Python the characters can be indexed *positively* or *negatively*.

The syntax is:
> `any_string[index]`
> where
> - the indices count 
>    - from left to right starting at ***0***
>    - from right to left starting at ***-1***
> - the indices must be integers
> and
> - the positive index cannot be bigger than the ***(length of the string - 1)***
> - the negative index cannot be smaller than the ***length of the string***

For example with this string variable:

> `variable = "cheEs3"`
with 
> `how_long = len(variable) # how_long = 6`
> 
then
| Symbols: | c | h | e | E | s | 3 |
|   -      | - | - | - | - | - | - |
|Positive  | 0 | 1 | 2 | 3 | 4 | 5 |
|Negative  | -6 | -5 | -4 | -3 | -2 | -1 |

Thus:

> `print(variable[0]) # will display 'c'`

> `print(variable[-2]) # will display 's'`

and, in **this example** 

> `variable[3] == variable[5] # will be False`

and

> `new_string = variable[1] + variable[4] # assigns 'hs' to new_string`

---

#### Try it yourself

1. Create code that allows you to enter in your first and last name as one variable.
2. Display the *first* letter of your last name with a negative index and with a postive index.
3. What is the index of the space between your names? Assign that symbol to a variable.

E.g
``` py
name = input("What is your name? ") # and if the user types 'PJ Perri'
print(name[-5], name[4])
spacer_at = 2
the_space = name[2]
```

---

### String Slicing using Indices

With the following syntax, any string can be sliced up into a new string. **Note the default values and the use of colons to separate the parameters***

`new_string = any_string[start=0: stop=len(any_string):step-1]`

Thus:

``` py
name = "Rufus Xavier Sasperilla"
first_name = name[:5:]
second_name = name[6:12:]
third_name = name[13::]
# and
print(name[1:17:3] # produces usaeSp
```
***BTW: Are you noticing how start, stop, step is similar to how loops work?***
> - counting from zero `i = 0`
> - up to, but not including the stop, `while i < 10:`
> - and then incremented, `i += 1`

And how `for` loops work with range?

> `for i in range(10):`

