# Use a base R image
FROM rocker/r-base:latest

# Install system dependencies for Jupyter (and for building R packages)
RUN apt-get update && apt-get install -y \
    python3 python3-pip libssl-dev libcurl4-openssl-dev libxml2-dev \
    && rm -rf /var/lib/apt/lists/*

# Install Jupyter
RUN pip3 install jupyter

# Install IRkernel inside R, so R shows up as a Jupyter kernel
RUN R -e "install.packages('IRkernel', repos='http://cran.r-project.org')" \
    && R -e "IRkernel::installspec(user = FALSE)" \
    && R -e "install.packages('tidyverse', repos='http://cran.r-project.org')" 

# Expose Jupyter’s default port (not strictly necessary for Codespaces,
# but can be useful if you want to run Jupyter directly)
EXPOSE 8888

# Set default container command
CMD [ "/bin/bash" ]
