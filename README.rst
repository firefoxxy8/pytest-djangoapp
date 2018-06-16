pytest-djangoapp
================
https://github.com/idlesign/pytest-djangoapp

|release|  |lic|

.. |release| image:: https://img.shields.io/pypi/v/pytest-djangoapp.svg
    :target: https://pypi.python.org/pypi/pytest-djangoapp

.. |lic| image:: https://img.shields.io/pypi/l/pytest-djangoapp.svg
    :target: https://pypi.python.org/pypi/pytest-djangoapp


**Work in progress. Stay tuned.**


Description
-----------

*Nice pytest plugin to help you with Django pluggable application testing.*

This exposes some useful tools for Django applications developers to facilitate tests authoring, including:

* Settings overriding
* Template tags testing
* Users creation
* Request object mocking
* etc.

Suitable for Django 1.7+.


How to use
----------

Let's say you have classical tests placing (inside application directory):

.. code-block::

    package_dir
    |__ myapp
    |  |__ __init__.py
    |  |__ tests
    |  |  |__ __init__.py
    |  |  |__ conftest.py  <- Configure djangoapp here.
    |
    |__ setup.py


Add the following lines into `conftest.py` to configure `djangoapp` and start using it:

.. code-block:: python

    # conftest.py
    from pytest_djangoapp import configure_djangoapp_plugin

    pytest_plugins = configure_djangoapp_plugin()


Fixtures usage examples can be found in the documentation and the source code.


What about pytest-django
------------------------

There is a couple of design decisions in `pytest-django` that might make it uncomfortable to work with.

1. It uses `setuptools` entrypoints feature for `pytest` plugin discovery. It's not a problem by itself,
   but alongside with all kinds of bootstrapping with side effects made by `pytest-django` just on startup,
   makes the plugin a poor choice for cases of system-wide (i.e. not venv) installations.

2. Philosophy that next to no unit test should require DB access may be quite annoying.


Documentation
-------------

http://pytest-djangoapp.readthedocs.org/