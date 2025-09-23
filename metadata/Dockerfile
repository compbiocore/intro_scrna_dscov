FROM rocker/geospatial:4.5.1
 
RUN apt-get update && \
	apt-get -y --no-install-recommends install --fix-missing \
    libfftw3-dev \
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
     


RUN R -e "install.packages(c('BPCells'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('presto'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('glmGamPoi'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('maps'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('pillar'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('gridExtra'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('metap'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('arrow'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('RcppArmadillo'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('deldir'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('Seurat'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('hdf5r'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('patchwork'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('tidyverse'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('ggrepel'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('sctransform'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('qs2'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('knitr'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('kableExtra'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('stringr'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('plotly'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('viridis'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('parallel'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('pdftools'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('openxlsx'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('tesseract'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('harmony'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('RColorBrewer'),repos = 'http://cran.rstudio.com/',ask = FALSE)"
RUN R -e "install.packages(c('scales'),repos = 'http://cran.rstudio.com/',ask = FALSE)"

RUN R -e "BiocManager::install('AnnotationHub')"
RUN R -e "BiocManager::install('AUCell')"
RUN R -e "BiocManager::install('BiocGenerics')"
RUN R -e "BiocManager::install('biomaRt')"
RUN R -e "BiocManager::install('clustree')"
RUN R -e "BiocManager::install('clusterProfiler')"
RUN R -e "BiocManager::install('ComplexHeatmap')"
RUN R -e "BiocManager::install('DelayedArray')"
RUN R -e "BiocManager::install('DelayedMatrixStats')"
RUN R -e "BiocManager::install('doMC)"
RUN R -e "BiocManager::install('doRNG')"
RUN R -e "BiocManager::install('enrichplot')"
RUN R -e "BiocManager::install('glmGamPoi')"
RUN R -e "BiocManager::install('JASPAR2024')"
RUN R -e "BiocManager::install('limma')"
RUN R -e "BiocManager::install('lme4')"
RUN R -e "BiocManager::install('MAST')"
RUN R -e "BiocManager::install('mixtools')"
RUN R -e "BiocManager::install('multtest')"
RUN R -e "BiocManager::install('rhdf5'
RUN R -e "BiocManager::install('S4Vectors')"
RUN R -e "BiocManager::install('SingleCellExperiment')"
RUN R -e "BiocManager::install('SummarizedExperiment')"
RUN R -e "BiocManager::install('batchelor')"
RUN R -e "BiocManager::install('HDF5Array')"
RUN R -e "BiocManager::install('terra')"
RUN R -e "BiocManager::install('ggrastr')"


RUN R -e "BiocManager::install(c('DelayedArray'))"
RUN R -e "BiocManager::install(c('DelayedMatrixStats'))"
RUN R -e "BiocManager::install(c('doMC'))"
RUN R -e "BiocManager::install(c('doRNG'))"
RUN R -e "BiocManager::install(c('DOSE'))"
RUN R -e "BiocManager::install(c('GENIE3'))"
RUN R -e "BiocManager::install(c('glmGamPoi'))"
RUN R -e "BiocManager::install(c('JASPAR2024'))"
RUN R -e "BiocManager::install(c('MAST'))"
RUN R -e "BiocManager::install(c('Matrix.utils'))"
RUN R -e "BiocManager::install(c('mixtools'))"
RUN R -e "BiocManager::install(c('multtest'))"
RUN R -e "BiocManager::install(c('NMF'))"
RUN R -e "BiocManager::install(c('R2HTML'))"
RUN R -e "BiocManager::install(c('rbokeh'))"
RUN R -e "BiocManager::install(c('RcisTarget'))"
RUN R -e "BiocManager::install(c('rhdf5'))"
RUN R -e "BiocManager::install(c('Rtsne'))"
RUN R -e "BiocManager::install(c('scater'))"
RUN R -e "BiocManager::install(c('TFBSTools'))"
RUN R -e "BiocManager::install(c('vsn'))"
RUN R -e "BiocManager::install(c('zoo'))"

RUN R -e "remotes::install_github('lucylgao/clusterpval')"
RUN R -e "remotes::install_github('cole-trapnell-lab/monocle3')"
RUN R -e "remotes::install_github('satijalab/azimuth')"
RUN R -e "remotes::install_github('satijalab/seurat-wrappers')"
RUN R -e "remotes::install_github('satijalab/seurat-data')"
RUN R -e "remotes::install_github('cellgeni/sceasy')"
RUN R -e "remotes::install_github('cellgeni/schard')"

RUN R -e "SeuratData::InstallData('ifnb')"

RUN ln -s /usr/lib/rstudio-server/bin/rsession /usr/local/bin/rsession 
