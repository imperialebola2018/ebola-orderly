FROM vimc/orderly.server:master

RUN apt-get update || apt-get update && apt-get install -y git

# Install LaTeX
RUN apt-get update \
  && apt-get install -y --no-install-recommends \
    ghostscript \
    imagemagick \
    lmodern \
    texlive-fonts-recommended \
    texlive-humanities \
    texlive-latex-extra \
    texinfo \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/ \
  && cd /usr/share/texlive/texmf-dist \
  && wget http://mirrors.ctan.org/install/fonts/inconsolata.tds.zip \
  && unzip inconsolata.tds.zip \
  && rm inconsolata.tds.zip \
  && echo "Map zi4.map" >> /usr/share/texlive/texmf-dist/web2c/updmap.cfg \
  && mktexlsr \
  && updmap-sys

# Install Pandoc
ENV PANDOC_VERSION "1.19.2.1"
RUN wget https://github.com/jgm/pandoc/releases/download/${PANDOC_VERSION}/pandoc-${PANDOC_VERSION}-1-amd64.deb \
  && dpkg --install pandoc-${PANDOC_VERSION}-1-amd64.deb \
  && rm pandoc-${PANDOC_VERSION}-1-amd64.deb

# system dependencies required to install and run R packages (in
# alphabetical order)
RUN apt-get update && apt-get install -y \
  libcurl4-openssl-dev \
  libgdal-dev \
  libgsl0-dev \
  libmagick++-dev \
  libssl-dev \
  libsodium-dev \
  libudunits2-dev \
  libv8-dev \
  libxml2-dev

COPY bin /usr/local/bin/

# Add new packages here (in alphabetical order)
RUN install2.r --error \
  Hmisc \
  RColorBrewer \
  Rfast \
  binom \
  concaveman \
  deming \
  distcrete \
  dplyr \
  drat \
  ggplot2 \
  ggpubr \
  ggthemes \
  knitr \
  lme4 \
  lubridate \
  openxlsx \
  pander \
  readxl \
  rmarkdown \
  tidyr \
  tidyverse \
  waffle \
  wesanderson \
  zoo

RUN install_packages --repo "https://imperialebola2018.github.io/drat" \
  EpiEstim \
  cyphr \
  epitrix \
  incidence \
  earlyR \
  projections \
  vaultr

WORKDIR /orderly
