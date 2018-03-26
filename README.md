# alpine-chrome

基于alpine构建的chromium及chromedriver的dcoker容器

## 如何运行

### 启动chromedriver

> 通过启动chromedriver，暴露9515端口，远程连接至该端口，chromedriver会在需要的时候，自动启动chrome进程

> 通过http接口来与chrome的API通信
--whitelisted-ips设置允许哪些IP来访问chromedriver
-v /dev/shm:/dev/shm 共享主机内存，防止容器crash(session deleted because of page crash)
```
docker run -d \
-v /dev/shm:/dev/shm \
-v /data/chrome/:/data/chrome/ 
-p 9515:9515 ainow/alpine-chrome  
--whitelisted-ips=192.168.110.128,127.0.0.1 \
--verbose \
--name chromedriver
--log-path=/tmp/chromedriver.log
ainow/alpine-chrome
```

### 启动chrome浏览器

>  通过websocket与浏览器API接口通信

```
# 启动容器
docker run -d -v /data/chrome/:/data/chrome/ -p 9222:9222 ainow/alpine-chrome  

# 启动浏览器
chromium-browser --headless --no-sandbox --disable-gpu
```
