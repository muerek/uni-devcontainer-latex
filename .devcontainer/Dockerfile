FROM mcr.microsoft.com/devcontainers/base:bullseye as miktex

# Install MikTeX.
# VSCode LaTeX Workshop + MikTeX require Perl, this is already installed in this image.
WORKDIR /tmp/miktex
USER root
RUN curl -fsSL https://miktex.org/download/key | sudo tee /usr/share/keyrings/miktex-keyring.asc > /dev/null && \
    echo "deb [signed-by=/usr/share/keyrings/miktex-keyring.asc] https://miktex.org/download/debian bullseye universe" | sudo tee /etc/apt/sources.list.d/miktex.list && \
    sudo apt-get update && \
    sudo apt-get install -y miktex

# Finish setup and enable automatic package download.
RUN miktexsetup finish && initexmf --set-config-value [MPM]AutoInstall=1
# Install packages to avoid babel package hyphenation error for German.
RUN mpm --install hyph-utf8 && mpm --install dehyph-exptl

# Find executables and add them to PATH.
RUN echo "export PATH=/new/path:${PATH}" >> /root/.bashrc
ENV PATH "$PATH:/new/path"