FROM alpine:3.18
LABEL Maintainer="Wlniao <wlniao@qq.com>" \
      Description="Dotnet sdk container based on Alpine Linux."
ENV DOTNET_ROOT /usr/bin/dotnet
ENV PATH $PATH:$DOTNET_ROOT
RUN apk --no-cache add \
	krb5-libs \
	libstdc++ \
	libssl1.1 \
	libintl \
	icu-libs \
	build-base \
	zlib-dev \
	clang \
	wget \
	curl \
	icu \
	git \
	--repository http://dl-cdn.alpinelinux.org/alpine/edge/testing/ && rm -rf /var/cache/apk/* && rm -rf /root/.cache && rm -rf /tmp/*
RUN curl -o /tmp/dotnet.tar.gz https://download.visualstudio.microsoft.com/download/pr/10099e3c-c2e0-4f4c-a33e-6477a46f8d6b/f62cb118d5ded76cf81d702353255593/dotnet-sdk-8.0.100-rc.2.23502.2-linux-musl-x64.tar.gz \
    && mkdir -p $DOTNET_ROOT && tar zxf /tmp/dotnet.tar.gz -C $DOTNET_ROOT \
    && echo /dev/null > /tmp/dotnet.tar.gz \
    && chmod 777 $DOTNET_ROOT \
    && rm -rf /tmp/*

ENV ASPNETCORE_URLS= \
    # Do not generate certificate
    DOTNET_GENERATE_ASPNET_CERTIFICATE=false \
    # Do not show first run text
    DOTNET_NOLOGO=true \
    # SDK version
    DOTNET_SDK_VERSION=8.0.0 \
    # Enable correct mode for dotnet watch (only mode supported in a container)
    DOTNET_USE_POLLING_FILE_WATCHER=true \
    # Skip extraction of XML docs - generally not useful within an image/container - helps performance
    NUGET_XMLDOC_MODE=skip \
    DOTNET_CLI_TELEMETRY_OPTOUT=true