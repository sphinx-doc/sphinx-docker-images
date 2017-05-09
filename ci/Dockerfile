FROM ubuntu:trusty
MAINTAINER i.tkomiya@gmail.com

ENV LANG C.UTF-8
ENV TERM xterm
RUN apt-get update \
  && apt-get upgrade -y \
  && apt-get install -y \
       build-essential \
       git \
       gettext \
       imagemagick \
       make \
       lmodern \
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
RUN curl -LO https://raw.githubusercontent.com/sphinx-doc/sphinx/master/test-reqs.txt
RUN virtualenv -p python3.4 /python3.4 \
  && /python3.4/bin/pip install -r test-reqs.txt

RUN mkdir /repos /sphinx
WORKDIR /sphinx
CMD git clone /repos /sphinx \
  && /python3.4/bin/pip install -U -r test-reqs.txt \
  && make test PYTHON=/python3.4/bin/python
