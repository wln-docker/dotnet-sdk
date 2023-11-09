![wlniao](http://static.wlniao.com/logos/wlniao-bg.png)

# wlniao/dotnet-sdk
这是一个由Wlniao构建的Docker镜像，用于编译.Net的程序源码。


### 编译用例
```
docker run --rm -it -v $(pwd):/code docker.io/wlniao/dotnet-sdk:8.0.0-alpine dotnet publish /code --self-contained -c Release -p:PublishAot=true -p:PublishTrimmed=true
```

