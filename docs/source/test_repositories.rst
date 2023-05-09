.. SciXTemplatePipeline documentation master file, created by
   sphinx-quickstart on Tue May  2 15:24:55 2023.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

SciXTemplatePipeline
================================================

.. toctree::
   :maxdepth: 2
   :caption: Contents

   SciXTEMPLATE



.. role:: raw-html-m2r(raw)
   :format: html



.. image:: https://github.com/tjacovich/SciXTemplateRepository/actions/workflows/python_actions.yml/badge.svg
   :target: https://github.com/tjacovich/SciXTemplateRepository/actions/workflows/python_actions.yml
   :alt: Python CI actions

.. image:: https://coveralls.io/repos/github/tjacovich/SciXTemplateRepository/badge.svg?branch=main
   :target: https://coveralls.io/github/tjacovich/SciXTemplateRepository?branch=main
   :alt: Coverage Status


The Template Test Environment
====================================

The Template API Tests
---------------------------------

Running ``gRPC`` tests currently requires implementing a fake gRPC server. To save some pain in that regard, the ``tests/API/test_template_server.py`` file contains a full mock server that is instantiated when ``pytest`` is run and torn down when all the tests in ``TemplateServer`` have completed.

.. code-block:: bash

   virtualenv .venv
   source .venv/bin/activate
   pip install .[dev]
   pip install .
   pre-commit install
   pre-commit install --hook-type commit-msg


Maintainers
-----------

First Last

Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
