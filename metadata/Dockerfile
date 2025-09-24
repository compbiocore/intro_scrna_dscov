FROM ghcr.io/compbiocore/intro_scrna_dscov:sep_23_07-01-47_2025

RUN R -e "BiocManager::install(c('DOSE'))"
RUN R -e "BiocManager::install(c('GENIE3'))"
RUN R -e "BiocManager::install(c('Matrix.utils'))"
RUN R -e "BiocManager::install(c('NMF'))"
RUN R -e "BiocManager::install(c('R2HTML'))"
RUN R -e "BiocManager::install(c('rbokeh'))"
RUN R -e "BiocManager::install(c('RcisTarget'))"
RUN R -e "BiocManager::install(c('Rtsne'))"
RUN R -e "BiocManager::install(c('scater'))"
RUN R -e "BiocManager::install(c('TFBSTools'))"
RUN R -e "BiocManager::install(c('vsn'))"
RUN R -e "BiocManager::install(c('zoo'))"
RUN R -e "BiocManager::install(c('sva'))"
RUN R -e "BiocManager::install(c('ihw'))"


RUN R -e "remotes::install_github('lucylgao/clusterpval')"
RUN R -e "remotes::install_github('cole-trapnell-lab/monocle3')"
RUN R -e "remotes::install_github('satijalab/azimuth')"
RUN R -e "remotes::install_github('satijalab/seurat-wrappers')"
RUN R -e "remotes::install_github('satijalab/seurat-data')"
RUN R -e "remotes::install_github('cellgeni/sceasy')"
RUN R -e "remotes::install_github('cellgeni/schard')"

RUN R -e "SeuratData::InstallData('ifnb')"

RUN ln -s /usr/lib/rstudio-server/bin/rsession /usr/local/bin/rsession
