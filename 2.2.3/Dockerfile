FROM wlniao/dotnet:deps
RUN curl -o /tmp/dotnet.tar.gz https://download.visualstudio.microsoft.com/download/pr/17b53621-992d-4805-9feb-93cc34662c5f/c83ef9c56200b4d333b18c48f9054437/dotnet-sdk-2.2.110-linux-musl-x64.tar.gz \
    && tar zxf /tmp/dotnet.tar.gz -C /usr/local/bin \
    && chmod 777 /usr/local/bin/dotnet \
    && echo " " > /tmp/dotnet.tar.gz
WORKDIR /wln
CMD dotnet restore && dotnet run