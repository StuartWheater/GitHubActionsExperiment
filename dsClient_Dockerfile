FROM cimg/base:current

RUN sudo apt-get update -y
RUN sudo apt-get upgrade -y
RUN wget -qO- https://cloud.r-project.org/bin/linux/ubuntu/marutter_pubkey.asc | sudo gpg --dearmor -o /usr/share/keyrings/r-project.gpg
RUN echo "deb [signed-by=/usr/share/keyrings/r-project.gpg] https://cloud.r-project.org/bin/linux/ubuntu jammy-cran40/" | sudo tee -a /etc/apt/sources.list.d/r-project.list
RUN sudo apt-get update -y
RUN sudo apt-get upgrade -y
RUN sudo apt-get install --no-install-recommends r-base -y

RUN sudo apt-get install cmake gfortran -y
RUN sudo apt-get install libxml2-dev libcurl4-openssl-dev libssl-dev libgsl-dev libgit2-dev r-base -y
RUN sudo apt-get install libharfbuzz-dev libfribidi-dev libmagick++-dev libfontconfig1-dev -y
RUN sudo apt-get install libfreetype6-dev libpng-dev libtiff5-dev libjpeg-dev -y
RUN sudo R -q -e "install.packages(c('devtools','covr'), dependencies=TRUE, repos='https://cloud.r-project.org')"
RUN sudo R -q -e "install.packages(c('fields','meta','metafor','ggplot2','gridExtra','data.table','panelaggregation'), dependencies=TRUE, repos='https://cloud.r-project.org')"
RUN sudo R -q -e "install.packages(c('DSI','DSOpal','DSLite'), dependencies=TRUE, repos='https://cloud.r-project.org')"
RUN sudo R -q -e "install.packages(c('MolgenisAuth', 'MolgenisArmadillo', 'DSMolgenisArmadillo'), dependencies=TRUE, repos='https://cloud.r-project.org')"
RUN sudo R -q -e "install.packages(c('DescTools','e1071'), dependencies=TRUE, repos='https://cloud.r-project.org')"
RUN sudo R -q -e "install.packages(c('mvtnorm', 'expm', 'Exact', 'gld'), dependencies=TRUE, repos='https://cloud.r-project.org')"

RUN sudo R -q -e "library('devtools'); devtools::install_github(repo='datashield/dsDangerClient', ref='v6.3.1-dev', dependencies = TRUE)"

# XML grep for coverage report merging
RUN sudo apt-get install xml-twig-tools -y
