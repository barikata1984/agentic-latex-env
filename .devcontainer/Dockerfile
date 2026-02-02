FROM mcr.microsoft.com/devcontainers/base:ubuntu-24.04

# Pixi のインストール
COPY --from=ghcr.io/prefix-dev/pixi:latest /usr/local/bin/pixi /usr/local/bin/pixi

WORKDIR /workspace

ENV LANG=C.UTF-8 \
    LC_ALL=C.UTF-8

# 【重要】TeXLive は apt でインストールする (Conda版は古くて不安定なため)
# texlive-full は巨大なので、必要なセットに絞っていますが、
# 容量を気にしないなら texlive-full 一発でもOKです。
RUN apt-get update && apt-get install -y \
    texlive-latex-base \
    texlive-latex-extra \
    texlive-science \
    texlive-lang-japanese \
    texlive-fonts-recommended \
    texlive-fonts-extra \
    latexmk \
    biber \
    && rm -rf /var/lib/apt/lists/*

# Pixi のシェル補完
RUN echo 'eval "$(pixi completion --shell bash)"' >> /home/vscode/.bashrc