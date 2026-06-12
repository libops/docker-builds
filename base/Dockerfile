FROM alpine:3.24@sha256:a2d49ea686c2adfe3c992e47dc3b5e7fa6e6b5055609400dc2acaeb241c829f4

ARG \
    TARGETARCH \
    # renovate: datasource=repology depName=alpine_3_23/bash
    BASH_VERSION=5.3.3-r1 \
    # renovate: datasource=repology depName=alpine_3_23/ca-certificates
    CA_CERTIFICATES_VERSION=20251003-r0 \
    # renovate: datasource=repology depName=alpine_3_23/curl
    CURL_VERSION=8.19.0-r0 \
    # renovate: datasource=repology depName=alpine_3_23/git
    GIT_VERSION=2.52.0-r0 \
    # renovate: datasource=repology depName=alpine_3_23/gnupg
    GNUPG_VERSION=2.4.9-r0 \
    # renovate: datasource=repology depName=alpine_3_23/go
    GO_VERSION=1.25.10-r0 \
    # renovate: datasource=repology depName=alpine_3_23/gzip
    GZIP_VERSION=1.14-r2 \
    # renovate: datasource=repology depName=alpine_3_23/jq
    JQ_VERSION=1.8.1-r0 \
    # renovate: datasource=repology depName=alpine_3_23/mariadb-client
    MARIADB_CLIENT_VERSION=11.4.12-r0 \
    # renovate: datasource=repology depName=alpine_3_23/netcat-openbsd
    NETCAT_OPENBSD_VERSION=1.234.1-r0 \
    # renovate: datasource=repology depName=alpine_3_23/openssl
    OPENSSL_VERSION=3.5.7-r0 \
    # renovate: datasource=repology depName=alpine_3_23/patch
    PATCH_VERSION=2.8-r0 \
    # renovate: datasource=repology depName=alpine_3_23/procps-ng
    PROCPS_VERSION=4.0.5-r0 \
    # renovate: datasource=repology depName=alpine_3_23/shadow
    SHADOW_VERSION=4.18.0-r0 \
    # renovate: datasource=repology depName=alpine_3_23/util-linux
    UTIL_LINUX_VERSION=2.41.4-r0 \
    # renovate: datasource=repology depName=alpine_3_23/yq-go
    YQ_VERSION=4.49.2-r6

RUN --mount=type=cache,id=base-apk-${TARGETARCH},sharing=locked,target=/var/cache/apk \
    ln -s /var/cache/apk /etc/apk/cache && \
    apk add \
    bash=="${BASH_VERSION}" \
    ca-certificates=="${CA_CERTIFICATES_VERSION}" \
    curl=="${CURL_VERSION}" \
    git=="${GIT_VERSION}" \
    gnupg=="${GNUPG_VERSION}" \
    go=="${GO_VERSION}" \
    gzip=="${GZIP_VERSION}" \
    jq=="${JQ_VERSION}" \
    mariadb-client=="${MARIADB_CLIENT_VERSION}" \
    netcat-openbsd=="${NETCAT_OPENBSD_VERSION}" \
    openssl=="${OPENSSL_VERSION}" \
    patch=="${PATCH_VERSION}" \
    procps=="${PROCPS_VERSION}" \
    shadow=="${SHADOW_VERSION}" \
    util-linux=="${UTIL_LINUX_VERSION}" \
    yq=="${YQ_VERSION}"

COPY --link rootfs /

RUN create-service-user.sh --name goapp
