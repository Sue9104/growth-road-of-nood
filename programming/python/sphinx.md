# Sphinx

## Install

```bash
pip install sphinx
pip install sphinx-rtd-theme
```

## Quick start

```bash
sphinx-quickstart docs
```

### source/conf.py

```python
# add project path to sys.path
import os                                                                        
import sys                                                                       
sys.path.insert(0, os.path.abspath('../../'))
 
# edit theme
html_theme = 'sphinx_book_theme'
 
# edit extension
extensions = [
    'sphinx.ext.autodoc',
    'sphinx.ext.coverage',
    'sphinx.ext.napoleon',
    'sphinx.ext.intersphinx',
]
 
 
intersphinx_mapping = {
    'python': ('https://docs.python.org/3',(None, 'python-inv.txt'))}
 
```

### index.rst

```python
# automodule
.. automodule::module_name
    :members:
    :show-inheritance:
```

### run

```python
# generate rst file
sphinx-apidoc -f source python_project_path

# directly generate html in docs
make html
```

* Log Level
  * error
  * note
  * tip
  * warning

## script annotation

> Google Style: [https://google.github.io/styleguide/pyguide.html](https://google.github.io/styleguide/pyguide.html)

### function

```python
    """Fetches rows from a Smalltable.

    Retrieves rows pertaining to the given keys from the Table instance
    represented by table_handle.  String keys will be UTF-8 encoded.

    Args:
        table_handle: An open smalltable.Table instance.
        keys: A sequence of strings representing the key of each table
        row to fetch.  String keys will be UTF-8 encoded.
        require_all_keys: Optional; If require_all_keys is True only
        rows with values set for all keys will be returned.

    Returns:
        A dict mapping keys to the corresponding table row data
        fetched. For example:

        {b'Serak': ('Rigel VII', 'Preparer'),
        b'Zim': ('Irk', 'Invader'),
        b'Lrrr': ('Omicron Persei 8', 'Emperor')}

    Raises:
        IOError: An error occurred accessing the smalltable.
    """
```

### class

```python
    """Summary of class here.

    Longer class information....
    Longer class information....

    Attributes:
        likes_spam: A boolean indicating if we like SPAM or not.
        eggs: An integer count of the eggs we have laid.
    """
```
