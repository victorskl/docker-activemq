# docker-activemq

```
git clone https://github.com/victorskl/docker-activemq.git
cd docker-activemq
mkdir -p data
mkdir -p log
touch .env   [Or cp -v env.sample .env]
docker-compose -p dev up -d
```

If setting Memory through environment does not work like below:
```
ACTIVEMQ_MIN_MEMORY=1024
ACTIVEMQ_MAX_MEMORY=4096
```

Then, copy `env` file from `activemq` container and modify `ACTIVEMQ_OPTS_MEMORY="-Xms64M -Xmx8G"` and then override using volume mounting. For example:

```
docker cp activemq:/opt/activemq/bin/env .

vi env
    ACTIVEMQ_OPTS_MEMORY="-Xms64M -Xmx8G"

vi docker-compose.yml
    volumes:
      - ./data:/data
      - ./log:/var/log/activemq
      - ./env:/opt/activemq/bin/env

ps axu|grep java      
```
