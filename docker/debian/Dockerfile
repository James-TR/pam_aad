FROM debian:9.7
ARG VERSION
ARG DEBVER

RUN echo "deb http://http.us.debian.org/debian sid main" \
        >> /etc/apt/sources.list && \
    apt update && apt install -y \
        automake \
        build-essential \
        curl \
        debhelper \
        devscripts \
        git \
        indent \
        libcurl4-openssl-dev \
        libjansson-dev \
        libjwt-dev \
        libpam0g-dev \
        libssl-dev \
        libtool \
        pkg-config \
        quilt \
        uuid-dev

WORKDIR /usr/src/pam_aad
COPY . /usr/src/pam_aad
RUN tar cvzf "../pam-aad_${VERSION}.orig.tar.gz" --exclude='.git*' . && \
    debuild -us -uc -d -i'(.*)' && \
    dpkg -i "../libpam-aad_${VERSION}-${DEBVER}_amd64.deb"
