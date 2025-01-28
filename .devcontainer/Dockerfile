FROM mcr.microsoft.com/vscode/devcontainers/base:ubuntu
LABEL org.opencontainers.image.authors="jennyl.smith12@gmail.com"

# update packages and install dependencies
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
    build-essential gfortran \
    zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev \
    libssl-dev libreadline-dev libffi-dev \
    wget xorg openbox

# install python and venv
ENV PY_VERSION='3.12'
RUN apt-get -y install --no-install-recommends \
    software-properties-common && \
    add-apt-repository ppa:deadsnakes/ppa && \
    apt-get -y install python${PY_VERSION} python${PY_VERSION}-venv

# install R
ENV R_VERSION='4.1.2-1ubuntu2'
RUN wget -qO- https://cloud.r-project.org/bin/linux/ubuntu/marutter_pubkey.asc | sudo tee -a /etc/apt/trusted.gpg.d/cran_ubuntu_key.asc
RUN apt install r-base r-base-dev -y

# install quarto
ENV QUARTO_VER='1.7.13'
RUN wget -P /opt https://github.com/quarto-dev/quarto-cli/releases/download/v${QUARTO_VER}/quarto-${QUARTO_VER}-linux-arm64.tar.gz && tar -xzf /opt/quarto-${QUARTO_VER}-linux-arm64.tar.gz -C /opt
ENV PATH=$PATH:/opt/quarto-${QUARTO_VER}/bin

# install R package renv
# See Ubuntu repos for more packages that can be installed through apt manager: 
# https://cloud.r-project.org/bin/linux/ubuntu/
RUN wget https://github.com/rstudio/renv/archive/refs/tags/v1.0.11.tar.gz && \
    R CMD INSTALL v1.0.11.tar.gz && \
    rm -rf v1.0.11.tar.gz


##### Compiling from source takes a LONG time (> 10 min)
# Download and install Python from source
# WORKDIR /opt/Python-${PY_VERSION}
# RUN wget "https://www.python.org/ftp/python/${PY_VERSION}/Python-${PY_VERSION}.tgz" && tar -xf Python-${PY_VERSION}.tgz 
# RUN cd "Python-${PY_VERSION}" && ./configure --enable-optimizations && make install 

# Download and install R from source
# WORKDIR /opt/R-${R_VERSION}
# RUN wget https://cran.r-project.org/src/base/R-4/R-${R_VERSION}.tar.gz && tar -xf R-${R_VERSION}.tar.gz
# RUN cd "R-${R_VERSION}" && ./configure && make

# Clean up files
# WORKDIR /opt
# RUN rm -rf /opt/Python-${PY_VERSION} /opt/R-${R_VERSION}

