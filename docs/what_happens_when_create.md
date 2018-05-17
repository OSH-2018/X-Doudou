## What Happens When You `create` a Cunik

1. `/cunik/create POST` 请求到达；
2. HTTP server：将请求定向到 api.cunik.create；
3. api.cunik.create：解析 POST 参数，构造 backend.cunik.Config 的配置信息；
4. backend.cunik.create：处理 backend.cunik.Config，构造 backend.vm.Config
5. backend.vm.create：处理 backend.vm.Config，创建虚拟机并启动。