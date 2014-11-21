### docker 操作筆記

下載image

    docker pull ubuntu
	
執行一次性指令

    docker run ubuntu echo "hello"
	
互動式操作環境

    docker run -t -i ubuntu

查看 container (exited 狀態)

    docker ps
	
查看運行中的 container

    docker ps -l
	
喚醒 exited 狀態 container

    docker start container_id
    
attach container (須先喚醒 container)

    docker attach container_id
	
docker cmmit

    docker commit b878e78d5592 deanboole/ubuntu:kyc2
    # 可用  docker images 查看是否有成功 commit
	
docker push

    docker login
    docker push deanboole/ubuntu:kyc2

docker version

    Client version: 1.3.1
    Client API version: 1.15
    Go version (client): go1.3.3
    Git commit (client): 4e9bbfa
    OS/Arch (client): linux/amd64
    Server version: 1.3.1
    Server API version: 1.15
    Go version (server): go1.3.3
    Git commit (server): 4e9bbfa
    
docker 安裝

    https://docs.docker.com/installation/debian/
