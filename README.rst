=========================
Docker Images for Sphinx_
=========================

Images
======

- ``sphinx`` --
  Main Sphinx image --
  `Docker Hub <https://hub.docker.com/r/sphinxdoc/sphinx>`__,
  `GitHub Container Registry <https://ghcr.io/sphinx-doc/sphinx>`__
- ``sphinx-latexpdf`` --
  Image for LaTeX --
  `Docker Hub <https://hub.docker.com/r/sphinxdoc/sphinx-latexpdf>`__,
  `GitHub Container Registry <https://ghcr.io/sphinx-doc/sphinx-latexpdf>`__

.. note:: The ``sphinx-latexpdf`` container contains TeXLive images,
          meaning it is very large (over 2GiB).

Usage
=====

Create a Sphinx project:

.. code:: bash

   $ docker run -it --rm -v /path/to/document:/docs sphinxdoc/sphinx sphinx-quickstart

Build HTML document:

.. code:: bash

   $ docker run --rm -v /path/to/document:/docs sphinxdoc/sphinx sphinx-build -M html . _build

Build EPUB document:

.. code:: bash

   $ docker run --rm -v /path/to/document:/docs sphinxdoc/sphinx sphinx-build -M epub . _build

Build PDF document:

.. code:: bash

   $ docker run --rm -v /path/to/document:/docs sphinxdoc/sphinx-latexpdf sphinx-build -M latexpdf . _build

Tips
====

To install additional dependencies, use ``sphinxdoc/sphinx`` as a base image:

.. code:: dockerfile

   # in your Dockerfile
   FROM sphinxdoc/sphinx

   WORKDIR /docs
   ADD requirements.txt /docs
   RUN python3 -m pip install -r requirements.txt

Sphinx CI Docker Image
======================

The Docker image used for testing Sphinx_ in continuous integration is defined
in the ``ci`` directory.

.. _Sphinx: http://www.sphinx-doc.org/
