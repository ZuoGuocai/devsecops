# nexus私服搭建


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

```
wget https://s3.amazonaws.com/gitlab-runner-downloads/master/rpm/gitlab-runner_amd64.rpm



```


# jenkins slave.jar 


```


```
