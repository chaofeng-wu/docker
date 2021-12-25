FROM ubuntu

ENV TZ=Asia/Shanghai DEBIAN_FRONTEND=noninteractive

ARG VERSION=2.10

RUN set -x; buildDeps='wget python unzip nodejs npm'; runDeps='ttf-wqy-zenhei fonts-wqy-microhei chromium-browser git' \
    && apt update \
    && apt install -y $runDeps \
    && apt install -y $buildDeps \
    && npm install -g cnpm && cnpm install puppeteer \
    && wget -O BookStack.zip "https://github.com/TruthHun/BookStack/releases/download/v${VERSION}/BookStack-v${VERSION}_Linux_amd64.zip" \
    && mkdir -p /usr/local/bookstack \
    && unzip -d /usr/local/bookstack BookStack.zip \
    && rm BookStack.zip \
    && wget -nv -O- https://download.calibre-ebook.com/linux-installer.py | python -c "import sys; main=lambda:sys.stderr.write('Download failed\n'); exec(sys.stdin.read()); main()" \
    && apt purge -y --auto-remove $buildDeps \
    && chmod +x /usr/local/bookstack/BookStack \
    && cd /usr/local/bookstack \
    && ./BookStack install \
    && ./BookStack


EXPOSE 8181