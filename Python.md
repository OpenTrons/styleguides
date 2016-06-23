# Python

Unless otherwise specified, follow [PEP 8](http://www.python.org/dev/peps/pep-0008/).  For
docstrings, follow [PEP 257](http://www.python.org/dev/peps/pep-0257).

## Indentation

Use 4 spaces per indentation level.  Do not use tabs.

Continuation lines should use a hanging indent.

```python
# Do this:  Use more indentation to distinguish the hanging indent from
# the rest of the code
def long_function_name(
        var_one, var_two, var_three,
        var_four):
    print(var_one)

# Don't do this:  Aligning arguments with opening delimeter
foo = long_function_name(var_one, var_two,
                         var_three, var_four)
```

Line up the closing brace / bracket / parenthesis on multi-line constructs under the last item of the list

```python
my_list = [
    1, 2, 3,
    4, 5, 6,
    ]
```

## Tabs or Spaces?

Spaces, not tabs.

## Maximum Line Length

We will limit lines to 79 characters, even in this modern world of massive screens.  Limit
long blocks of text like docstrings or comments to 72 characters.  We do this for several
reasons:

* Even with large monitors, some of us will have an editor opened side-by-side with a browser window.

* It fits better in smaller screens (laptops).

* It fits better within the Github web interface.

## Encodings

Follow the recommended policy:  all identifiers must use ASCII-only, and should use English words.  String literals and comments must also be in ASCII.  If for any reason a string literal needs to contain non-ASCII characters, use `\x`, `\u`, or `\U` escapes.

## Imports

Import only modules.  Use `as` to resolve name conflicts, if necessary.  Use `from` for all imports below top-level.  Use only absolute imports; do not use relative imports.  Do not import packages, classes, functions, fields, or anything that is not a module.

Do not use wildcard imports.

(`from foo import *` or `import bar.baz.Spar` can lead to serious maintenance issues because it makes it hard to find module dependencies.  Importing the module effectively wraps usage of any class or function within the module in a namespace.)

```python
import os
import sys

from models.graphics import views as graphics_views
from models.sounds import views as sounds_views
from sound.effects import echo
...
echo.echofilter(input, output, delay=0.7, atten=4)
```

Even if the module is in the same package, do not directly import the module without the full package name. This might cause the package to be imported twice and have unintended side effects.

## Classes

If a class inherits from no other base classes, explicitly inherit from `object`.

```python
# Do this
class SimpleClass(object):
    pass

# Not this
class SimpleClass:
    pass
```

## String formatting

When interpolating strings with variables, use the `str.format` function rather than the `%` operator.  This is the new standard in Python 3.

Use the single quote character `'` rather than double quotes `"` for small, symbol-like strings (anything behaving like an identifier), and double quotes for natural language text, strings being formatted/interpolated, docstrings, and raw string literals in regular expressions.

```python
LIGHT_MESSAGES = {
    'English': "There are %(number_of_lights)s lights.",
    'Pirate':  "Arr! Thar be %(number_of_lights)s lights."
    }

def lights_message(language, number_of_lights):
    """Return a language-appropriate string reporting the light count."""
    return LIGHT_MESSAGES[language] % locals()

def is_pirate(message):
    """Return True if the given message sounds piratical."""
    return re.search(r"(?i)(arr|avast|yohoho)!", message) is not None
```

## Conclusion

Be consistent.  But know when to be inconsistent (aka, when to break the rules).

Some elements above are taken from Stack Overflow or the following sites -- but these
resources (in whole or in part, other than the specific items above) should not be taken
as a definitive part of this style guide.

* [Google's Python Style Guide](http://google-styleguide.googlecode.com/svn/trunk/pyguide.html)
* [The Hitchhiker's Guide to Python!](http://docs.python-guide.org/en/latest/index.html)
* [Michael Foord's Personal Style Guide](http://www.voidspace.org.uk/python/articles/python_style_guide.shtml)
* [Stack Overflow: single quotes vs. double quotes](http://stackoverflow.com/questions/56011/single-quotes-vs-double-quotes-in-python?rq=1)
* [Style Guide for Melange GSoC](http://code.google.com/p/soc/wiki/PythonStyleGuide)
