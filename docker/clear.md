## 杀死所有正在运行的容器
```docker
docker kill $(docker ps -a -q)
```

## 删除所有已经停止的容器
```docker
docker rm $(docker ps -a -q)
```

## 删除所有未打某标签的镜像
```docker
docker rmi $(docker images -q -f test=true)
```

## 删除所有镜像
```docker
docker rmi $(docker images -q)
```

## 删除所有的none镜像
```docker
docker rmi `docker images | grep  "<none>" | awk '{print $3}'`
```