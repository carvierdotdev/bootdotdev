# Basic Variable types

## Strings

In programming, snippets of text are called "[strings](https://docs.python.org/3/library/stdtypes.html#textseq)". They're lists of characters _strung_ together. We create strings by wrapping the text in single quotes or double quotes. That said, **double quotes are preferred**.

```python
name_with_single_quotes = 'boot.dev' # not so good
name_with_double_quotes = "boot.dev" # so good
```

## Numbers

Numbers are _not_ surrounded by quotes when they're declared.

**An [integer](https://docs.python.org/3/c-api/long.html) (or "int") is a number without a decimal part**:

```python
x = 5 # positive integer
y = -5 # negative integer
```

**A [float](https://docs.python.org/3/library/functions.html#float) is a number with a decimal part**:

```python
x = 5.2
y = -5.2
```
## Booleans

A ["Boolean"](https://docs.python.org/3/c-api/bool.html#boolean-objects) (or "bool") is a type that can only have one of two values: `True` or `False`. As you may have heard, computers really only use 1's and 0's. These 1's and 0's are just `True/False` boolean values.

```python
is_tall = True
is_short = False
```
## F-string (Strings with Dynamic values)

In Python, we can create strings that contain dynamic values with the [f-string](https://docs.python.org/3/tutorial/inputoutput.html#formatted-string-literals) syntax.

- Add an `f` to the start of quotes to create an f-string: `f"this is easy!"`
- Use curly brackets `{}` around a variable to [interpolate](https://en.wikipedia.org/wiki/String_interpolation) (put) its value into the string.
- Remember, it's just a string! Don't overthink it!

```python
f"this is easy!"
```

## NoneType Variables

Not all variables have a value. We can make an "empty" variable by setting it to [`None`](https://docs.python.org/3/library/constants.html#None). `None` is a special value in Python that represents the absence of a value. It is _not_ the same as zero, False, or an empty string.

```python
my_mental_acuity = None
```

The value of `my_mental_acuity` in this case is `None` until we use the assignment operator, `=`, to give it a value.

## None Is NOT a String

[NoneType](https://docs.python.org/3/library/types.html#types.NoneType) is _not_ the same as a string with a value of "None":

```python
my_none = None # this is a None-type
my_none = "None" # this is a string with the value "None"
```

### When to use it

So when would you _use_ it? One use case is to represent that a value hasn't been determined yet, for example, an uncaptured input. Maybe your program is waiting for a user to enter their name. You might start with a variable:

```python
username = None
```

Then later in the code, once the user has entered their name, you can assign it to the `username` variable:

```python
username = input("What's your name? ")
```

Remember, it's crucial to recognize that `None` is not the same as the string `"None"`. They look the same when printed to the console, but they are different data types. If you use `"None"` instead of `None`, you will end up with code that looks correct when it's _printed_ but fails the _tests_.

## Dynamic Typing

Python is [dynamically typed](https://en.wikipedia.org/wiki/Type_system#Static_and_dynamic_type_checking_in_practice), which means a variable can store any type, and that type can _change_.

For example, if I make a number variable, I can later change that variable to a string:

```python
speed = 5
speed = "five"
```

### But Like, Maybe Don't

In almost all circumstances, it's a _bad idea_ to change the type of a variable. The "proper" thing to do is to just create a new one. For example:

```python
speed = 5
speed_description = "five"
```

### What Is Non-Dynamic Typing?

Languages that aren't dynamically typed are [statically typed](https://developer.mozilla.org/en-US/docs/Glossary/Static_typing), such as Go and Typescript (one of which you'll learn in a later course depending on your chosen track). In a statically typed language, if you try to assign a value to a variable of the wrong type, an error would crash the program.

If Python were statically typed, the first example from before wouldn't allow the second line, `speed = "five"`. The computer would give an error along the lines of `you can't assign a string value ("five") to a number variable (speed)`.

## Math With Strings (Concatenation)

When working with strings the `+` operator performs a "[concatenation](https://en.wikipedia.org/wiki/Concatenation)", which is a fancy word that means "joining two strings". _Generally speaking, it's better to use string interpolation with `f-strings` over `+` concatenation_.

```python
first_name = "Lane "
last_name = "Wagner"
full_name = first_name + last_name
print(full_name)
# prints "Lane Wagner"
```

`full_name` now holds the value "Lane Wagner".

Notice the extra space at the end of `"Lane "` in the `first_name` variable. That extra space is there to separate the words in the final result: `"Lane Wagner"`.

## Multi-Variable Declaration

We can save space when creating many new variables by declaring them on the same line:

```python
sword_name, sword_damage, sword_length = "Excalibur", 10, 200
```

Which is the same as:

```python
sword_name = "Excalibur"
sword_damage = 10
sword_length = 200
```

Any number of variables can be declared on the same line, and variables declared on the same line _should_ be related to one another in some way so that the code remains easy to understand.

We call code that's easy to understand "clean code".

