[![devops](https://img.shields.io/badge/DevOps-Jenkins-green)](http://github.com/ZuoGuocai)


#  理念


![image](https://raw.githubusercontent.com/ZuoGuocai/devsecops/master/images/pipeline.gif)

![image](https://raw.githubusercontent.com/ZuoGuocai/devsecops/master/images/pipeline.JPG)


[devops 元素周期表](https://devops.phodal.com/)
[devops flow](https://www.processon.com/view/5d1ea322e4b05dcb4397732e?fromnew=1)

# 导航
[code3721](https://www.code3721.com/nav/devops.html)

# Jira 禅道 和 confluence


#  蒲公英 内测分发平台


# npm private repository

https://github.com/cnpm/cnpmjs.org


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


[maven environment](https://blog.csdn.net/hongweigg/article/details/54091148)
```

mvn  clean  deploy 



```
# mvnw 
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

 > pipeline as code

# argo  gocd  Drone CI  blueking ci


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
[jenkins pipeline Jenkinsfile](https://www.jenkins.io/zh/doc/book/pipeline/jenkinsfile/#usernames-and-passwords)

```
# githook
[使用 Githook 实现团队 Coding Review 流程](https://www.jianshu.com/p/935409ce4c9a)
[gitbook](https://imweb.io/topic/5b13aa38d4c96b9b1b4c4e9d)

# Git

[通过web学习git](https://learngitbranching.js.org/?demo=&locale=zh_CN)

try.github.io

https://lab.github.com/

geektime.com

《玩转Git三剑客》
[分支管理](https://www.liaoxuefeng.com/wiki/896043488029600/900005860592480)

# harbor 

docker registry


# Gerrit

一种免费、开放源代码的代码审查软件，使用网页界面。利用网页浏览器，同一个团队的软件程序员，可以相互审阅彼此修改后的程序代码，决定是否能够提交，退回或者继续修改。


# k8s

https://kuboard.cn/

```
k8s 最佳实践
```
# docker


docker 最佳实践
```
https://blog.windrunner.me/sa/docker-best-practice.html

```

#  Sentry 

是一个开源的实时错误追踪系统,可以帮助开发者实时监控并修复异常问题。它主要专注于持续集成、提高效率并且提升用户体验

> build config

[ - ]  .gitlab-ci.yml
[ - ]  Dockerfile
[ - ]  Jenkinsfile
[ - ]  setting.xml
[ - ]  pom.xml
[ - ]  build.gradle
[ - ]  build.xml
[ - ]  docker-compose.yml

>  ignore config
```
使用 .dockerignore
docker 在构建过程中会把同目录中的所有 .dockerignore 和 Dockerfile 以外的文件打包发给镜像， 在文件过多时这会很耗时间。

.gitignore

.npmignore

```
# 冲突解决


git 解决冲突
[maven 解决冲突](https://blog.csdn.net/jhon07/article/details/88292065)


idea 解决冲突
https://juejin.im/post/5cf3815ce51d45777540fd5a


# IDE 插件

Java 内存泄露分析，JProfile 

阿里云代码规范

https://developer.aliyun.com/special/tech-java

https://github.com/alibaba/p3c

[参考文档](https://zhy.readthedocs.io/Backgroud/JavaEE/README/)


[arthas 诊断]

https://help.aliyun.com/document_detail/112975.html?spm=a2c4g.11186623.6.594.47382352JBIOGs

# Alibaba Cloud

https://help.aliyun.com/document_detail/30515.html?spm=a2c4g.11174283.2.8.23091a2fBVUrS6


# doc management

- docsify

- showdoc

- mkdoc

#  flywaydb
```
Flyway是一个简单开源数据库版本控制器（约定大于配置），主要提供migrate、clean、info、validate、baseline、repair等命令。它支持SQL（PL/SQL、T-SQL）方式和Java方式，支持命令行客户端等，还提供一系列的插件支持（Maven、Gradle、SBT、ANT等）。

官方网站：https://flywaydb.org/
```

# 各个平台
[android](https://www.jianshu.com/p/38b2e17ced73)

- 交付物

|platform|type|
|:----:|:-----:|
|ios|ipa|
|android|apk|
|java|jar,war|
|npm|dst|

ios
# keywords

- gitflow   
- gitops

[gitflow](https://mritd.me/2018/05/11/add-commit-message-style-check-to-your-gitlab/)





# Tips

```
Maven中建立的依赖管理方式基本已成为Java语言依赖管理的事实标准，Maven的替代者Gradle也基本沿用了Maven的依赖管理机制。在Maven依赖管理中，唯一标识一个依赖项是由该依赖项的三个属性构成的，分别是groupId、artifactId以及version。这三个属性可以唯一确定一个组件（Jar包或者War包）。

```


[理解Maven中的SNAPSHOT版本和正式版本](https://www.cnblogs.com/huang0925/p/5169624.html)


# demo

https://www.qikqiak.com/k8s-book/docs/66.devops.html


# 代码

[如何写出优雅的go代码](https://draveness.me/golang-101/)



#  robotframework


[robotframework](https://robotframework.org/)
