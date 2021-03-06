multisplitby |build| |coverage| |zenodo|
========================================
Split an iterable into multiple using arbitrary predicates.

This package comes with a single function: ``multisplitby.multi_split_by``.

For all lists ``values`` and ``predicates``, the following conditions are always true:

1. ``1 + len(predicates) = len(list(multi_split_by(values, predicates)))``
2. ``values == itertools.chain.from_iterable(multi_split_by(values, predicates))``

Normal usage with one predicate:

.. code-block:: python

   >>> values = range(4)
   >>> predicates = [lambda x: 2 < x]
   >>> list(map(list, multi_split_by(values, predicates)))
   [[0, 1, 2], [3]]

Normal usage with several predicates:

.. code-block:: python

   >>> values = range(9)
   >>> predicates = [lambda x: 2 < x, lambda x: 4 < x, lambda x: 7 < x]
   >>> list(map(list, multi_split_by(values, predicates)))
   [[0, 1, 2], [3, 4], [5, 6, 7], [8]]

If no values are given, will result in ``|predicates| + 1`` generators, all yielding empty lists.

.. code-block:: python

   >>> values = []
   >>> predicates = [lambda x: 2 < x, lambda x: 4 < x, lambda x: 7 < x]
   >>> list(map(list, multi_split_by(values, predicates)))
   [[], [], [], []]

If no predicates are given, will result in a single generator that yields the original list:

.. code-block:: python

   >>> values = range(4)
   >>> predicates = []
   >>> list(map(list, multi_split_by(values, predicates)))
   [[0, 1, 2, 3]]

Installation |pypi_version| |python_versions| |pypi_license|
------------------------------------------------------------
Install from `PyPI <https://pypi.python.org/pypi/multisplitby>`_ with:

.. code-block:: bash

   $ pip install multisplitby

or get the latest code from `GitHub <https://github.com/cthoyt/multisplitby>`_ with:

.. code-block:: bash

   $ git clone https://github.com/cthoyt/multisplitby.git
   $ cd multisplitby
   $ pip install -e .

.. |build| image:: https://travis-ci.com/cthoyt/multisplitby.svg?branch=master
    :target: https://travis-ci.com/cthoyt/multisplitby

.. |coverage| image:: https://codecov.io/gh/cthoyt/multisplitby/branch/master/graph/badge.svg
    :target: https://codecov.io/gh/cthoyt/multisplitby

.. |python_versions| image:: https://img.shields.io/pypi/pyversions/multisplitby.svg
    :alt: Stable Supported Python Versions

.. |pypi_version| image:: https://img.shields.io/pypi/v/multisplitby.svg
    :alt: Current version on PyPI

.. |pypi_license| image:: https://img.shields.io/pypi/l/multisplitby.svg
    :alt: Apache 2.0 License

.. |zenodo| image:: https://zenodo.org/badge/155096674.svg
   :target: https://zenodo.org/badge/latestdoi/155096674
