FROM alpine:3.9

RUN set -ex \
 && apk add --no-cache --virtual .build-deps \
    curl \
    ghostscript \
    perl \
 && mkdir /tmp/install-tl-unx \
 && wget -qO- http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz | tar zx -C /tmp/install-tl-unx --strip-components=1 \
 && echo selected_scheme scheme-basic >> /tmp/install-tl-unx/texlive.profile \
 && echo collection-fontsrecommended 1 >> /tmp/install-tl-unx/texlive.profile \
 && echo collection-latexrecommended 1 >> /tmp/install-tl-unx/texlive.profile \
 && echo collection-langjapanese 1 >> /tmp/install-tl-unx/texlive.profile \
 && echo instopt_adjustpath 1 >> /tmp/install-tl-unx/texlive.profile \
 && echo tlpdbopt_install_docfiles 0 >> /tmp/install-tl-unx/texlive.profile \
 && echo tlpdbopt_install_srcfiles 0 >> /tmp/install-tl-unx/texlive.profile \
 && /tmp/install-tl-unx/install-tl --profile /tmp/install-tl-unx/texlive.profile \
 && rm -rf /tmp/install-tl-unx \
 # Setup for Hiragino fonts
 && tlmgr repository add http://contrib.texlive.info/current tlcontrib \
 && tlmgr pinning add tlcontrib '*' \
 && tlmgr install \
    japanese-otf-nonfree \
    japanese-otf-uptex-nonfree \
    ptex-fontmaps-macos \
    cjk-gs-integrate-macos \
 && mkdir -p /System/Library/Fonts \
 && touch '/System/Library/Fonts/ヒラギノ明朝 ProN.ttc' \
 && touch '/System/Library/Fonts/ヒラギノ丸ゴ ProN W4.ttc' \
 && touch '/System/Library/Fonts/ヒラギノ角ゴシック W0.ttc' \
 && touch '/System/Library/Fonts/ヒラギノ角ゴシック W1.ttc' \
 && touch '/System/Library/Fonts/ヒラギノ角ゴシック W2.ttc' \
 && touch '/System/Library/Fonts/ヒラギノ角ゴシック W3.ttc' \
 && touch '/System/Library/Fonts/ヒラギノ角ゴシック W4.ttc' \
 && touch '/System/Library/Fonts/ヒラギノ角ゴシック W5.ttc' \
 && touch '/System/Library/Fonts/ヒラギノ角ゴシック W6.ttc' \
 && touch '/System/Library/Fonts/ヒラギノ角ゴシック W7.ttc' \
 && touch '/System/Library/Fonts/ヒラギノ角ゴシック W8.ttc' \
 && touch '/System/Library/Fonts/ヒラギノ角ゴシック W9.ttc' \
 && mkdir -p /usr/local/texlive/texmf-local/fonts/opentype/hiragino-highsierra-pron \
 && ln -s '/System/Library/Fonts/ヒラギノ明朝 ProN.ttc' /usr/local/texlive/texmf-local/fonts/opentype/hiragino-highsierra-pron/HiraginoSerif.ttc \
 && ln -s '/System/Library/Fonts/ヒラギノ丸ゴ ProN W4.ttc' /usr/local/texlive/texmf-local/fonts/opentype/hiragino-highsierra-pron/HiraginoSansR-W4.ttc \
 && ln -s '/System/Library/Fonts/ヒラギノ角ゴシック W0.ttc' /usr/local/texlive/texmf-local/fonts/opentype/hiragino-highsierra-pron/HiraginoSans-W0.ttc \
 && ln -s '/System/Library/Fonts/ヒラギノ角ゴシック W1.ttc' /usr/local/texlive/texmf-local/fonts/opentype/hiragino-highsierra-pron/HiraginoSans-W1.ttc \
 && ln -s '/System/Library/Fonts/ヒラギノ角ゴシック W2.ttc' /usr/local/texlive/texmf-local/fonts/opentype/hiragino-highsierra-pron/HiraginoSans-W2.ttc \
 && ln -s '/System/Library/Fonts/ヒラギノ角ゴシック W3.ttc' /usr/local/texlive/texmf-local/fonts/opentype/hiragino-highsierra-pron/HiraginoSans-W3.ttc \
 && ln -s '/System/Library/Fonts/ヒラギノ角ゴシック W4.ttc' /usr/local/texlive/texmf-local/fonts/opentype/hiragino-highsierra-pron/HiraginoSans-W4.ttc \
 && ln -s '/System/Library/Fonts/ヒラギノ角ゴシック W5.ttc' /usr/local/texlive/texmf-local/fonts/opentype/hiragino-highsierra-pron/HiraginoSans-W5.ttc \
 && ln -s '/System/Library/Fonts/ヒラギノ角ゴシック W6.ttc' /usr/local/texlive/texmf-local/fonts/opentype/hiragino-highsierra-pron/HiraginoSans-W6.ttc \
 && ln -s '/System/Library/Fonts/ヒラギノ角ゴシック W7.ttc' /usr/local/texlive/texmf-local/fonts/opentype/hiragino-highsierra-pron/HiraginoSans-W7.ttc \
 && ln -s '/System/Library/Fonts/ヒラギノ角ゴシック W8.ttc' /usr/local/texlive/texmf-local/fonts/opentype/hiragino-highsierra-pron/HiraginoSans-W8.ttc \
 && ln -s '/System/Library/Fonts/ヒラギノ角ゴシック W9.ttc' /usr/local/texlive/texmf-local/fonts/opentype/hiragino-highsierra-pron/HiraginoSans-W9.ttc \
 && cjk-gs-integrate --fontdef-add cjkgs-macos-highsierra.dat \
 && kanji-config-updmap-sys --jis2004 hiragino-highsierra-pron \
 && mktexlsr \
 && rm -f /System/Library/Fonts/*.ttc \
 && apk del .build-deps
