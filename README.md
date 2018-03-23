# alpine-chrome

基于alpine构建的chromium及chromedriver的dcoker容器

## 如何运行

### 启动chrome浏览器

>  通过websocket与浏览器API接口通信

```
docker run -d -v /data/chrome/:/data/chrome/ -p 9222:9222 ainow/alpine-chrome  --headless --no-sandbox --disable-gpu
```


### 启动chromedriver

> 通过http接口来与chrome的API通信
--whitelisted-ips设置允许哪些IP来访问chromedriver
```
docker run -d -v /data/chrome/:/data/chrome/ -p 9515:9515 ainow/alpine-chrome  --whitelisted-ips=192.168.110.128,127.0.01 --verbose --log-path=/tmp/chromedriver.log
```


