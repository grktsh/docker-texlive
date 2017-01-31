FROM grktsh/texlive:xenial

COPY fonts /usr/share/texmf/fonts/opentype/hiragino-pron/

RUN mktexlsr \
 && kanji-config-updmap-sys --jis2004 hiragino-pron \
 && luaotfload-tool -u -v
