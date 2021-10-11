# JHipster Demo

**Install JHipster Apps**
---

### Intall JHipster Apps

1. Copy remove repository
```shell
git clone https://github.com/ilovecorea/jhipster-demo.git jhipster
```

2. Intall generator-jhipster
```shell
npm install -g generator-jhipster
jhipster --version
INFO! Using JHipster version installed globally
7.3.0
```

3. Run import-jdl generator
```shell
jhipster import-jdl apps.jh
```

### Deploy Monitoring using docker-compose

1. Create a subfolder for the docker-compose
```shell
mkdir docker-compose
cd docker-compose
jhipster docker-compose
```

2. Configuration details
```shell
? Which *type* of application would you like to deploy? Microservice application
? Which *type* of gateway would you like to use? JHipster gateway based on Spring Cloud Gateway
? Enter the root directory where your gateway(s) and microservices are located ../
3 applications found at /Users/heedong.kang/IdeaProjects/jhipster-demo/

? Which applications do you want to include in your configuration? blog, gateway, store
? Which applications do you want to use with clustered databases (only available with MongoDB and Couchbase)? store
? Do you want to setup monitoring for your applications ? Yes, for metrics only with Prometheus
Consul detected as the service discovery and configuration provider used by your apps
🐳  Welcome to the JHipster Docker Compose Sub-Generator 🐳
```

**Build & Run Docker**
---

### Build docker images
```shell
for i in blog gateway store
do 
cd $i 
./mvnw package -Pprod -Papi-docs verify jib:dockerBuild -DskipTests
cd ..
done
```

### Run docker-compose
```shell
docker-compose  up
```

**Reference**
---

* https://developer.okta.com/blog/2019/09/26/get-started-elk-stack
