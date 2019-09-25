## 切换用户

```docker
RUN groupadd -r redis && useradd -r -g redis redis
RUN wget -O /usr/local/bin/gosu \
    "https://github.com/tianon/gosu/releases/download/1.7/gosu-amd64" \
    && chmod +x /usr/local/bin/gosu \
    && gosu nobody true
CMD ["exec", "gosu", "redis", "redis-server"]
```