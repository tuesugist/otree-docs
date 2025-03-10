Version history
```````````````

Version 5.3
===========

-   Bugfix to deleting sessions in devserver
-   ``{{ static }}`` tag checks that the file exists
-   In SessionData tab, fix the "next round"/"previous round" icons on Mac
-   Fix to currency formatting in Japanese/Korean/Turkish currency (numbers were displayed with a decimal when there should be none)
-   allow error_message to be run on non-form pages (e.g. live pages)
-   Better error reporting when an invalid value is passed to ``js_vars``
-   Minor fixes & improvements


Version 5.2
===========

-   For compatibility with oTree 3.x,
    formfield ``<input>`` elements now prefix their ``id`` attribute with ``id_``.
    If you use ``getElementById``/``querySelector``/etc. to select any formfield inputs,
    you might need to update your selectors.
-   The data export now outputs "time started" as UTC.
-   "Time spent" data export has a column name change.
    If you have been using the ``pagetimes.py`` script,
    you should download the new version.

Version 5.1
===========

-   Breaking changes to REST API

Version 5.0
===========

-   oTree Lite
-   The no-self format
-   The beta method ``Player.start()`` has been removed.
-   ``cu()`` is now available as an alias for ``Currency``.
    ``c()`` will still work as long as you have ``from otree.api import Currency as c``
    at the top of your file.
    More details `here <https://groups.google.com/g/otree/c/Bwv67asPIlo>`__.
-   oTree 3.x used two types of tags in templates: ``{{ }}`` and ``{% %}``.
    Starting in oTree 5, however, you can forget about ``{% %}`` and just use ``{{ }}`` everywhere if you want.
    More details `here <https://groups.google.com/g/otree/c/Bwv67asPIlo>`__.
-   All REST API calls now return JSON

Version 3.3
===========

-   BooleanField now uses radio buttons by default (instead of dropdown)
-   ``otree zip`` can now keep your requirements.txt up to date.
-   oTree no longer installs `sentry-sdk`. If you need Sentry on Heroku, you should add it to your `requirements.txt` manually.
-   Faster server
-   Faster startup time
-   Faster installation
-   Data export page no longer outputs XLSX files. Instead it outputs CSV files formatted for Excel
-   Admin UI improvements, especially session data tab

Version 3.2
===========

-   Should use less memory and have fewer memory spikes.
-   Enhancements to SessionData and SessionMonitor.

Version 3.1
===========

-   New way to define :ref:`roles`
-   You can pass a string to ``formfield``, for example ``{{ formfield 'contribution' }}``.

Version 3.0
===========

Live pages
----------

See :ref:`live`.

REST API
--------

See :ref:`rest`

Custom data export
------------------

See :ref:`custom-export`.

Other things
------------

-   Python 3.8 is now supported.
-   Speed improvements to devserver & zipserver
-   You can now download a single session's data as Excel or CSV (through session's Data tab)
-   When browser bots complete, they keep the last page open
-   group_by_arrival_time: quicker detection if a participant goes offline
-   Browser bots use the REST API to create sessions
    (see :ref:`rest`).
-   Instead of ``runprodserver`` you can now use ``prodserver`` (that will be the preferred name going forward).
-   "Page time" data export now has more details such as whether it is a wait page.
-   ``devserver`` and ``zipserver`` now must use ``db.sqlite3`` as the database.


Version 2.5
===========
-   Removed old ``runserver`` command.
-   Deprecated non-oTree widgets and model fields. See `here <https://groups.google.com/forum/#!topic/otree/vsvsQ7njjY8>`__.

Version 2.4
===========

-   ``zipserver`` command
-   New MTurk format
-   oTree no longer records participants' IP addresses.

Version 2.3
===========

-   Various improvements to performance, stability, and ease of use.
-   oTree now requires Python 3.7
-   oTree now uses Django 2.2.
-   Chinese/Japanese/Korean currencies are displayed as 元/円/원 instead of ¥/₩.
-   On Windows, ``prodserver`` just launches 1 worker process. If you want more processes,
    you should use a process manager. (This is due to a limitation of the ASGI server)
-   ``prodserver`` uses Uvicorn/Hypercorn instead of Daphne
-   update_my_code has been removed

Version 2.2
===========

-   support for the ``otreezip`` format
    (``otree zip``, ``otree unzip``)
-   MTurk: in sandbox mode, don't grant qualifications
    or check qualification requirements
-   MTurk: before paying participants, check if there is adequate
    account balance.
-   "next button" is disabled after clicking, to prevent congesting the server
    with duplicate page loads.
-   Upgrade to the latest version of Sentry
-   Form validation methods should go on the model, not the page.
    See :ref:`dynamic_validation`
-   :ref:`app_after_this_page`
-   Various performance and stability improvements

.. _v21:

Version 2.1
===========

-   oTree now raises an error if you use an undefined variable in your template.
    This will help catch typos like
    ``{{ Player.payoff }}`` or ``{{ if player.id_in_gruop }}``.
    This means that apps that previously worked may now get a template error
    (previously, it failed silently).
    If you can't remove the offending variable,
    you can apply the ``|default`` filter, like: ``{{ my_undefined_variable|default:None }}``
-   oTree now warns you if you use an invalid attribute on a Page/WaitPage.
-   CSV/Excel data export is done asynchronously, which will fix
    timeout issues for large files on Heroku.
-   Better performance, especially for "Monitor" and "Data" tab in admin interface
