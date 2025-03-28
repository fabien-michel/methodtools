methodtools
===========

.. image:: https://travis-ci.com/youknowone/methodtools.svg?branch=master
    :target: https://travis-ci.com/youknowone/methodtools
.. image:: https://codecov.io/gh/youknowone/methodtools/graph/badge.svg
    :target: https://codecov.io/gh/youknowone/methodtools

Expand functools features to methods, classmethods, staticmethods and even for
(unofficial) hybrid methods.

Use `methodtools` module instead of `functools` module. Than it will work as
you expected.

.. code:: python

    from methodtools import lru_cache

    class A(object):

        # cached method. the storage lifetime follows `self` object
        @lru_cache()
        def cached_method(self, args):
            ...

        # cached classmethod. the storage lifetime follows `A` class
        @lru_cache()  # the order is important!
        @classmethod  # always lru_cache on top of classmethod 
        def cached_classmethod(self, args):
            ...

        # cached staticmethod. the storage lifetime follows `A` class
        @lru_cache()  # the order is important!
        @staticmethod  # always lru_cache on top of classmethod
        def cached_staticmethod(self, args):
            ...

    @lru_cache()  # just same as functools.lru_cache
    def cached_function():
        ...


Documentation
-------------

For now, `methodtools` only provides `lru_cache`.
See above for example.
See documentation of `functools.lru_cache` for arguments details.


Installation
------------

PyPI is the recommended way.

.. sourcecode:: shell

    $ pip install methodtools

To browse versions and tarballs, visit:
    `<https://pypi.python.org/pypi/methodtools/>`_

.. note::
    If you are working on Python 2, install also `functools32`.


See also
--------

This project is derived from `Ring <https://github.com/youknowone/ring/>`_,
a rich cache interface using the same method handling technique.
