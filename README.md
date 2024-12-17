# Why do we have this repo at Festi?

This is just a minor supply-chain security / robustness issue, since we're using this
package in festi-ecommerce-n1.

If the maintainer would suddenly decide to delete the github repo, or change its license,
or make breaking changes, or make malignant changes, then it won't affect us.

So please ignore, but don't delete.

python-kennitala
================

python-kennitala is a python library for common operations on Icelandic
National Registry codes - [kennitala](https://en.wikipedia.org/wiki/Kennitala).

## Capabilities

* Validation of kennitala
* Extraction of birth date from kennitala
* Generating kennitala for a given birth date (for people or companies)
* Generating random kennitala (for people or companies)
* Recognize if kennitala belongs to person or company
* Common formatting.

## Usage

    >>> from datetime import date
    >>> from kennitala import Kennitala
    >>>
    >>> kt_no = '0101109639'
    >>> kennitala = Kennitala(kt_no)
    >>> kennitala.validate()
    True
    >>> kennitala.get_birth_date()
    datetime.date(1910, 1, 1)
    >>> kennitala.only_digits()
    '0101109639'
    >>> kennitala.with_dash()
    '010110-9639'
    >>> kennitala = Kennitala(kt_no.replace('3', '4'))
    >>> kennitala.validate()
    False
    >>> kennitala.get_birht_date()
    Traceback (most recent call last):
        File kennitala.py, in get_birth_date
    kennitala.Invalid
    >>>
    >>> company_kt = Kennitala.generate(date.today(), person=False)
    >>> Kennitala.is_personal(company_kt)
    False


## Installation

inside your virtualenv execute:

    $ pip install kennitala

or download and install manually.


## Tests

Tests are written for [py.test](https://pytest.org/latest)

To run tests simply execute:

    $ PYTHONPATH=./ py.test tests
