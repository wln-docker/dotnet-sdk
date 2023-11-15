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
RUN curl -o /tmp/dotnet.tar.gz https://download.visualstudio.microsoft.com/download/pr/40a3227f-0d20-4c23-b1a5-ecd659e3faef/fa59541ab3a35a50172ea5f81070e075/dotnet-sdk-8.0.100-linux-musl-x64.tar.gz \
    && mkdir -p $DOTNET_ROOT && tar zxf /tmp/dotnet.tar.gz -C $DOTNET_ROOT \
    && echo /dev/null > /tmp/dotnet.tar.gz \
    && chmod 777 $DOTNET_ROOT \
    && rm -rf /tmp/*

ENV DOTNET_SDK_VERSION=8.0.0 \
    DOTNET_RUNNING_IN_CONTAINER=true \
    DOTNET_USE_POLLING_FILE_WATCHER=true \
    DOTNET_CLI_TELEMETRY_OPTOUT=true \
    DOTNET_NOLOGO=true \
    NUGET_XMLDOC_MODE=skip