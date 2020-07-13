# nexus私服搭建


```
wget https://sonatype-download.global.ssl.fastly.net/repository/downloads-prod-group/3/nexus-3.24.0-02-unix.tar.gz

tar -xf  nexus-3.24.0-02-unix.tar.gz 


cd nexus-3.24.0-02/bin

./nexus  start

ps aux |grep nexus


lsof -i:8081
```

# maven 

```

mvn  clean  deploy 

```

