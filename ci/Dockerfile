FROM ubuntu:bionic
MAINTAINER i.tkomiya@gmail.com

ENV DEBIAN_FRONTEND=noninteractive
ENV LANG C.UTF-8
ENV TERM xterm
RUN apt-get update \
  && apt-get upgrade -y \
  && apt-get install -y \
       build-essential \
       epubcheck \
       git \
       gettext \
       graphviz \
       imagemagick \
       make \
       lmodern \
       openjdk-11-jre-headless \
       python-virtualenv \
       python3-pip \
       python3-dev \
       texlive-latex-recommended \
       texlive-latex-extra \
       texlive-fonts-recommended \
       texlive-fonts-extra \
       texlive-luatex \
       texlive-xetex \
  && apt-get autoremove \
  && apt-get clean

# Install test dependencies
RUN virtualenv -p python3.6 /python3.6 \
  && /python3.6/bin/pip install "Sphinx[test,websupport]" \
  && /python3.6/bin/pip uninstall -y Sphinx

RUN mkdir /repos /sphinx
WORKDIR /sphinx
