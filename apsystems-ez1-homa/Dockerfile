# https://developers.home-assistant.io/docs/add-ons/configuration#add-on-dockerfile
ARG BUILD_ARCH=amd64
ARG BUILD_FROM=ghcr.io/home-assistant/amd64-base-python:latest
FROM $BUILD_FROM

ENV LOG_TIMESTAMP="%Y-%m-%d %T"

RUN echo "alias l='ls --color=auto -alF'" >> /root/.bashrc

# Install dependencies
RUN apk update && \
    apk add --no-cache poetry git make && \
    mkdir -p /usr/local/src && \
    git -C /usr/local/src clone --depth 1 --branch main https://github.com/hass-hmueller01/hass-addon-helper.git

# Copy root filesystem
COPY rootfs /

# Build the Python virtual environment for the service
RUN \
    cd /usr/local/src/hass-addon-helper && \
    git pull && \
    make install && \
    cd /etc/services.d/apsystems-ez1 && \
    python3 -m venv .venv && \
    source .venv/bin/activate && \
    poetry install

# Cleanup
RUN apk del --rdepends poetry make && \
    apk cache clean && \
    rm -rf /var/cache/apk/* /tmp/* /root/.cache/pip

ENTRYPOINT ["/init"]
