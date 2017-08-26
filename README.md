# DailyNote

### Daily Note for reference
===========
2016.5.29

* 1.pip install packages from local

use below command:
(DIR include packages(wheel, soure) you want to install)
> pip install --no-index --find-links=DIR -r requirements.txt

ref: https://pip.pypa.io/en/stable/user_guide/#installing-from-local-packages

* 2.virtualenv usage:

```Bash
pip install virtualenv
virtualenv --no-site-packages venv
cd venv
source venv/bin/activate
deactivate
```

ref: http://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/001432712108300322c61f256c74803b43bfd65c6f8d0d0000

2016.6.18
1.tmux 
ref: www.wtoutiao.com/p/g6dWTR.html
2.travis ci
ref: https://travis-ci.com/

2016.6.19
1.redis connection pool
ref: http://blog.csdn.net/chosen0ne/article/details/7319807

pool = redis.ConnectionPool(host='127.0.0.1', port=9212)
edis pipeline机制，可以在一次请求中执行多个命令，这样避免了多次的往返时延。
pool = redis.ConnectionPool(host='127.0.0.1', port=9212)  
r = redis.Redis(connection_pool=pool)  
pipe = r.pipeline()  
pipe.set('one', 'first')  
pipe.set('two', 'second')  
pipe.execute()  
  
pipe.set('one'. 'first').rpush('list', 'hello').rpush('list', 'world').execute()

2.supervisor with redis
ref: https://gist.github.com/solar/3898630

redis.ini:
[program:redis]
command=/usr/local/bin/redis-server /etc/redis.conf
autostart=true
autorestart=true
user=root
stdout_logfile=/var/log/redis/stdout.log
stderr_logfile=/var/log/redis/stderr.log

install.sh:
#!/bin/sh

version="2.6.3"
priority="20603"

sudo mkdir -p /var/redis /var/log/redis
curl -sL http://redis.googlecode.com/files/redis-${version}.tar.gz | tar zx
cd redis-${version}/
make
sudo make PREFIX=/usr/local/redis/${version} install
cd ../
sudo alternatives --install /usr/local/bin/redis-server redis /usr/local/redis/${version}/bin/redis-server ${priority} \
  --slave /usr/local/bin/redis-benchmark redis-benchmark /usr/local/redis/${version}/bin/redis-benchmark \
  --slave /usr/local/bin/redis-check-aof redis-check-aof /usr/local/redis/${version}/bin/redis-check-aof \
  --slave /usr/local/bin/redis-check-dump redis-check-dump /usr/local/redis/${version}/bin/redis-check-dump \
  --slave /usr/local/bin/redis-cli redis-cli /usr/local/redis/${version}/bin/redis-cli
sudo cp ./redis.conf /etc/redis.conf
sudo cp ./redis.ini /etc/supervisor.d/redis.ini
sudo supervisorctl reread
sudo supervisorctl add redis

2016.6.21
http://www.fullstackpython.com/

2016.6.22
http://www.csdn.net/article/2014-03-31/2819057-redis-journey-how-to-beyond-sql

2016.7.2
http://blog.jobbole.com/58003/  4个Linux服务器监控工具
https://pypi.python.org/pypi/Glances/
http://www.tecmint.com/glances-an-advanced-real-time-system-monitoring-tool-for-linux/

2017.7.29
https://juejin.im/entry/58feac9d8d6d810058a33a6f 棋牌游戏服务器架构: 总体设计

2017.8.3
http://book.pythontips.com/en/latest/index.html 开源python书籍
http://blog.csdn.net/x_r_su/article/details/54731558?locationNum=12&fps=1 python进阶必读汇总
http://cuiqingcai.com/4320.html blog
https://hungys.xyz/ 

2017.8.4
https://github.com/Microsoft/vscode-tips-and-tricks

2017.8.5
https://pan.baidu.com/share/link?shareid=2050741762&uk=2444516112
http://www.meijutt.com/content/meiju22716.html

2017.8.9
南航明珠  113430206082

https://pan.baidu.com/share/link?shareid=407177742&uk=509128973#list/path=%2F%E6%88%91%E7%9A%84%E8%B5%84%E6%BA%90%2F2016%E4%B8%AD%E5%8D%8E%E4%BC%9A%E8%AE%A1%E7%BD%91%E8%AF%81%E5%88%B8%E4%BB%8E%E4%B8%9A%E8%B5%84%E6%A0%BC%E8%A7%86%E9%A2%91&parentPath=%2F%E6%88%91%E7%9A%84%E8%B5%84%E6%BA%90

