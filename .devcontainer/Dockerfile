FROM rocker/rstudio:4.3.1

# Install Quarto CLI
RUN wget https://quarto.org/download/latest/quarto-linux-amd64.deb && \
    apt-get update && \
    apt-get install -y ./quarto-linux-amd64.deb && \
    rm quarto-linux-amd64.deb

RUN apt-get update && apt-get install -y git

RUN apt-get update && apt-get install -y python3 python3-pip && \
    pip install ipykernel ipywidgets jupyter


# Install R packages
RUN R -e "install.packages(c('quarto', 'tidyverse', 'ggplot2', 'lubridate', 'timetk'), repos='https://cloud.r-project.org')"

# Forecasting Libraries
RUN R -e "install.packages(c('forecast', 'prophet'), repos='https://cloud.r-project.org')"

# Machine Learning Libraries
RUN R -e "install.packages(c('glmnet', 'earth', 'kernlab', 'kknn', 'randomForest', 'ranger', 'xgboost', 'Cubist'), repos='https://cloud.r-project.org')"

# Time Series ML
RUN R -e "install.packages(c('tidymodels', 'rules'), repos='https://cloud.r-project.org')"

# Extras
RUN R -e "install.packages(c('DataExplorer', 'fs'), repos='https://cloud.r-project.org')"

# Install R Language Server for VS Code integration
RUN R -e "install.packages('languageserver')"

# Python integration
RUN R -e "install.packages('reticulate')"

# Modeltime
RUN R -e "install.packages('modeltime')"

# Install IRkernel inside R and register it
RUN R -e "install.packages('IRkernel', repos = 'https://cloud.r-project.org'); IRkernel::installspec(user = FALSE)"

# Git safe directory
RUN git config --global --add safe.directory /workspaces/time_series