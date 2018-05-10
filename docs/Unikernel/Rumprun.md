## 工具链

```shell
$ git clone http://repo.rumpkernel.org/rumprun
$ cd rumprun
$ git submodule update --init  # 炒鸡慢
$ CC=cc ./build-rr.sh hw  # hw for KVM，xen for Xen，在实验室服务器上出现 machine/cdefs.h 找不到的问题，在 bwg 和超算练习服务器上正常

$ export PATH="${PATH}:$(pwd)/rumprun/rumprun/bin"
```

* 构建成功后目录不能改名。

```shell
# 设置网络设备
$ ip tuntap add tap0 mode tap
$ ip addr add 10.0.120.100/24 dev tap0
$ ip link set dev tap0 up
```

## 仓库

```shell
$ git clone http://repo.rumpkernel.org/rumprun-packages
$ cd rumprun-packages
$ cp config.mk.dist config.mk
$ ...  # 修改 config.mk，指定 TUPLE
```

## nginx

```shell
$ cd nginx
$ make
$ rumprun-bake hw_virtio ./nginx.bin bin/nginx  # hw_virtio for KVM/QEMU

# 启动
$ rumprun qemu -i -M 128 \
    -I if,vioif,'-net tap,script=no,ifname=tap0'\
    -W if,inet,static,10.0.120.101/24 \
    -b images/data.iso,/data \
    -- ./nginx.bin -c /data/conf/nginx.conf
## 现在可以通过 10.0.120.101 访问

# 修改 images/data 以更改配置文件、网站内容
```
## mysql

```shell
$ cd mysql
$ make
$ # host 的 openssl 找不到，待修复
```

需要 cmake

## redis

```shell
$ cd redis
$ make
$ rumprun-bake hw_generic bin/redis-server.bin bin/redis-server

# 持久化
$ rumprun qemu -i -M 256 \
    -I if,vioif,'-net tap,script=no,ifname=tap0' \
    -W if,inet,static,10.0.120.101/24 \
    -b images/data.iso,/data \
    -b images/datapers.img,/backup \
    -- bin/redis-server.bin /data/conf/redisaof.conf
## 成功，但是需要手动 mkfs（Debian 上）

# 非持久化
$ rumprun qemu -i -M 256 \
    -I if,vioif,'-net tap,script=no,ifname=tap0' \
    -W if,inet,static,10.0.120.101/24 \
    -b images/data.iso,/data \
    -- bin/redis-server.bin /data/conf/redis.conf
## 成功
```

