### 构建镜像
```
docker build -t docker.io/wlniao/dotnet-sdk:8.0.0-alpine .
```

### 编译用例
```
docker run --rm -it -v $(pwd):/code docker.io/wlniao/dotnet-sdk:8.0.0-alpine dotnet publish /code --self-contained -c Release -p:PublishAot=true -p:PublishTrimmed=true
```