FROM ghcr.io/compbiocore/intro_scrna_dscov:sep_23_11-23-48_2025

FROM rocker/geospatial:4.5.1
 

#install some base libs
RUN apt-get update && \
	apt-get -y --no-install-recommends install --fix-missing \
        apt-file \
        apt-utils \
        build-essential \
        bzip2 \
        ca-certificates \
        cmake \
        curl \
	      default-jdk \
        default-jre\
        gdb \
        git \
        hdf5-helpers \
        lbzip2 \
        libbz2-dev \
        libcairo2-dev \
        libcurl4-openssl-dev \
        libfftw3-dev \
        libgeos-dev \
        libgl1-mesa-dev \
        libglpk-dev \
        libglu1-mesa-dev \
        libgsl0-dev \
        libhdf4-alt-dev \
        libhdf5-dev \
        libjpeg-dev \
        libjq-dev \
        liblzma-dev \
        libmariadbd-dev \
        libnetcdf-dev \
        libpng-dev \
        libpq-dev \
        libproj-dev \
        libprotobuf-dev \
        libsqlite3-dev \
        libssh2-1-dev \
        libssl-dev \
        libudunits2-dev \
        libxml2-dev \
        libxt-dev \
        libz-dev \
        make \
        netcdf-bin \
        postgis \
        protobuf-compiler \
        python3-pip \
        sqlite3 \
        tk-dev \
        unixodbc-dev \
        unzip \
        vim \
        libpoppler-cpp-dev \
        && apt-get clean && rm -rf /var/lib/apt/lists/*

RUN R -e "install.packages('BiocManager', dependencies=TRUE, repos='http://cran.rstudio.com/', ask = FALSE)"
RUN R -e "install.packages('remotes', dependencies=TRUE, repos='http://cran.rstudio.com/', ask = FALSE)"


# FFTW, FIt-SNE
RUN wget http://www.fftw.org/fftw-3.3.10.tar.gz \
    && tar zxvf fftw-3.3.10.tar.gz \
    && rm fftw-3.3.10.tar.gz \
    && cd fftw-3.3.10 \
    && ./configure \
    && make \
    && make install \
    && git clone https://github.com/KlugerLab/FIt-SNE.git \
    && cd FIt-SNE/ \
    && g++ -std=c++11 -O3  src/sptree.cpp src/tsne.cpp src/nbodyfft.cpp  -o bin/fast_tsne -pthread -lfftw3 -lm \
    && cp bin/fast_tsne /usr/local/bin/
     


