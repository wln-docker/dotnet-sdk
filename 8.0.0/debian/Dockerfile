FROM debian:stable-20231030
LABEL Maintainer="Wlniao <wlniao@qq.com>" \
      Description="Dotnet container based on Alpine Linux."
ENV DOTNET_ROOT /usr/bin/dotnet
ENV PATH $PATH:$DOTNET_ROOT
RUN apk --no-cache add ca-certificates \
	clang zlib1g-dev

RUN curl -o /tmp/dotnet.tar.gz https://download.visualstudio.microsoft.com/download/pr/9144f37e-b370-41ee-a86f-2d2a69251652/bc1d544112ec134184a5aec7f7a1eaf9/dotnet-sdk-8.0.100-rc.2.23502.2-linux-x64.tar.gz \
    && mkdir -p $DOTNET_ROOT && tar zxf /tmp/aspnetcore.tar.gz -C $DOTNET_ROOT \
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