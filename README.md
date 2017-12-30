
# docker-redis

<p>alpine redis checked</p>
<p>官网的方式用器Dockerfile文件运行是验证起不来的，按照redis安装简单调整</p>
<p>Docker version 1.12.6, build 88a4867/1.12.6</p>
<p>的编译版本没问题</p>
<p>升级后的</p>
<p>Docker version 1.12.6, build ec8512b/1.12.6</p>
<p>此版本各种问题，其他镜像运行也是如此，有必要自己定制编译docker</p>
<p>Connection reset by peer</p>
<p>有必要通过COPY 命令复制进去。</p>

## 修改的地方
<p>//redis.conf</p>
<p>#bind 127.0.0.1  #开启外部访问</p>
<p>protected-mode no #关闭保护模式</p>
<p>dir /data #指定工作路径</p>

## 更小的install方式
<p>等待调试</p>
