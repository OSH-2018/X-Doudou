## 工具链

```shell
# 先装 opam

opam init
opam switch 4.04.2
eval `opam config env`
opam install mirage
```


## Hello, world!

```shell
git clone git://github.com/mirage/mirage-skeleton.git
cd mirage-skeleton
mirage configure -t unix
make depend
make
```

## www

```shell
git clone git://github.com/mirage/mirage-www
cd mirage-www
make prepare
cd src

mirage configure -t unix --kv_ro crunch --net socket
make depend
make
sudo ./xxx

mirage configure -t ukvm --kv_ro crunch --net socket
make depend
make
```

