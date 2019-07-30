
# Docker

## Dockerfile

### 基本结构

```txt
    分为4部分: 基础镜像信息、维护者信息、镜像操作指令、容器启动时执行指令。
```

### 指令

* FROM

```txt
    格式 FROM <image> | FROM <image>:<tag>
```

* MAINTAINER

```txt
    MAINTAINER <name> 维护者信息
```

* RUN

```txt
    格式 RUN <command> | RUN ["executable","param1",...]
    前者在shell终端中运行/bin/sh -c; 后者则使用exec执行
    RUN在当前镜像基础上执行制定命令,并提交为新的镜像
```

* CMD

```txt
    格式 CMD ["executable","param1",...] |
         CMD cmmand param1 param2 在/bin/sh中执行 |
         CMD ["param1","param2",...] 提供给ENTRYPOINT的默认参数
    每个dockerfile只有一条CMD命令被执行，指定多条只有最后一条执行。启动时容器指定了运行命令,则会覆盖
```

* EXPOSE

```txt
    格式 EXPOSE <port> [<port>...]
    服务暴露端口号
```

* ENV

```txt
    格式 ENV <KEY> <VALUE> 
    制定一个环境变量被后续的RUN指令使用 并在容器运行时保持
```

* ADD

```txt
    格式 ADD <src> <dest>
    复制本地主机的src(为dockerfile所在目录的相对路径)到容器中的<dest>;也可以是URL;还可以是tar文件(自动解压为目录)
```

* COPY

```txt
    格式 COPY <src> <dest>
    复制本地主机的<src>(为Dockerfile所在目录的相对路径，文件或目录)为容器中的<dest>。目录不存在时，会自动创建
```

* ENTRYPOINT

```txt
    格式 ENTRYPOINT ["executable","param1",...] |
         ENTRYPOINT command param1 param2 ... (shell中执行)
    配置容器启动后执行的命令。并且不可被docker run提供的参数覆盖
    每个dockerfile中只能有一个ENTRYPOINT,当指定多个ENTRYPOINT时，只有最后一个生效
```

* VOLUME

```txt
    格式 VOLUME ["/data"]
    创建一个可以从本地之际或其他容器挂在的挂载点。
```

* USER

```txt
    格式 USER daemon
    指定运行容器时的用户名或UID，后续的RUN也会使用指定的用户
```

* WORKDIR

```txt
    格式 WORKDIR /path/to/workdir
    为后续的RUN、CMD、ENTRYPOINT制定配置工作目录
    可以使用多个WORKDIR 后续命令如果参数是相对路径，则会基于之前的命令指定的路径。
```

* ONBUILD

```txt
    格式 ONBUILD [INSTRUCTION]
    配置当前所创建的镜像作为其他新创建镜像的基础镜像时，所执行的操作指令。
```
