# Start the whole thing

```sh
cd ubuntu-apt-proxy-squid
docker compose up -d
```

# Access the running ``ubuntu`` container

```sh
docker compose exec ubuntu bash
```

# Install packages

```sh
apt update
apt install iputils-ping telnet curl iproute2
```
<!-- 
```sh
echo 'Acquire::http::Proxy "http://squid:3128/";' > /etc/apt/apt.conf.d/99proxy
echo 'Acquire::https::Proxy "http://squid:3128/";' >> /etc/apt/apt.conf.d/99proxy
``` -->

# Test from ``ubuntu`` container

```sh
apt update
```
```sh
curl http://nginx
```

```sh
ip -br -c a
```

# Stop ``squid`` container
From ``your terminal``

```sh
docker compose stop squid
```

# Test2
From ``your machine`` open nginx container

http://localhost:8080


# Check logs on ``squid`` container

From ``your terminal``, 

```sh
docker compose logs squid -f
```
