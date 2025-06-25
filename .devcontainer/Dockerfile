FROM rocker/rstudio:4.3.1

# Install Quarto CLI
RUN wget https://quarto.org/download/latest/quarto-linux-amd64.deb && \
    apt-get update && \
    apt-get install -y ./quarto-linux-amd64.deb && \
    rm quarto-linux-amd64.deb

RUN apt-get update && apt-get install -y git

# Install R packages
RUN R -e "install.packages(c('quarto', 'tidyverse', 'ggplot2', 'lubridate'), repos='https://cloud.r-project.org')"

# Git safe directory
RUN git config --global --add safe.directory /workspaces/TimeSeriesR