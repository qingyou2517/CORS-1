# 创建 qq.com:8888 和 frank.com:9990：
```
首先，以管理员权限打开记事本，用记事本打开 C:\Windows\System32\drivers\etc，修改host：
  
  127.0.0.1 qq.com
  127.0.0.1 frank.com
  
这样就能用 127.0.0.1:8888 和 127.0.0.1:9990 分别模拟 qq.com:8888 和 frank.com:9990
```
# frank.com 的 frank.js 脚本使用 CORS 跨域访问 qq.com 的 friends.json 数据
```
在qq.com 的 server.js 服务器中添加 Access-Control-Allow-Origin：

else if(path === '/friends.json'){
    response.statusCode = 200
    response.setHeader('Content-Type', 'text/json;charset=utf-8')
    response.setHeader('Access-Control-Allow-Origin','http://frank.com:9990')
    response.write(fs.readFileSync('./public/friends.json'))
    response.end()
  }
```
