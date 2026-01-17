# 基础镜像，平台由 docker-compose 指定
ARG TARGETPLATFORM
FROM ubuntu:22.04

# 安装编译工具和 MPI
RUN apt-get update && apt-get install -y \
    build-essential \
    g++ \
    make \
    openmpi-bin \
    libopenmpi-dev \
    libomp-dev \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /workspace

# 保持容器运行
CMD ["/bin/bash"]