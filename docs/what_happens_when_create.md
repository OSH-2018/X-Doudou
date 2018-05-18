## What Happens When You `create` a Cunik

1. `/cunik/create POST` 请求到达；
2. HTTP server：将请求定向到 api.cunik.create；
3. api.cunik.create：解析 POST 参数，调用 api.models.cunik...；
4. api.models.cunik...：调用相应后端，创建虚拟机。
