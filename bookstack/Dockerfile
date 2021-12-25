FROM ubuntu

ENV TZ=Asia/Shanghai DEBIAN_FRONTEND=noninteractive

ARG VERSION=2.10
ARG buildDeps="wget python unzip software-properties-common"
ARG runDeps="ttf-wqy-zenhei fonts-wqy-microhei chromium-browser git"
ARG downloadUrl="https://gitee.com/truthhun/BookStack/attach_files/870796/download/BookStack-v2.10_Linux_amd64.zip"

RUN set -x \
    && apt update \
    && apt install -y ${buildDeps} \
    && echo -e "\n" | add-apt-repository ppa:saiarcot895/chromium-beta \
    && apt install -y ${runDeps} \
    && wget -nv -O- https://download.calibre-ebook.com/linux-installer.py | python -c "import sys; main=lambda:sys.stderr.write('Download failed\n'); exec(sys.stdin.read()); main()" 
    

RUN wget -O BookStack.zip "${downloadUrl}" \
    && mkdir -p /usr/local/bookstack \
    && unzip -d /usr/local/bookstack BookStack.zip \
    && rm BookStack.zip \
    && apt purge -y --auto-remove ${buildDeps} \
    && chmod +x /usr/local/bookstack/BookStack

CMD cd /usr/local/bookstack \
    && ./BookStack install \
    && ./BookStack


EXPOSE 8181