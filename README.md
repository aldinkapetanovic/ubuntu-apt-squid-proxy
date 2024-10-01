# Access the running ubuntu container

```sh
docker compose exec ubuntu bash
```

# Install packages

```sh
apt update
apt install iputils-ping telnet curl iproute2
```

```sh
echo 'Acquire::http::Proxy "http://squid:3128/";' > /etc/apt/apt.conf.d/99proxy
echo 'Acquire::https::Proxy "http://squid:3128/";' >> /etc/apt/apt.conf.d/99proxy
```