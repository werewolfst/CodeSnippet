## 使用apt-get更新并安装某个软件后，要注意清理apt-get的缓存

```docker
RUN apt-get update \
    && apt-get install -y ** \
    && rm -rf /var/lib/apt/lists/* 
```