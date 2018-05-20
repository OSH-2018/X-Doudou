## 源码架构

* api

  * models

    提供对 cunik 和 image 以及对应的 registry 的操作。

  * router

    对 HTTP Server 收到的请求、参数进行处理，最终将操作转发至 models 提供的接口。

* backend

  * unikernel

    提供对各种 unikernel 的接口

  * vm

    提供对各种 vm 的接口

## 一些概念

### Image

镜像，包括元数据及相应的 unikernel。

### Image Registry

本地的 Image “注册表”，记录本地存在的 image 等。

### Cunik

包括一个虚拟机实例、运行的 image、数据卷、网络配置等。

### Cunik Registry

本地的 cunik “注册表”，记录本地存在的 cunik、配置信息、运行信息等。

### Cunik Config

### VM Config