2017.8.10
http://www.sdifen.com/ithoughtsx4.html
http://blog.csdn.net/u011497262/article/details/52325705  一份非常好的Matplotlib 教程

2017.8.14
http://blog.csdn.net/google19890102/article/details/51355282

http://stackabuse.com/python-async-await-tutorial/

2017.8.15
https://imququ.com/post/http2-resource.html
https://tools.keycdn.com/http2-test
https://www.gitbook.com/book/zhongsp/typescript-handbook/details

2017.8.16
https://github.com/PyCQA/pycodestyle/issues/476  #noqa meaning
https://stackoverflow.com/questions/22190403/how-could-i-use-requests-in-asyncio 
https://pawelmhm.github.io/asyncio/python/aiohttp/2016/04/22/asyncio-aiohttp.html

2017.8.17

A "distutils.cfg" has been written to:
  /usr/local/opt/pypy/libexec/lib-python/2.7/distutils
specifying the install-scripts folder as:
  /usr/local/share/pypy

If you install Python packages via "pypy setup.py install", easy_install_pypy,
or pip_pypy, any provided scripts will go into the install-scripts folder
above, so you may want to add it to your PATH *after* /usr/local/bin
so you don't overwrite tools from CPython.

Setuptools and pip have been installed, so you can use easy_install_pypy and
pip_pypy.
To update setuptools and pip between pypy releases, run:
    pip_pypy install --upgrade pip setuptools

See: https://docs.brew.sh/Homebrew-and-Python.html
-----------------------------------------------------

http://sdiehl.github.io/gevent-tutorial/#subprocess
http://www.cnblogs.com/ajianbeyourself/p/3970603.html 使用gevent提高IO繁忙型wsgi服务的并发量（转）
https://blog.youxu.info/ 
http://www.jianshu.com/p/8d167e3bca50  MAC查看端口占用情况

http://vdoobv.com/

2017.8.18
https://www.palletsprojects.com/

2017.8.19

Here is a list of the basic Docker commands from this page, and some related ones if you’d like to explore a bit before moving on.

docker build -t friendlyname .  # Create image using this directory's Dockerfile
docker run -p 4000:80 friendlyname  # Run "friendlyname" mapping port 4000 to 80
docker run -d -p 4000:80 friendlyname         # Same thing, but in detached mode
docker ps                                 # See a list of all running containers
docker stop <hash>                     # Gracefully stop the specified container
docker ps -a           # See a list of all containers, even the ones not running
docker kill <hash>                   # Force shutdown of the specified container
docker rm <hash>              # Remove the specified container from this machine
docker rm $(docker ps -a -q)           # Remove all containers from this machine
docker images -a                               # Show all images on this machine
docker rmi <imagename>            # Remove the specified image from this machine
docker rmi $(docker images -q)             # Remove all images from this machine
docker login             # Log in this CLI session using your Docker credentials
docker tag <image> username/repository:tag  # Tag <image> for upload to registry
docker push username/repository:tag            # Upload tagged image to registry
docker run username/repository:tag                   # Run image from a registry

2017.8.21
修改账户密码
1.Linux环境下
#su  postgres 
-bash-3.2$psql -U postgres 
postgres=#alter user postgres with password 'new password';
postgres=#\q

http://www.kmeiju.net/archives/5541.html  got

2017.8.23
https://github.com/shihyu/python_ebook

2017.8.25
https://eastlakeside.gitbooks.io/interpy-zh/content/
https://mg.pov.lt/objgraph/ 内存泄漏工具
https://stackoverflow.com/questions/556405/what-do-real-user-and-sys-mean-in-the-output-of-time1

2017.8.26
intellij idea 2017
1. 到网站 http://idea.lanyus.com/ 获取注册码。

2.填入下面的license server:

　　http://intellij.mandroid.cn/
　　http://idea.imsxm.com/
　　http://idea.iteblog.com/key.php

以上方法验证均可以

kotlin
https://panxl6.gitbooks.io/kotlin-in-action-in-chinese/
https://www.kotlincn.net/docs/reference/
