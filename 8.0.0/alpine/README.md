### 构建镜像
```
docker build -t docker.io/wlniao/dotnet-sdk:8.0.0-alpine .
```

### 编译用例
```
docker run --rm -it -v $(pwd):/code -w /code docker.io/wlniao/dotnet-sdk:8.0.0-alpine dotnet publish /code -o /code/bin/dist --self-contained -c Release -p:PublishAot=true -p:PublishTrimmed=true
```

### 制品用例
```
docker run --rm -it -v $(pwd)/bin/dist:/wln -w /wln docker.io/wlniao/dotnet:deps8 sh
```