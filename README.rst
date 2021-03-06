STIX Document Validator
=======================

A Python tool and API that validates STIX XML instance documents.

.. _XML Schema: http://stix.mitre.org/language/
.. _STIX Profiles: http://stixproject.github.io/documentation/profiles/
.. _Best Practices: http://stixproject.github.io/documentation/suggested-practices/

:Source: https://github.com/STIXProject/stix-validator
:Documentation: http://stix-validator.readthedocs.org
:Information: http://stix.mitre.org

|travis badge| |health badge| |version badge| |downloads badge|

.. |travis badge| image:: https://api.travis-ci.org/STIXProject/stix-validator.png?branch=master
   :target: https://travis-ci.org/STIXProject/stix-validator
   :alt: Build Status
.. |health badge| image:: https://landscape.io/github/STIXProject/stix-validator/master/landscape.svg
   :target: https://landscape.io/github/STIXProject/stix-validator/master
   :alt: Code Health
.. |version badge| image:: https://pypip.in/v/stix-validator/badge.png
   :target: https://pypi.python.org/pypi/stix-validator/
.. |downloads badge| image:: https://pypip.in/d/stix-validator/badge.png
   :target: https://pypi.python.org/pypi/stix-validator/

Validation
----------

The **STIX Document Validator** can perform the following forms of 
STIX document validation:

* `XML Schema`_: Validate STIX documents against bundled or external 
  STIX schemas.
* `STIX Profiles`_: Verify STIX Profile conformance (**experimental**)
* `Best Practices`_: Verify alignment with STIX Best Practices.

Dependencies
------------

The **STIX Document Validator** has the following dependencies:

* `Python`_ v2.7: Python interpreter
* `lxml`_ >= v3.2.0: XML processing library.

  * `libxml2`_ >= v2.9.1: Required XML processing C 
    library for ``lxml``.
* `xlrd`_ >= v0.9.2: XLSX library for parsing STIX Profiles.
* `ordereddict`_ >= 1.1: A drop-in replacement for ``collections.OrderedDict``
  on Python 2.6.

.. _Python: http://python.org/download
.. _lxml: http://lxml.de/index.html#download
.. _libxml2: http://www.xmlsoft.org/downloads.html
.. _xlrd: https://pypi.python.org/pypi/xlrd
.. _ordereddict: https://pypi.python.org/pypi/ordereddict

For a Windows installer of lxml, we recommend looking here: 
http://www.lfd.uci.edu/~gohlke/pythonlibs/#lxml

The **STIX Document Validator** is developed and actively tested against 
Python 2.7; we believe that most parts should also work with Python 2.6, 
however we make no guarantees. If you encounter an error under Python 2.6,
please let us know so we can investigate whether a fix is feasible.

The **STIX Document Validator** is not compatible with Python 3.


Installation
------------

The recommended method for installing the **STIX Document Validator** is via
``pip``.

::

  $ pip install stix-validator

This will install the ``sdv`` package into your Python installation's
``site-packages`` and a ``stix_validator.py`` script on your ``PATH``.


How To Use
----------

The **STIX Document Validator** bundles a ``stix_validator.py`` script
which can can validate a STIX XML document against STIX schemas, STIX 
Best Practices, and STIX Profiles.

**NOTE:** The STIX Profile validation and conversion capabilities should be
considered **experimental.**

**Validate using local schemas**  

::

  $ stix_validator.py <stix_document.xml>

**Validate using schemaLocation**  

::

  $ stix_validator.py --use-schemaloc <stix_document.xml>

**Validate using non-bundled schemas**

::

  $ stix_validator.py --schema-dir </path/to/schemas> <stix_document.xml>

**Validate a directory of STIX documents**  

::

  $ stix_validator.py </path/to/stix_dir>

**Validate multiple files and/or directories**  

::

  $ stix_validator.py <one.xml> <two.xml> <directory_of_files> ...

**Check "best practice" guidance**  

:: 

  $ stix_validator.py --best-practices <stix_document.xml>

**Validate using STIX Profile**  

::
 
  $ stix_validator.py --profile <stix_profile.xlsx> <stix_document.xml>

**Translate STIX Profile to XSLT/Schematron**  

::

  $ stix_validator.py --profile <stix_profile.xlsx> --xslt-out <stix_profile.xslt> --schematron-out <stix_profile.sch>

All STIX Documents?
-------------------

The **STIX Document Validator** bundles a schema directory with it, which 
includes all STIX schema files (v1.0 through v1.1.1). If an instance document 
uses constructs or languages defined by other schemas a user must point the 
**STIX Document Validator** at those schemas in order to validate.

To use schemas other than those bundled with the **STIX Document Validator**
use the ``--schemas-dir`` flag to pass in a path to a STIX schema directory.

Common Libxml2 Error
--------------------

Users often report an error which looks something like the following:

::

    Fatal error occurred: local union type: A type, derived by list or union, must have the
    simple ur-type definition as base type, not '{http://cybox.mitre.org/common-2}(NULL)'., line 350

This error is caused by an insufficient version of libxml2 being installed
on the system. The **STIX Document Validator** requires ``libxml2`` v2.9.1 at
a minimum and is not guaranteed to work properly with earlier versions.

To see what version of libxml2 you have installed, execute the
``xml2-config --version`` command and make sure you are running at least v2.9.1.

Terms
-----

BY USING THE STIX DOCUMENT VALIDATOR, YOU SIGNIFY YOUR ACCEPTANCE OF THE 
TERMS AND CONDITIONS OF USE.  IF YOU DO NOT AGREE TO THESE TERMS, DO NOT USE 
THE STIX DOCUMENT VALIDATOR.

For more information, please refer to the LICENSE.txt file
