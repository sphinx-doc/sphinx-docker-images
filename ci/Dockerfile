FROM ubuntu:24.04

ENV DEBIAN_FRONTEND=noninteractive
ENV LANG C.UTF-8
ENV TERM xterm
RUN apt-get update \
 && apt-get upgrade -y \
 && apt-get install -y \
       build-essential \
       dvipng \
       epubcheck \
       git \
       gettext \
       graphviz \
       imagemagick \
       make \
       lmodern \
       openjdk-11-jre-headless \
       python3-venv \
       python3-pip \
       python3-dev \
       texlive-latex-recommended \
       texlive-latex-extra \
       texlive-fonts-recommended \
       tex-gyre \
       texlive-fonts-extra \
       texlive-luatex \
       texlive-xetex \
 && apt-get autoremove \
 && apt-get clean

RUN mkdir /sphinx
WORKDIR /sphinx
