# 基于jenkins
FROM jenkins
USER root

# 将 shell 替换为 bash
RUN rm /bin/sh && ln -s /bin/bash /bin/sh

# 设置中科大软件镜像源
RUN sed -i 's/deb.debian.org/mirrors.ustc.edu.cn/g' /etc/apt/sources.list
RUN sed -i 's|security.debian.org|mirrors.ustc.edu.cn/debian-security|g' /etc/apt/sources.list
# upgrade
RUN apt-get update && apt-get upgrade -y

# 安装 dotnet core SDK
RUN apt-get install curl libunwind8 gettext apt-transport-https -y \
&& curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg \
&& mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg \
&& sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/dotnetdev.list' \
&& apt-get update \
&& apt-get install dotnet-sdk-2.0.0 -y
