# Python Method Decorators

Once you understand the ins and outs of functions, Python decorators should be fairly easy to grasp.
A Python decorator is simply a function that accepts a function as an argument, and then returns another function.
Sounds inception-like, but bare with us.

First, let's define a decorator method.
Its purpose is to the take the string output of a different method, completely uppercase it and return a method that will output the final string.

```py
def upper(message_function):
  def final_function():
    message_function_value = message_function()
    return message_function_value.upper()
  return final_function
```

Now we can decorate another method by preceding it with `@upper`.

By providing the `@upper` decorator, what Python does is pass the `message` method into the `upper` method as an argument.

```py
@upper
def message():
  return "Nashville Software School"
```

Now when you execute the `message()` method, what's actually being invoked is the `final_function()` method that the `heading()` returns.

```
Python 3.6.0 (default, Nov 16 2015, 10:56:55) 
[GCC 4.2.1 Compatible Apple LLVM 7.0.0 (clang-700.1.76)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> message()
'NASHVILLE SOFTWARE SCHOOL'
```

## HTML Output Formatting with Decorators

You can add as many decorators to a method that you like. Just make sure that each one returns a method that can be passed to the next one.

```py
def upper(message_function):
    def final_function():
        return message_function().upper()
    return final_function


def split(message_function):
    def final_function():
        return message_function().split()
    return final_function


def len_per_word(message_function):
    def final_function():
        return [(word, len(word)) for word in message_function()]
    return final_function


# In this example, the value goes from message to upper to split to len_per_word
@len_per_word
@split
@upper
def message(value):
    return value


print(message("Nashville Software School"))
```
