FROM mcr.microsoft.com/devcontainers/jekyll

# Work around stale Yarn apt key in upstream image and install project dependencies.
RUN rm -f /etc/apt/sources.list.d/yarn.list /etc/apt/sources.list.d/yarn*.list \
    && apt-get update \
    && apt-get install -y --no-install-recommends \
        build-essential \
        imagemagick \
        inotify-tools \
        jupyter-nbconvert \
        procps \
        ruby-full \
        zlib1g-dev \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
