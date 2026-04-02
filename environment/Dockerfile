# hash:sha256:e523de88a1e39258153cb6ab0a9ebe1d0f48108563f62c7ded6810460c99e638
ARG REGISTRY_HOST
FROM $REGISTRY_HOST/codeocean/code-server-python-extensions-pack:v5.0

ARG DEBIAN_FRONTEND=noninteractive
ARG GIT_ASKPASS
COPY git-ask-pass /

RUN --mount=type=secret,id=git-access-token \
    GIT_ACCESS_TOKEN="$(cat /run/secrets/git-access-token)" \
    pip install -U --no-cache-dir \
    aind-data-access-api[docdb]==1.9.3 \
    codeocean==0.14.0 \
    -e git+https://github.com/AllenNeuralDynamics/aind-hcr-data-loader.git#egg=aind-hcr-data-loader \
    -e git+https://github.com/AllenNeuralDynamics/aind-hcr-qc.git#egg=aind-hcr-qc
