Installation
============

.. |github| image:: _static/GitHub-Mark-32px.png
   :height: 25px

.. |beerme| image:: https://badgen.net/badge/BeerMe/1.2.0/yellow?icon=atom
   :height: 20px
   :target: http://beerme.nishantgerald.com



Clone |github| Repo
-------------------

|beerme|

First thing you want to do is clone the `BeerMe <https://github.com/nishantgerald/BeerMe>`_ repo:

.. code-block:: console

   git clone https://github.com/nishantgerald/BeerMe.git

.. admonition:: Installation Note

   Please assume that any/all commands that are run, are executed from the project root directory.

Requirements
------------

.. admonition:: BeerMe Package Requirements

   * certifi
   * click==8.1.3
   * Flask==2.2.2
   * importlib-metadata==4.12.0
   * itsdangerous==2.1.2
   * Jinja2==3.1.2
   * MarkupSafe==2.1.1
   * numpy==1.23.3
   * pandas==1.5.0
   * python-dateutil==2.8.2
   * pytz==2022.2.1
   * six==1.16.0
   * Werkzeug==2.2.2
   * zipp==3.8.1

You can install all of them by running the following:

.. code-block:: console

   pip install -r requirements.txt

Get latest Brewery Data 
-----------------------

BeerMe uses open-source brewery data from `OpenBreweryDB <https://www.openbrewerydb.org/>`_
I've saved you the time of having to pull down the data manually, and you can do so by running the
``update_data`` script.

Update the dataset using:

.. code-block:: console

   ./beerme/data/update_data.sh

That should pull down the latest brewery data from the following regions:

* England
* France
* Ireland
* Poland
* Scotland
* South Korea
* United States

Once pulled down, they are all concatenated into a single ``brewery.csv`` file (exluding headers, since they are common across regions).

Initialize SQLite3 Database
---------------------------
Once the Brewery data has been updated, you can go ahead and initialize our SQLite database. The purpose
of this database is the store user registration data, as well as beer check-in data.

Initialize the database using:

.. code-block:: console

   flask --app beerme init-db

Deploy
---------------------------
You're now ready to deploy the application:

.. code-block:: console

   flask --app beerme run -p 5001

In this example we've deploy BeerMe on port 5001, however, you can use any unused port on your server.

Reset Database
---------------------------
If, for some reason, you need to reset the database to a fresh new version:

1. Remove the old sqlite file using ``rm instance/beerme.sqlite``, and
2. Rerun the database initialization function ``flask --app beerme init-db``


Congratulations - you're all set!