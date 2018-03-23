# docker-activemq

```
git clone https://github.com/victorskl/docker-activemq.git
cd docker-activemq
mkdir -p data
mkdir -p log
touch .env   [Or cp -v env.sample .env]
docker-compose -p dev up -d
```