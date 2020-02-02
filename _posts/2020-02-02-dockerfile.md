---
title: Dockerfile 用法解析
---

FROM：（唯一必须项）基于哪个镜像。

WORKDIR：生成接下来的 shell 语句运行在哪个目录，如果没有就会自动生成。

COPY：把宿主机的文件拷贝到镜像中去。

RUN：运行 shell 语句（构建时）。

ADD：和 RUN 类似，但是可以接受 URL，如果能用 RUN 完成的话用 RUN 就行了（够用就好）。

CMD：指定镜像启动时运行的脚本（运行时）。

ENTRYPOINT：类似 CMD。

EXPOSE：指定当前镜像暴露的端口。

VOLUME：指定文件映射到哪里

ENV：环境变量（构建时和运行时都有效）。

ARG：类似 ENV，但是只在构建时有效。

LABEL：设置元数据（没有实质性的作用）。

ONBUILD：当前镜像构建时不会执行，基于当前镜像的镜像构建时才会执行。

STOPSIGNAL：指定用什么 SIGNAL 停止容器。

HEALTHCHECK：用来检查容器健康状态的配置（少用）。

SHELL：指定用哪种 Shell。

USER：指定用户身份。