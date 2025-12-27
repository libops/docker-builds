FROM alpine:3.23@sha256:865b95f46d98cf867a156fe4a135ad3fe50d2056aa3f25ed31662dff6da4eb62

ARG \
    TARGETARCH \
    # renovate: datasource=repology depName=alpine_3_23/bash
    BASH_VERSION=5.3.3-r1 \
    # renovate: datasource=repology depName=alpine_3_23/ca-certificates
    CA_CERTIFICATES_VERSION=20251003-r0 \
    # renovate: datasource=repology depName=alpine_3_23/curl
    CURL_VERSION=8.17.0-r1 \
    # renovate: datasource=repology depName=alpine_3_23/git
    GIT_VERSION=2.52.0-r0 \
    # renovate: datasource=repology depName=alpine_3_23/gnupg
    GNUPG_VERSION=2.4.8-r1 \
    # renovate: datasource=repology depName=alpine_3_23/go
    GO_VERSION=1.25.5-r0 \
    # renovate: datasource=repology depName=alpine_3_23/gzip
    GZIP_VERSION=1.14-r2 \
    # renovate: datasource=repology depName=alpine_3_23/jq
    JQ_VERSION=1.8.1-r0 \
    # renovate: datasource=repology depName=alpine_3_23/mariadb-client
    MARIADB_CLIENT_VERSION=11.4.9-r0 \
    # renovate: datasource=repology depName=alpine_3_23/netcat-openbsd
    NETCAT_OPENBSD_VERSION=1.234.1-r0 \
    # renovate: datasource=repology depName=alpine_3_23/openssl
    OPENSSL_VERSION=3.5.4-r0 \
    # renovate: datasource=repology depName=alpine_3_23/patch
    PATCH_VERSION=2.8-r0 \
    # renovate: datasource=repology depName=alpine_3_23/postgresql18-client
    POSTGRES_CLIENT_VERSION=18.1-r0 \
    # renovate: datasource=repology depName=alpine_3_23/procps-ng
    PROCPS_VERSION=4.0.5-r0 \
    # renovate: datasource=repology depName=alpine_3_23/shadow
    SHADOW_VERSION=4.18.0-r0 \
    # renovate: datasource=repology depName=alpine_3_23/util-linux
    UTIL_LINUX_VERSION=2.41.2-r0 \
    # renovate: datasource=repology depName=alpine_3_23/yq-go
    YQ_VERSION=4.49.2-r1

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
    postgresql18-client=="${POSTGRES_CLIENT_VERSION}" \
    procps=="${PROCPS_VERSION}" \
    shadow=="${SHADOW_VERSION}" \
    util-linux=="${UTIL_LINUX_VERSION}" \
    yq=="${YQ_VERSION}"

COPY --link rootfs /

RUN create-service-user.sh --name goapp
