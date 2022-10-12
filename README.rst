=========================
Docker Images for Sphinx_
=========================

Images
======

- ``sphinx`` --
  Main Sphinx image --
  `Docker Hub <https://hub.docker.com/r/sphinxdoc/sphinx>`__,
  `GitHub Container Registry <https://github.com/sphinx-doc/docker/pkgs/container/sphinx>`__
- ``sphinx-latexpdf`` --
  Image for LaTeX --
  `Docker Hub <https://hub.docker.com/r/sphinxdoc/sphinx-latexpdf>`__,
  `GitHub Container Registry <https://github.com/sphinx-doc/docker/pkgs/container/sphinx-latexpdf>`__

.. note:: The ``sphinx-latexpdf`` container contains TeXLive images, meaning it
          is very large (over 2GB).

Usage
=====

Create a Sphinx project:

.. code:: bash

   $ docker run -it --rm -v /path/to/document:/docs sphinxdoc/sphinx sphinx-quickstart

Build HTML document:

.. code:: bash

   $ docker run --rm -v /path/to/document:/docs sphinxdoc/sphinx make html

Build EPUB document:

.. code:: bash

   $ docker run --rm -v /path/to/document:/docs sphinxdoc/sphinx make epub

Build PDF document:

.. code:: bash

   $ docker run --rm -v /path/to/document:/docs sphinxdoc/sphinx-latexpdf make latexpdf

Tips
====

To install additional dependencies, use ``sphinxdoc/sphinx`` as a base image:

.. code:: dockerfile

   # in your Dockerfile
   FROM sphinxdoc/sphinx

   WORKDIR /docs
   ADD requirements.txt /docs
   RUN pip3 install -r requirements.txt

Sphinx CI Docker Image
======================

The Docker image used for testing Sphinx_ in continuous integration is defined
in the ``ci`` directory.

.. _Sphinx: http://www.sphinx-doc.org/
