# Data Science Playground

[![License](https://img.shields.io/badge/license-MIT-green)](./LICENSE)

Quick start environment for data science.

## Getting started

You're going to need the following software components to get started:

* [Visual Studio Code](https://code.visualstudio.com/) - comprehensive IDE supporting dev containers
* [Docker Desktop](https://www.docker.com/products/docker-desktop/) - leading container engine
* Docker extension for VSCode - support for Docker from VSCode
* Dev Containers extension for VSCode - support for development environments in VSCode

## System configuration

The devcontainer is built on [Arch Linux](https://archlinux.org/). The following key assumptions
were made:

* The environment container is unprivileged
* The container is operated by `vscode` user (`GID` = `UID` = `1000`)
* The container binds to hosts `/var/run/docker.sock` socket to allow interaction with Docker on
the host
* The directory with codebase is mounted under `/workspace`, which is NOT the user directory
(`/home/vscode` is)
* Python uses virtual environment which is owned by `vscode`
* The name of the virtual environment is `.env`

## System packages and supporting VSCode extensions

The following packages, site packages and extensions are installed:

* Python + Pylance + IntelliSense for Python
* PIP package manager
* Jupyther notebooks support
* CSV formatter
* Markdown linting
* Git + Git Graph extension
* GitHub Actions extension
* GitHub CoPilot extension
* Docker extension + socket binding (Docker from Docker)
* `sudo` for DevContainer continuous improvement

## Domain specific packages

The following site packages were pre-installed in a Python virtual environment:

* `jupyter`
* `ipykernel`
* `matplotlib`
* `numpy`
* `pandas`
* `scikit-learn`
* `seaborn`
* `keras`
* `tensorflow`
