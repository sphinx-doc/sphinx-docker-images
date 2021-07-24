FROM fedora
LABEL maintainer="Sphinx Team <https://www.sphinx-doc.org/>"

WORKDIR /docs
RUN echo -e 'assumeyes=True\ninstall_weak_deps=False\ntsflags=nodocs' >> /etc/dnf/dnf.conf \
    # Install latex with Chinese support
    && dnf in make latexmk texlive-{xetex,xindy,cmap,xecjk,gnu-freefont,fncychap,wrapfig,capt-of,framed,upquote,needspace,tabulary,parskip,fandol}\
       pip \
    && pip --no-cache-dir install setuptools
    && pip install --no-cache-dir Sphinx Pillow
    && dnf autoremove \
    && dnf clean all

CMD ["make", "latexpdf"]
