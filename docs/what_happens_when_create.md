## What Happens When You `create` a Cunik

1. HTTP server：`/cunik/create POST` 请求到达 HTTP server；
2. api.cunik.create：解析 POST 参数，构造 backend.cunik.Config 的配置信息；
3. backend.cunik.create：处理 backend.cunik.Config，构造 backend.vm.Config
4. backend.vm.create：处理 backend.vm.Config，创建虚拟机并启动。