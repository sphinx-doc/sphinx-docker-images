FROM ubuntu:trusty
MAINTAINER i.tkomiya@gmail.com

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
       openjdk-7-jre-headless \
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
RUN curl -LO https://raw.githubusercontent.com/sphinx-doc/sphinx/stable/test-reqs.txt
RUN virtualenv -p python3.4 /python3.4 \
  && /python3.4/bin/pip install -r test-reqs.txt

RUN mkdir /repos /sphinx
WORKDIR /sphinx
