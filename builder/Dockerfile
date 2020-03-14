ARG DEY_BASE="thud"
FROM dey-base:${DEY_BASE}

# Change back to root for root operations
USER root

# Install some helper packages
RUN apt-get update && apt-get install -y vim && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Install azure dependencies
ARG AZURE_BRANCH="thud"
ARG AZURE_INSTALL_PATH=/usr/local/azure-thud
RUN install -o 1000 -g 1000 -d ${AZURE_INSTALL_PATH}
WORKDIR ${AZURE_INSTALL_PATH}
RUN repo init -u https://github.com/nikooiko/azure-digi-manifest.git \
    -b ${AZURE_BRANCH} \
    -m azure.xml \
    && repo sync -j4 --no-repo-verify
ENV AZURE_INSTALL_PATH=${AZURE_INSTALL_PATH}

# Install builder scripts
COPY scripts/* /usr/local/bin/

USER dey
WORKDIR /workdir