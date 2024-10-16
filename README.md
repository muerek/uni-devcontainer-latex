# Devcontainer for LaTeX

This is a LaTeX environment packaged into a Docker container.
Use this as a starting point for writing documents in LaTeX.

## What it contains

This repository contains these elements:

- A Dockerfile with instructions to install MikTeX on a Debian devcontainer image provided by Microsoft.
- A devcontainer definition referencing that Dockerfile and instructing VS Code to install the required LaTeX extension.
- Configuration settings for the VS Code LaTeX extension to store all output in a separate `./out` folder.
- A gitignore file to ignore all content of that output folder

## How to use

For your initial setup, follow these steps:

1. Clone this repository to your machine.
2. Open the folder with VS Code.
3. When prompted, trust the contents of this folder.
4. When prompted, click "Open in container".
5. Wait while VS Code downloads the image and initializes the container.

If your LaTeX file references any packages, watch out for MikTeX prompts.
MikTeX will ask for your confirmation before installing packages.

You can open the MikTeX configuration panel by opening a new Terminal in VS Code and typing `mpm`.

## Why use this setup?

*Why a local LaTeX setup?* - This setup works offline and you can use Git for free. While Overleaf hides a lot of complexity for you, I have encountered connection issues and found it quite expensive just to get Git versioning for my files.

*Why containerize it?* - I want to keep my local machine clean. The installation instructions for LaTeX distributions did not read like they were lightweight and isolated pieces of software, but rather huge and messy.

*Why MikTeX on Linux?* - MikTeX downloads packages on the fly. This seemed like the most user-friendly and sensible option to me. I do not want to modify my devcontainer definition just to install a package or dump several gigabytes of packages on my machine just-in-case like recommended for other LaTeX distributions.

## System requirements and caveats

I have tested this setup with the following system:

- Windows 11 23H2 on x64
- WSL 2 enabled
- Docker Desktop 4.29.0
- VS Code 1.94.2

Possible limitations on other systems:

- I am not sure how/if the Dockerfile works on ARM-based platforms.
- I am not sure how/if the MikTeX prompts are rendered on non-WSL Docker backends.

## Disclaimer

Please note: I am no expert on LaTeX or how to set up a LaTeX environment. I have not found a good, recent or comprehensive explanation for setting up LaTeX in a container in the internet, so this is what I put together myself. I may be completely wrong on some points.