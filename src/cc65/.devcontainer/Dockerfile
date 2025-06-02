# See here for image contents: https://github.com/devcontainers/images/blob/main/src/base-alpine/.devcontainer/Dockerfile

# [Choice] Alpine version: 3.16, ..., 3.20
ARG VARIANT="3.20"
FROM mcr.microsoft.com/vscode/devcontainers/base:alpine-${VARIANT}

ARG CC65_VERSION=latest

RUN mkdir -p /usr/src && cd /usr/src && \
    git clone https://github.com/cc65/cc65.git && cd cc65 && \
    if [ "${CC65_VERSION}" != "latest" ]; then \
       git checkout tags/V${CC65_VERSION} -b "tag-${CC65_VERSION}"; \
    fi && \
    nice make -j2 && make install PREFIX=/usr prefix=/usr && \
    rm -rf /usr/src/cc65
