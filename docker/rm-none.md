## 删除所有的<none>镜像

```docker
docker rmi `docker images | grep  "<none>" | awk '{print $3}'`
```