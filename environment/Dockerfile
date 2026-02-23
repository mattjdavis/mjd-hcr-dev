# hash:sha256:e846741b987818a8b31bfac7b82bcd90e1fb639105fe00443ac5f6eaa4f7bae6
ARG REGISTRY_HOST
FROM $REGISTRY_HOST/codeocean/code-server-python-extensions-pack:code-server4.108.2python3.12.4aind-metadata-mcp0.5.2withDOTFILES_REPOsupport

ARG DEBIAN_FRONTEND=noninteractive
ARG GIT_ASKPASS
COPY git-askpass /

RUN --mount=type=secret,id=git-access-token \
    GIT_ACCESS_TOKEN="$(cat /run/secrets/git-access-token)" \
    pip install -U --no-cache-dir \
    aind-data-access-api[docdb] \
    codeocean-sdk-python \
    -e git+https://github.com/AllenNeuralDynamics/aind-hcr-data-loader.git#egg=aind-hcr-data-loader \
    -e git+https://github.com/AllenNeuralDynamics/aind-hcr-qc.git#egg=aind-hcr-qc
