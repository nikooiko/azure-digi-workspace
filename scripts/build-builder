#!/bin/bash

[ -z "${RELEASE}" ] && echo "RELEASE is not specified" && exit 1

DIR=$(realpath $(dirname $0))
# start with dey base (prerequisite)
pushd ${DIR}/../builder/dey-base
docker build -t dey-base:${RELEASE} \
  --build-arg DEY_INSTALL_PATH="/usr/local/dey-${RELEASE}" \
  --build-arg DEY_BRANCH=${RELEASE} \
  .
popd

# continue with the final builder
pushd ${DIR}/../builder
docker build -t azure-digi-builder:${RELEASE} \
  --build-arg DEY_BASE=${RELEASE} \
  --build-arg AZURE_BRANCH=${RELEASE} \
  --build-arg AZURE_INSTALL_PATH="/usr/local/azure-${RELEASE}" \
  .
popd
