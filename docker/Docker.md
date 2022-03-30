## Docker 使用

``` sh
# 构建镜像
# docker build -f Dockerfile -t clay/luban-h5:latest .

# 启动容器
# docker run -d -p 1235:1337 --name luban-h5 clay/luban-h5:latest

# 浏览器访问
# 前端页面：http://127.0.0.1:1235
# 后端页面：http://127.0.0.1:1235/admin
```
