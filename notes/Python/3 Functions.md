# Functions

**Functions help when it's needed to reuse the same logic.** We can define a new function called `area_of_circle` using the `def` keyword.

## Printing vs. Returning

Some new developers get hung up on the difference between `print()` and `return`.

It can be particularly confusing when the test suite we provide simply prints the output of your functions to the console. It makes it _seem_ like `print()` and `return` are interchangeable, _but they are not_!

- `print()` is a function that:
    1. Prints a value to the console
    2. Does _not_ return a value
- `return` is a keyword that:
    1. Ends the current function's execution
    2. Provides a value (or values) back to the caller of the function
    3. Does _not_ print anything to the console (unless the return value is later `print()`ed)

## Printing to Debug Your Code

Printing values and running your code is a great way to debug your code. You can see what values are stored in various variables, find your mistakes, and fix them. Add print statements and run your code as you go! It's a great habit to get into to make sure that each line you write is doing what you expect it to do.

In the real world it's rare to leave `print()` statements in your code when you're done debugging. Similarly, you need to remember to remove any `print()` statements from your code before submitting your work here on Boot.dev because it will interfere with the tests!

## Where to Declare Functions

You've probably noticed that a variable needs to be declared _before_ it's used. For example, the following doesn't work:

```python
print(my_name)
my_name = 'Lane Wagner'
# NameError: 'my_name' is not defined
```

It needs to be:

```python
my_name = 'Lane Wagner'
print(my_name)
# Lane Wagner
```

Code executes in _order from top to bottom_, so a variable needs to be created before it can be used. That means that if you define a function, you can't call that function until _after_ it has been defined.

## Order of Functions

All functions must be defined before they're used.

You might think this would make structuring Python code hard because the order of the functions needs to be just right. As it turns out, there's a simple trick that makes it super easy.

Most Python developers solve this problem by defining all the functions in their program first, then they call an "entry point" function last. That way all of the functions have been read by the Python interpreter before the first one is called.

> Conventionally this "entry point" function is usually called main to keep things simple and consistent.

```python
def main():
    health = 10
    armor = 5
    add_armor(health, armor)

def add_armor(h, a):
    new_health = h + a
    print_health(new_health)

def print_health(new_health):
    print(f"The player now has {new_health} health")

# call entrypoint last
main()
```

## None Return value

When no return value is specified in a function, it will automatically return None. For example, maybe it's a function that prints some text to the console, but doesn't explicitly return a value. The following code snippets all return the same value, **None**:

With **Return none**
```python
def my_func():
    print("I do nothing")
    return None
```
With **Return**
```python
def my_func():
    print("I do nothing")
    return
```
Without anything
```python
def my_func():
    print("I do nothing")
```

## What's the difference between printing a value and returning it?

- Print: Shows a value in the console.
- Return: Makes a value available to the caller of the function

## Multiple Return Values in a Function

A function can return more than one value by separating them with commas.

```python
def cast_iceblast(wizard_level, start_mana):
    damage = wizard_level * 2
    new_mana = start_mana - 10
    return damage, new_mana # return two values
```

### Receiving Multiple Values

When calling a function that returns multiple values, you can assign them to multiple variables.

```python
damage, mana = cast_iceblast(5, 100)
print(f"Damage: {damage}, Remaining Mana: {mana}")
# Damage: 10, Remaining Mana: 90
```

When `cast_iceblast` is called, it returns two values. The first value is assigned to `damage`, and the second value is assigned to `mana`. Just like function inputs, it's the _order_ of the values that matters, not the variable names. We could just as easily have named the variables `one` and `two`:

```python
one, two = cast_iceblast(5, 100)
print(f"Damage: {one}, Remaining Mana: {two}")
# Damage: 10, Remaining Mana: 90
```

Descriptive variable names make your code easier to understand, so name them well!

### What Happened to the Variables?

The `damage` and `new_mana` variables from `cast_iceblast`'s function body only exist _inside_ of the function. They can't be used outside of the function. More on that later when we talk about scope.

## Parameters vs. Arguments

Parameters are the names used for inputs when defining a function. Arguments are the values of the inputs supplied when a function is called.

To reiterate, arguments are the actual values that go into the function, such as 42.0, "the dark knight", or True. Parameters are the names we use in the function definition to refer to those values, which at the time of writing the function, can be whatever we like.

That said, this is all semantics, and frankly developers are really lazy with these definitions. You'll often hear the words "arguments" and "parameters" used interchangeably.

### TL.DR.

- Parameter are the inputs specified by the function definition
- Arguments are the values that are passed into the function by the caller

```python
# a and b are parameters
def add(a, b):
    return a + b

# 5 and 6 are arguments
sum = add(5, 6)
```

## Default Values

In Python you can specify a [default](https://docs.python.org/3/glossary.html#term-parameter) value for a function parameter. It's nice for when a function has parameters that are "optional". You as the function definer can specify a specific default value in case the caller doesn't provide one.

A default value is created by using the assignment (`=`) operator in the function signature.

```python
def get_greeting(email, name="there"):
    print("Hello", name, "welcome! You've registered your email:", email)
```

```python
get_greeting("lane@example.com", "Lane")
# Hello Lane welcome! You've registered your email: lane@example.com
```

```python
get_greeting("lane@example.com")
# Hello there welcome! You've registered your email: lane@example.com
```

If the second parameter is omitted, the default `"there"` value will be used in its place. As you may have guessed, for this structure to work, optional parameters (the ones with defaults) must come _after_ all required parameters.