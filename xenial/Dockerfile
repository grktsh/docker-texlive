FROM ubuntu:16.04

RUN apt-get update && apt-get install -y --no-install-recommends \
    texlive \
    texlive-fonts-extra \
    texlive-lang-japanese \
    texlive-latex-extra \
    texlive-luatex \
    texlive-pictures \
    texlive-xetex \
    lmodern \
 && rm -rf /var/lib/apt/lists/*

VOLUME /root/.texmf-var
VOLUME /var/lib/texmf/luatex-cache
