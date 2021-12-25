## BookStack自用：

### 感谢以下项目:

[https://github.com/truthhun/BookStack](https://github.com/truthhun/BookStack)                                   

### 版本：

|名称|版本|说明|
|:-|:-|:-|
|BookStack|2.10|amd64;arm64v8;arm32v7|

#### 版本升级注意：

* 需要先自行安装mysql

### docker命令行设置：

1. 下载镜像

       使用Dockerfile构建: docker build -t bookstack:v1 .

2. 创建calibre-web容器

       docker run -d -p 8181:8181 \
              --name bookstack \
              --restart=always \
              -v 配置位置文件:/usr/local/bookstack/conf/ \
              bookstack:v1

3. 运行

       docker start bookstack

4. 停止

       docker stop bookstack

5. 删除容器

       docker rm  bookstack

6. 删除镜像

       docker image rm  bookstack:v1

### 变量:

|参数|说明|
|:-|:-|
| `--name=bookstack` |容器名|
| `--restart=always` |自启动|
| `-v 配置位置文件:/usr/local/bookstack/conf/` |bookstack配置位置文件|
| `-p 8181:8181` |运行端口|

