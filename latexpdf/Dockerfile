FROM python:slim
LABEL maintainer="Sphinx Team <https://www.sphinx-doc.org/>"

WORKDIR /docs
RUN apt-get update \
 && apt-get install -y \
      graphviz \
      imagemagick \
      make \
      \
      latexmk \
      lmodern \
      texlive-latex-recommended \
      texlive-latex-extra \
      texlive-fonts-recommended \
      texlive-fonts-extra \
      texlive-lang-cjk \
      texlive-lang-japanese \
      texlive-luatex \
      texlive-xetex \
 && apt-get autoremove \
 && apt-get clean

RUN python3 -m pip install -U pip
RUN python3 -m pip install Sphinx==2.4.3 Pillow

CMD ["make", "latexpdf"]
