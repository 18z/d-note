## docker 操作筆記

### IMAGE

```bash
# 下載image
$ docker pull deanboole/gcc

# 查看 image 有哪些
$ docker image

REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
deanboole/gcc       gcc5-1              d3f73fef10cf        2 minutes ago       1.153 GB
gcc-5.1             latest              02e3279a9edd        15 hours ago        1.153 GB
buildpack-deps      wheezy              5a67014e6fb0        33 hours ago        459.2 MB
gcc                 5.2                 5f5adc3c63a6        4 weeks ago         1.389 GB
gcc                 latest              5f5adc3c63a6        4 weeks ago         1.389 GB
```

### 讓 container 執行指令

```bash
# 執行一次性指令
$ docker run deanboole/gcc:gcc5-1 echo "hello"

# 互動式操作環境
$ docker run -t -i deanboole/gcc:gcc5-1
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
# Usage: docker commit [OPTIONS] CONTAINER [REPOSITORY[:TAG]]

$ docker commit d9713f42505c deanboole/gcc:gcc5-1

# docker push
$ docker login
$ docker push deanboole/gcc:gcc5-1

# 可至下列網址查看
https://hub.docker.com/r/deanboole/gcc/tags/

# docker pull
$ docker login
$ docker pull deanboole/gcc:gcc5-1
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

### docker build from dockerfile

```bash
# 首先 clone 該專案至 local 端
$ git clone https://github.com/docker-library/gcc.git

# 進入 gcc/5.1 資料夾
$ cd gcc/5.1

# 開始建立 image
$ docker build -t gcc-5.1 .
```

### 在 container 內 compile

```bash
$ docker run --rm -v "$PWD":/usr/src/myapp -w /usr/src/myapp gcc-5.1 gcc -o hello hello.c
```

### 參考文獻

* [docker hub gcc](https://hub.docker.com/_/gcc/)
* [build dockerfile](https://docs.docker.com/reference/builder/)
* [docker run cmd](https://docs.docker.com/reference/run/#clean-up-rm)
