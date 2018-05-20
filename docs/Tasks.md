定一个小目标：HTTP 接口 创建、启动、查询、暂停、恢复、删除 rumprun 的一个应用（nginx），暂不实现网络和储存功能。

 

接口：Wed 23:59

总：5.30 23:59

- 路由：CunikConfig Cunik

  把 HTTP 请求转发到 api.models.cunik。

  内存、镜像名、虚拟机类型

- libvirt

  接到 VMConfig，创建对应的虚拟机，其他接口

  VM、VMConfig

- Cunik Registry

  为 Cunik 提供创建、状态记录、查询、更改

- Cunik、CunikConfig：CunikRegistry

  定义 CunikConfig，将 CunikConfig 转换为 VMConfig

  实现 Rumprun 后端的 CunikConfig 到 VMConfig