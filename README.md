## docker 操作筆記

### IMAGE

```bash
# 下載image
$ docker pull ubuntu

# 查看 image 有哪些

$ docker image
```

### 讓 container 執行指令

```bash
# 執行一次性指令
$ docker run ubuntu echo "hello"

# 互動式操作環境
$ docker run -t -i ubuntu
```

### 查看 container 狀態或處理 container

```bash
# 查看運行中的 container
$ docker ps

# 查看 container (exited 狀態)
$ docker ps -l

# 喚醒 exited 狀態 container
$ docker start container_id

# attach container (須先喚醒 container)
$ docker attach container_id

# 刪除 container
$ docker rm container_id
```

### 客製化 images

```bash
# docker commit 可用  docker images 查看是否有成功 commit
$ docker commit b878e78d5592(container id) deanboole/ubuntu:kyc2

# docker push
$ docker login
$ docker push deanboole/ubuntu:kyc2

# docker pull
$ docker login
$ docker pull deanboole/ubuntu:kyc2
```

### 安裝

```
debian
https://docs.docker.com/installation/debian/

mac os
https://github.com/boot2docker/osx-installer
```

### docker 啟動
```bash
# mac os
$ boot2docker start
$ eval "$(boot2docker shellinit)"
```
