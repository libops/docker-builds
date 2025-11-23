ARG LEHIGH_TAG=main
FROM islandora/base:6.0.11@sha256:1bea55c375ee9165ab62f192b7eea9d4cdafeeee1b70d56d3f4ece644e2282e6

ARG TARGETARCH
ARG \
    # renovate: datasource=github-tags depName=golang packageName=golang/go versioning=go-mod-directive
    GO_VERSION=go1.25.3 \
    GO_BASE_URL="https://go.dev/dl/${GO_VERSION}" \
    GO_AMD64=linux-amd64.tar.gz	\
    GO_AMD64_SHA256="0335f314b6e7bfe08c3d0cfaa7c19db961b7b99fb20be62b0a826c992ad14e0f" \
    GO_ARM64=linux-arm64.tar.gz \
    GO_ARM64_SHA256="1d42ebc84999b5e2069f5e31b67d6fc5d67308adad3e178d5a2ee2c9ff2001f5"

RUN --mount=type=cache,id=base-downloads-${TARGETARCH},sharing=locked,target=/opt/downloads \
    if [ "${TARGETARCH}" = "amd64" ]; \
    then \
    download.sh \
    --url "${GO_BASE_URL}.${GO_AMD64}" \
    --sha256 "${GO_AMD64_SHA256}" \
    --dest /usr/local ; \
    else \
    download.sh \
    --url "${GO_BASE_URL}.${GO_ARM64}" \
    --sha256 "${GO_ARM64_SHA256}" \
    --dest /usr/local ; \
    fi

ENV \
    PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/local/go/bin \
    PORT=8080

RUN go version | grep "${GO_VERSION}"

RUN create-service-user.sh --name goapp && \
    cleanup.sh

COPY --link rootfs /

HEALTHCHECK CMD /bin/bash -c 'curl -sf http://localhost:$PORT/healthcheck'
