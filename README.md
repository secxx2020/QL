
# 组织基地：QQ群1021185005
# 青龙面板拉库命令
``````
ql repo https://ghproxy.net/https://github.com/smallfawn/QLScriptPublic.git  backup  main
``````
自用青龙docker搭建命令
``````
#老版青龙(2.11.3)搭建命令
docker run -dit \
  -v $PWD/ql/config:/ql/config \
  -v $PWD/ql/log:/ql/log \
  -v $PWD/ql/db:/ql/db \
  -v $PWD/ql/repo:/ql/repo \
  -v $PWD/ql/raw:/ql/raw \
  -v $PWD/ql/scripts:/ql/scripts \
  -p 5700:5700 \
  --name qinglong \
  --hostname qinglong \
  --restart unless-stopped \
  yanyu.icu/whyour/qinglong:2.11

version: '3'
services:
  qinglong:
    image: yanyu.icu/whyour/qinglong:2.11
    container_name: qinglong
    hostname: qinglong
    volumes:
      - $PWD/ql/config:/ql/config
      - $PWD/ql/log:/ql/log
      - $PWD/ql/db:/ql/db
      - $PWD/ql/repo:/ql/repo
      - $PWD/ql/raw:/ql/raw
      - $PWD/ql/scripts:/ql/scripts
    ports:
      - 5700:5700
    restart: unless-stopped

https://github.com/whyour/qinglong/tree/d6614acf66a243fddc494bcfcee44b3a55020591
``````
#最新版青龙搭建命令
``````
docker run -dit \
-v $PWD/ql:/ql/data \
-p 5600:5700 \
-e TZ=Asia/Shanghai \
--dns 114.114.114.114 \
--name qinglong \
--hostname qinglong \
--no-healthcheck \
--restart always \
whyour/qinglong
