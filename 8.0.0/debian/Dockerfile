FROM debian:stable-20231030
LABEL Maintainer="Wlniao <wlniao@qq.com>" \
      Description="Dotnet sdk container based on Debian Linux."
ENV DOTNET_ROOT /usr/bin/dotnet
ENV PATH $PATH:$DOTNET_ROOT
#通过build-essential库安装gcc，zlib需要安装zlib1g-dev的开发版本，debian12的icu需要安装libicu72版本
RUN apt update && apt install -y --no-install-recommends ca-certificates \
	libc6 \
        libgcc1 \
        libgssapi-krb5-2 \
        libicu72 \
        libssl3 \
        libstdc++6 \
        zlib1g-dev \
        openssl \
        clang \
        curl \
	gcc \
        git \
	&& apt clean \
	&& apt autoremove \
	&& rm -rf /var/lib/apt/lists/*

RUN curl -o /tmp/dotnet.tar.gz https://download.visualstudio.microsoft.com/download/pr/5226a5fa-8c0b-474f-b79a-8984ad7c5beb/3113ccbf789c9fd29972835f0f334b7a/dotnet-sdk-8.0.100-linux-x64.tar.gz \
    && mkdir -p $DOTNET_ROOT && tar zxf /tmp/dotnet.tar.gz -C $DOTNET_ROOT \
    && echo /dev/null > /tmp/dotnet.tar.gz \
    && chmod 777 $DOTNET_ROOT \
    && rm -rf /tmp/*

ENV DOTNET_SDK_VERSION=8.0.0 \
    DOTNET_RUNNING_IN_CONTAINER=true \
    DOTNET_USE_POLLING_FILE_WATCHER=true \
    DOTNET_CLI_TELEMETRY_OPTOUT=true \
    DOTNET_NOLOGO=true \
    NUGET_XMLDOC_MODE=skip \
    BUILD_CONFIGURATION=Release