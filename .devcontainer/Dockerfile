FROM docker.io/texlive/texlive:latest

# Avoid interactive prompts during Docker build
ARG DEBIAN_FRONTEND=noninteractive

# Set the working directory inside the container
WORKDIR /workspace

# Set up the CTAN repository mirror
RUN tlmgr option repository https://mirrors.cloud.tencent.com/CTAN/systems/texlive/tlnet

# Install latexmk via tlmgr
RUN tlmgr install latexmk || true

# Install system dependencies first
RUN apt-get update && apt-get install -y --no-install-recommends \
    wget \
    perl \
    fontconfig \
    ca-certificates \
    cabextract \
    xfonts-utils \
    fonts-khmeros \
    fonts-noto-core \
    fonts-noto-extra \
    && rm -rf /var/lib/apt/lists/*

# Enable Debian contrib repository because ttf-mscorefonts-installer is in contrib
RUN if [ -f /etc/apt/sources.list ]; then \
      sed -i 's/ main$/ main contrib/g' /etc/apt/sources.list || true; \
    fi && \
    if [ -d /etc/apt/sources.list.d ]; then \
      find /etc/apt/sources.list.d -name "*.sources" -exec \
      sed -i 's/Components: main/Components: main contrib/g' {} \; || true; \
    fi

# Accept Microsoft Core Fonts EULA and install Times New Roman
RUN echo "ttf-mscorefonts-installer msttcorefonts/accepted-mscorefonts-eula select true" | debconf-set-selections \
    && apt-get update \
    && apt-get install -y --no-install-recommends ttf-mscorefonts-installer \
    && fc-cache -f -v \
    && rm -rf /var/lib/apt/lists/*

# Copy project files into the container
COPY . /workspace