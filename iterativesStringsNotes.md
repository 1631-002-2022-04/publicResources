# Iterative Data Types: Part 1 - Strings
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

***recognize that every example (instance) of a class can have its own particular attributes, but all instances of the class 'inherits' the same methods.***

And, although we've assumed that all the data types we've seen up to now are just values,

***with the string data type*** (and soon you will learn about `lists`)

***every string is really an instance of its String class, meaning it will have attributes and 'String' methods.***

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

where

> - the indices count 
>    - from left to right starting at ***0***
>    - from right to left starting at ***-1***
> - the indices must be integers

and

> - the positive index cannot be bigger than the ***(length of the string - 1)***
> - the negative index cannot be smaller than the ***length of the string***

For example with this string variable:

> `variable = "cheEs3"`

with 

> `how_long = len(variable) # how_long = 6`

then each of its characters can be located with an index:


|  | c | h | e | E | s | 3 |
|-| - | - | - | - | - | - |
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
1. Display the *first* letter of your last name with a negative index and with a postive index.
1. What is the index of the space between your names? Assign that symbol to a variable.

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

---

#### Try it yourself

1. Create code that allows you to enter the full title of your favourite [*Star Wars* movie](https://en.wikipedia.org/wiki/List_of_Star_Wars_films).
2. Use slicing to create new variables for the first word, last word and one of the middle words.

E.g.
``` py
name = "Rogue One: A Star Wars Story"
first_word = name[:5]
middle_word = name[13:17]
last_word = name[-5:]
```

---

### Strings and Common Built-in Functions

Because strings are classes, their attributes can be discovered by Python's built in functions.

Evaluted using each character's [ASCII value](https://www.asciitable.com/)

> `= max()`
> `= min()`

Works like this:

``` py
biggest = max("a to z A to Z")    # will return 'z'
smallest = min("PJ Perri")        # will return ' ' (the space)
if "AAB" < "AAA":
    print("'AAB' is smaller than 'AAA'")
else:
    print("'AAB' is larger than 'AAA'")   # this is what is displayed
```

***Notice how space is encoded as a 32, so it will be smaller than number symbols, which, in turn, are encoded with a smaller ASCII number than upper-case letter symbols, leaving upper-case letter symbols as biggest characters.***

This built-in function is especially useful when one needs to iterate over string (aka look at each character one at a time).

> `= len()`

```py
cheese = "Rogue One: A Star Wars Story"
i=0
while i < len (cheese):
    print(cheese[i])
    i +=1
####
toast = input("Type in your address ")
for index in (range(  len(toast)   )):
    # stuff done at each letter's index...no matter how long the input was
```

### Strings and their own Methods

The String class has a [long list of methods](https://docs.python.org/3/library/stdtypes.html#string-methods) that all strings inherit the moment they are defined.

For example, try the following:

```py
aString = "This"
bString = "that"
cString = "To be or not to be. That is the question."

print(aString.upper())
print(bString.lower())
words_list = cString.split(" ")
print(words_list)
```

####String Class Methods to Know. (UNDERCONSTRUCTION and may be dropped)

Appreciate, the methods listed below are available to any named string variable.

#### String Value Returning Methods

Here are a few string methods that return values that are worth knowing about:

`= any_string.count(subString)`
> counts the number of the subString in the original string

Notice how the following 2 versions are equivalent
```py
movie_title = "The Good, the Bad, and the Ugly"
subString = "the"

# version 1
x = movie_title(subString)

# version 2
tally = 0
i = 0
while i < len(movie_title):
    if movie_title[i:3] == subString:
        tally += 1
    
    i += 1
 ```
 #### Try some yourself
 
 For each of the following string methods, look up what they do and see if you can code your own function that uses string indexing, string slicing and looping through a string, to produce the same result.
 1. `= any_string.startswith(subString)` or `= any_string.endswith(subString)` where your function returns a Boolean
 2. `= any_string.removeprefix(prefix)` or `= any_string.removesuffix(suffix)` where your function returns a new *shortened* string
 3. `= any_string.index(subString)` or `=any_string.rindex(subString)` where your function returns the index where the substring starts.

 Here's a tricky one:
 
 4. `= any_string.replace(oldString, newString)` 
 
 > Hint: using `= any_string.index(oldString)' and `=len(oldString)` to find the oldString's start and stop points, <br>
then generate string slices from before and after, and concatenate them, along with the newString into a brand result.

### Other String methods to explore:
- `= any_string.split()` Try using it to split up a sentence into a list of words.

**Boolean String Methods**

- `= any_string.isupper()`,  `.islower()`, `.isalpha()`, `.isnumeric()` (this one does *not* work how we'd like it to),
<BR>`.endswith(ending)`, and `.startswith(starting)`

**And these interesting string methods taht deal with capitalization**
> `= any_string.upper()`, `.lower()`, `.title()`, `.capitalize()`

and their associated Boolean methods like `= any_string.islower()` etc.





