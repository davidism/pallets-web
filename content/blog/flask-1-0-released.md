~~~~toml
title = "Flask 1.0 Released"
author_name = "David Lord"
published = 2018-04-26
tags = ["security", "releases"]
~~~~

The Pallets team is pleased to release [Flask](https://palletsprojects.com/p/flask/) 1.0.

The Flask framework has been stable for a long time. A little more than 8 years after the first commit, the version number finally reflects that. 1.0 comes with a significant number of changes representing over a year of work.

*   Dropped support for Python 2.6 and 3.3.
*   The CLI is more flexible. ``FLASK_APP`` can point to an app factory, optionally with arguments. It understands import names in more cases where filenames were previously used. It automatically detects common filenames, app names, and factory names. ``FLASK_ENV`` describes the environment the app is running in, like ``development``, and replaces ``FLASK_DEBUG`` in most cases. [See the docs to learn more.](http://flask.pocoo.org/docs/1.0/cli/)
*   If python-dotenv is installed, the ``flask`` CLI will load environment variables from ``.flaskenv`` and ``.env`` files rather than having to export them in each new terminal.
*   The development server is multi-threaded by default to handle concurrent requests during development.
*   ``flask.ext``, which was previously deprecated, is completely removed. Import extensions by their actual package names.
*   Accessing missing keys from ``request.form`` shows a more helpful error message in debug mode, addressing a very common source of confusion for developers.
*   Error handlers are looked up by code then exception class, on the blueprint then application. This gives more predictable control over handlers, including being able to handle ``HTTPException``.
*   The behavior of ``app.logger`` has been greatly simplified and should be much easier to customize. The logger is always named ``flask.app``, it only adds a handler if none are registered, and it never removes existing handlers. [See the docs to learn more.](http://flask.pocoo.org/docs/1.0/logging/)
*   The ``test_client`` gained a ``json`` argument for posting JSON data, and the ``Response`` object gained a ``get_json`` method to decode the data as JSON in tests.
*   A new ``test_cli_runner`` is added for testing an app's CLI commands.
*   Many documentation sections have been rewritten to improve clarity and relevance. This is an ongoing effort.
*   The [tutorial](http://flask.pocoo.org/docs/1.0/tutorial/) and corresponding [example](https://github.com/pallets/flask/tree/1.0/examples/tutorial) have been rewritten. They use a structured layout and go into more detail about each aspect in order to help new users avoid common issues and become comfortable with Flask.

There are many more changes throughout the framework. [Read the full changelog](http://flask.pocoo.org/docs/1.0/changelog/) to understand what changes may affect your code when upgrading.


JSON Security Fix