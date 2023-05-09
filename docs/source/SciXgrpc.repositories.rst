.. SciXTemplatePipeline documentation master file, created by
   sphinx-quickstart on Tue May  2 15:24:55 2023.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

The gRPC Backend
====================================

.. toctree::
   :maxdepth: 2
   :caption: Contents

.. role:: raw-html-m2r(raw)
   :format: html



.. image:: https://github.com/tjacovich/SciXTemplateRepository/actions/workflows/python_actions.yml/badge.svg
   :target: https://github.com/tjacovich/SciXTemplateRepository/actions/workflows/python_actions.yml
   :alt: Python CI actions

.. image:: https://coveralls.io/repos/github/tjacovich/SciXTemplateRepository/badge.svg?branch=main
   :target: https://coveralls.io/github/tjacovich/SciXTemplateRepository?branch=main
   :alt: Coverage Status



The Template gRPC API
---------------------------------

Because we are using ``AVRO`` instead of ``protobufs``, we cannot take advantage of the automatic API generation that ``gRPC`` offers. To help defray some of the cost of manually creating the API code, we have included some boilerplate code that initializes an ``INIT`` method, as well as a ``MONITOR`` method.

Maintainers
-----------

First Last

Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
