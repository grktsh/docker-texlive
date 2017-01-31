# docker-texlive

Dockerfiles for Tex Live.

## Usage

Build:

```
docker build -t grktsh/texlive:xenial .
```

To use upLaTeX:

```console
docker run -it --rm -v $(pwd):/work -w /work grktsh/texlive:xenial ptex2pdf -u -l example
```

To use LuaTeX-ja:

```console
docker create -v /root/.texmf-var -v /var/lib/texmf/luatex-cache --name texlive-data grktsh/texlive:xenial /bin/true
docker run -it --rm -v $(pwd):/work -w /work --volumes-from texlive-data grktsh/texlive:xenial lualatex example
```
