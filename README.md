# nexus


```
wget https://sonatype-download.global.ssl.fastly.net/repository/downloads-prod-group/3/nexus-3.24.0-02-unix.tar.gz

tar -xf  nexus-3.24.0-02-unix.tar.gz 


cd nexus-3.24.0-02/bin

./nexus  start

ps aux |grep nexus


lsof -i:8081

默认密码 cat  /var/lib/tomcats/sonatype-work/nexus3/admin.password

ulimit -n 65536



同步第三方maven  proxy模式
```

# maven 

```

mvn  clean  deploy 

```

#  sonarqube



```
yum  -y install  java-11-openjdk   java-11-openjdk-devel


yum install -y https://download.postgresql.org/pub/repos/yum/reporpms/EL-7-x86_64/pgdg-redhat-repo-latest.noarch.rpm
yum install -y postgresql12
/usr/pgsql-12/bin/postgresql-12-setup initdb
yum install -y postgresql12-server
/usr/pgsql-12/bin/postgresql-12-setup initdb
systemctl enable postgresql-12
systemctl start postgresql-12
vim  /var/lib/pgsql/12/data/pg_hba.conf

\l  查询数据库

unzip sonarqube-8.4.0.35506.zip
cat sonar.properties |grep -v "#"
sonar.jdbc.username=sonar
sonar.jdbc.password=sonar
sonar.jdbc.url=jdbc:postgresql://127.0.0.1:5432/sonar

wrapper.conf
wrapper.java.initmemory=1

默认密码 admin admin

中文插件chinese pack

[参考](https://www.cnblogs.com/throwable/p/12907785.html)
```


# gitlab runner  

- linux
```

设置----cicd

wget https://s3.amazonaws.com/gitlab-runner-downloads/master/rpm/gitlab-runner_amd64.rpm

yum -y install gitlab-runner_amd64.rpm


systemctl start   gitlab-runner

gitlab-runner  register  --tls-ca-file DigiCertCA.crt

gitlab-ci-multi-runner list

cat /etc/gitlab-runner/config.toml



[参考](https://www.funtl.com/zh/spring-cloud-itoken-ci/%E4%BD%BF%E7%94%A8-GitLab-Runner.html#%E6%B3%A8%E5%86%8C-runner)


vim /etc/gitlab/gitlab.rb

gitlab_rails['time_zone'] = 'Asia/Shanghai'



gitlab-ci.yml 

test1
test2

1和2 并列

```
- windows
```
gitlab-runner-windows-amd64.exe install

gitlab-runner-windows-amd64.exe  register

gitlab-runner-windows-amd64.exe  start

gitlab-runner-windows-amd64.exe status



```



FAQ 

```
1. gitlab CI 失败一次后 fatal: git fetch-pack: expected shallow list

- 升级git 版本 ，默认centos7 是git1.8 




2. x509: certificate signed by unknown authority.

 - 安装ca证书 update-ca-certificates
 
 
3. job 中文乱码

4. 日志时区
```



# jenkins slave  agent.jar 

gaowei.vip

```


```

# Git

geektime.com

《玩转Git三剑客》


# harbor 

docker registry


# Gerrit

一种免费、开放源代码的代码审查软件，使用网页界面。利用网页浏览器，同一个团队的软件程序员，可以相互审阅彼此修改后的程序代码，决定是否能够提交，退回或者继续修改。


# k8s


# docker

#  Sentry 

是一个开源的实时错误追踪系统,可以帮助开发者实时监控并修复异常问题。它主要专注于持续集成、提高效率并且提升用户体验

> config

[ - ]  .gitlab-ci.yml
[ - ]  Dockerfile
[ - ]  Jenkinsfile
[ - ]  setting.xml
[ - ]  pom.xml
[ - ]  build.gradle
[ - ]  build.xml
[ - ]  docker-compose.yml



# 冲突解决


git 解决冲突
[maven 解决冲突](https://blog.csdn.net/jhon07/article/details/88292065)


# IDE 插件

Java 内存泄露分析，JProfile 
