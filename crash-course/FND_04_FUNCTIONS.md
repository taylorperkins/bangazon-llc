# Functions
In python, creating functions is very simple.
The biggest thing to consider is indentation.
Start at the wall of the file, then indent out 4 spaces to start the contents of the function.
Here is how you (def)ine it.

```python
def display_name(name):
    print(name)

display_name('Josephina')
```

You can define documentation for a function. This is highly encouraged.

```
>>> def display_name(name):
...     """Displays a name
... 
...     Arguments:
...     name -- a string to be printed
...     """
...     print(name)
... 
>>> display_name('Josephina')
Josephina
>>> 
>>> print(display_name.__doc__)
Displays a name

    Arguments:
    name -- a string to be printed

```
