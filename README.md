# docker-texlive

## Usage

```console
docker run --rm -v /System/Library/Fonts:/System/Library/Fonts:ro -v $(pwd):/work -w /work grktsh/texlive:ja ptex2pdf -l -u example
```
