#wlniao/dotnet

### Version
```
This docker imager build for the .NET Core SDK 2.2.7
```

### Build
```
git clone https://github.com/wln-docker/dotnet-sdk.git && docker build -t wlniao/dotnet-sdk:2.2.7 --no-cache ./dotnet-sdk/2.2.7
```

### How to use
```
docker run -d -v /tmp/code:/wln wlniao/dotnet-sdk:2.2.7
```
使用热更新
```
docker run -d -v /tmp/code:/wln wlniao/dotnet-sdk:2.2.7 sh -c "dotnet add package Microsoft.DotNet.Watcher.Tools --version 2.0.0 && dotnet watch run --verbose"
```