# prettierjson

[![made-with-python](https://img.shields.io/badge/Made%20with-Python-1f425f.svg?style=flat-square)](https://www.python.org/)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg?style=flat-square)](https://github.com/psf/black)
[![Github release](https://img.shields.io/badge/release-1.0.1-blue.svg?style=flat-square)](https://github.com/brianburwell11/prettierjson/releases/tag/1.0.1)
[![PyPi](https://img.shields.io/badge/-PyPi-white.svg?logo=pypi&labelColor=4B8BBE&logoColor=FFD43B&style=flat-square)](https://pypi.org/project/prettierjson/)
[![Documentation](https://img.shields.io/badge/-Documentation-2980b9.svg?logo=readthedocs&labelColor=2980b9&logoColor=FFFFFF&style=flat-square)][documentation]

Generate prettier and more compact JSON dumps

## Installation

**prettierjson** can be installed using one of these commands:

```sh
pip install prettierjson
```

```sh
poetry add prettierjson
```

## Usage

### in python scripts

prettierjson offers one function `prettierjson.dumps()` which is intended to be used as a drop-in replacement for `json.dumps()`

```python
from prettierjson import dumps

my_dictionary = {"foo": bar}

with open("foobar.json", "w") as f:
    f.write(dumps(my_dictionary))
```

If prettierjson needs to exist within the same module as the built-in json package _without overriding_ the default `json.dumps()`, the entire package should be imported in order to avoid namespace collisions
```python
import json
import prettierjson

my_dictionary = {"foo": bar}

with open("builtin.json", "w") as f:
    f.write(json.dumps(my_dictionary))
with open("prettierjson.json", "w") as f:
    f.write(prettierjson.dumps(my_dictionary))
```

See [the documentation][documentation] for more details.


### as a command line interface

prettierjson can also be as a command line interface

In this way, prettierjson can be used to "prettify" one or multiple JSON files in-place by passing them as arguments
```sh
$ prettierjson PATH/TO/JSON/FILE1.json PATH/TO/JSON/FILE2.json
```

Indent size and max line length can be set with the `--indent` and `--line-length` flags
```sh
$ prettierjson --indent=2 --line-length=88 PATH/TO/JSON/FILE.json
```

Run `prettierjson -h` for more command line usage details.


<!-- links -->
[poetry]: https://python-poetry.org/docs/
[changelog]: docs/CHANGELOG.md
[documentation]: https://github.com/brianburwell11/prettierjson/wiki
