# docker-sphinx

Docker images for [Sphinx](https://www.sphinx-doc.org/).

## Images

* sphinxdoc/sphinx
* sphinxdoc/sphinx-latexpdf

Note:

``sphinxdoc/sphinx-latexpdf`` contains TeXLive packages. So the image is very large (over 2GB!).

## Usage

Create a Sphinx project::

```bash
$ docker run --rm -v /path/to/document:/docs sphinxdoc/sphinx sphinx-quickstart
```

Build HTML document::

```bash
$ docker run --rm -v /path/to/document:/docs sphinxdoc/sphinx make html
```

Build EPUB document::

```bash
$ docker run --rm -v /path/to/document:/docs sphinxdoc/sphinx make epub
```

Build PDF document::

```bash
$ docker run --rm -v /path/to/document:/docs sphinxdoc/sphinx-latexpdf make latexpdf
```

## Tips

If you would like to install dependencies, use ``sphinxdoc/sphinx`` as a base image::

```dockerfile
# in your Dockerfile
FROM sphinxdoc/sphinx

WORKDIR /docs
ADD requirements.txt /docs
RUN pip3 install -r requirements.txt
```
