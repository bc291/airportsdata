============
airportsdata
============

.. |ICAO| replace:: 28,876

.. |IATA| replace:: 6,571

.. |version| image:: https://img.shields.io/pypi/v/airportsdata.svg
    :target: https://pypi.org/project/airportsdata/
    :alt: pypi version

.. |support| image:: https://img.shields.io/pypi/pyversions/airportsdata.svg
    :target: https://pypi.org/project/airportsdata/
    :alt: supported Python version

.. |license| image:: https://img.shields.io/pypi/l/airportsdata.svg
    :target: https://pypi.org/project/airportsdata/
    :alt: license

.. |issues| image:: https://img.shields.io/github/issues-raw/mborsetti/airportsdata
    :target: https://github.com/mborsetti/airportsdata/issues
    :alt: issues

.. |CI| image:: https://github.com/mborsetti/airportsdata/workflows/Tests/badge.svg?branch=main
    :target: https://github.com/mborsetti/airportsdata/actions
    :alt: CI testing status

.. |coveralls| image:: https://coveralls.io/repos/github/mborsetti/airportsdata/badge.svg?branch=main
    :target: https://coveralls.io/github/mborsetti/airportsdata?branch=main
    :alt: code coverage by Coveralls


Extensive database of location and timezone data for nearly every airport and landing strip in the world, with |ICAO|
entries.

Each entry consists of the following data:

* ``icao``: ICAO 4-alphanumeric code or FAA/TC LID[*] (|ICAO| entries)
* ``iata``: IATA 3-letter code (for |IATA| entries) or an empty string
* ``name``: Official name (latin script)
* ``city``: City
* ``subd``: Subdivision (e.g. state, province, region, etc.)
* ``country``: `ISO 3166-1 <https://en.wikipedia.org/wiki/ISO_3166-1#Current_codes>`__ alpha-2 country code
  (plus ``XK`` for Kosovo)
* ``elevation``: MSL elevation (the highest point of the landing area) in feet
* ``lat``: Latitude (decimal)
* ``lon``: Longitude (decimal)
* ``tz``: Timezone expressed as a `tz database name <https://en.wikipedia.org/wiki/List_of_tz_database_time_zones>`__
  (IANA-compliant)

.. [*] See `here <https://github.com/mborsetti/airportsdata/README_FAA.rst>`__ for an explanation on how
   airports with only an U.S. FAA or Transport Canada Location Identifier location identifier (FAA/TC LID) are
   listed.  See `here <https://github.com/mborsetti/airportsdata/README_IATA.rst>`__ for a list of IATA Multi
   Airport Cities.

Best efforts are placed to review all contributions for accuracy, but accuracy cannot be guaranteed nor should be
expected by users.

Known issues:

* 219 aerodromes have IATA codes that are not in the `IATA database
  <https://www.iata.org/en/publications/directories/code-search/>`__ and may be incorrect;
* A small, but unknown, number of aerodromes are missing their IATA code (none are major ones);
* Timezone was originally sourced from `TimeZoneDB <https://timezonedb.com>`__ and is missing for Antarctica;
* No historical data.

Please report any issues you may find `here
<https://github.com/mborsetti/airportsdata/blob/main/CONTRIBUTING.rst>`__.

This project is a fork of https://github.com/mwgg/Airports. All IATA codes submitted in this fork have been
validated against `IATA <https://www.iata.org/en/publications/directories/code-search/>`__.

Raw data
========

A CSV (comma separated values) file with headers (UTF-8 encoding) is downloadable from GitHub `here
<https://github.com/mborsetti/airportsdata/raw/main/airportsdata/airports.csv>`__.

Python
======
|version| |support| |CI| |coveralls| |issues|

Install from `PyPi <https://pypi.org/project/airportsdata/>`__  using pip:

.. code-block:: bash

  pip install -U airportsdata

Once installed, to load the data into a dict:

.. code-block:: python

  import airportsdata
  airports = airportsdata.load()  # key is ICAO code, the default
  print(airports['KJFK'])

or

.. code-block:: python

  import airportsdata
  airports = airportsdata.load('IATA')  # key is IATA code
  print(airports['JFK'])

License
=======

|license|

Released under the `MIT License <https://opensource.org/licenses/MIT>`__ (see license `here
<https://github.com/mborsetti/airportsdata/blob/main/LICENSE>`__).
