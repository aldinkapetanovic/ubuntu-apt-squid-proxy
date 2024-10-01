# Proxy apt traffic via squid

## Start the whole thing

```sh
cd ubuntu-apt-proxy-squid
docker compose up -d
```

## Check logs on ``squid`` container

From ``your terminal``, 

```sh
docker compose logs squid -f
```

## Access the running ``ubuntu`` container

```sh
docker compose exec ubuntu bash
```

### Install packages on ``ubuntu`` container

```sh
apt update
apt install iputils-ping telnet curl iproute2
```

### Test from ``ubuntu`` container

```sh
curl http://nginx
```

```sh
ip -br -c a
```

## Test2
From ``your web browser`` open nginx container

http://localhost:8080


## Stop ``squid`` container
From ``your terminal``

```sh
docker compose stop squid
```

## Check that proxy for apt is not working on ``ubuntu`` container

```sh
apt update
ping google.com
```

<!-- 
```sh
echo 'Acquire::http::Proxy "http://squid:3128/";' > /etc/apt/apt.conf.d/99proxy
echo 'Acquire::https::Proxy "http://squid:3128/";' >> /etc/apt/apt.conf.d/99proxy
``` -->