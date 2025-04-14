FROM mcr.microsoft.com/vscode/devcontainers/base:ubuntu
LABEL org.opencontainers.image.authors="jennyl.smith12@gmail.com"

# software versions for project dependencies 
ENV PY_VERSION='3.12'

ENV QUARTO_VER='1.7.13'
ENV QUARTO_ARCH='arm64'

ENV R_VERSION='4.1.2-1ubuntu2'
ENV RENV_VER='1.0.11'

# location for dependencies
ENV DIR='/opt'

# update packages and install dependencies
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
    build-essential gfortran \
    zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev \
    libssl-dev libreadline-dev libffi-dev \
    wget xorg openbox gh

# install python and venv
RUN apt-get -y install --no-install-recommends \
    software-properties-common && \
    add-apt-repository ppa:deadsnakes/ppa && \
    apt-get -y install python${PY_VERSION} python${PY_VERSION}-venv
RUN cd /usr/bin && ln -sf python3.12 python3 && python3 --version

# install R
RUN wget -qO- https://cloud.r-project.org/bin/linux/ubuntu/marutter_pubkey.asc | sudo tee -a /etc/apt/trusted.gpg.d/cran_ubuntu_key.asc
RUN apt install r-base r-base-dev -y && R --version

# install quarto
RUN wget -q -P $DIR https://github.com/quarto-dev/quarto-cli/releases/download/v${QUARTO_VER}/quarto-${QUARTO_VER}-linux-${QUARTO_ARCH}.tar.gz && tar -xzf $DIR/quarto-${QUARTO_VER}-linux-${QUARTO_ARCH}.tar.gz -C $DIR
ENV PATH=$PATH:${DIR}/quarto-${QUARTO_VER}/bin

# install R package renv
# See Ubuntu repos for more packages that can be installed through apt manager: https://cloud.r-project.org/bin/linux/ubuntu/
RUN Rscript -e "install.packages('remotes', repos='https://cloud.r-project.org', verbose='TRUE'); remotes::install_version('renv', version = '$RENV_VER', verbose = 'TRUE')"



##### Compiling from source takes a LONG time (> 10 min)
# Download and install Python from source
# WORKDIR $DIR/Python-${PY_VERSION}
# RUN wget "https://www.python.org/ftp/python/${PY_VERSION}/Python-${PY_VERSION}.tgz" && tar -xf Python-${PY_VERSION}.tgz 
# RUN cd "Python-${PY_VERSION}" && ./configure --enable-optimizations && make install 

# Download and install R from source
# WORKDIR $DIR/R-${R_VERSION}
# RUN wget https://cran.r-project.org/src/base/R-4/R-${R_VERSION}.tar.gz && tar -xf R-${R_VERSION}.tar.gz
# RUN cd "R-${R_VERSION}" && ./configure && make

# Clean up files
# WORKDIR $DIR
# RUN rm -rf $DIR/Python-${PY_VERSION} $DIR/R-${R_VERSION}

