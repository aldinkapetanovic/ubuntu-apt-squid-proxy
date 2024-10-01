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

From ``your terminal``,

```sh
docker compose exec ubuntu bash
```

### Install packages on ``ubuntu`` container

```sh
apt update
apt install -y iputils-ping telnet curl iproute2
```

### Test from ``ubuntu`` container

```sh
curl http://nginx
```

```sh
ping google.com
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
curl http://nginx
```

```
root@05973f3de24e:/# apt update
Ign:1 http://security.ubuntu.com/ubuntu noble-security InRelease
Ign:2 http://archive.ubuntu.com/ubuntu noble InRelease
Ign:3 http://archive.ubuntu.com/ubuntu noble-updates InRelease
Ign:4 http://archive.ubuntu.com/ubuntu noble-backports InRelease
Ign:1 http://security.ubuntu.com/ubuntu noble-security InRelease
Ign:2 http://archive.ubuntu.com/ubuntu noble InRelease
Ign:3 http://archive.ubuntu.com/ubuntu noble-updates InRelease
Ign:4 http://archive.ubuntu.com/ubuntu noble-backports InRelease
Ign:2 http://archive.ubuntu.com/ubuntu noble InRelease
Ign:1 http://security.ubuntu.com/ubuntu noble-security InRelease
Ign:3 http://archive.ubuntu.com/ubuntu noble-updates InRelease
Ign:4 http://archive.ubuntu.com/ubuntu noble-backports InRelease
Err:1 http://security.ubuntu.com/ubuntu noble-security InRelease
  Could not resolve 'squid'
Err:2 http://archive.ubuntu.com/ubuntu noble InRelease
  Could not resolve 'squid'
Err:3 http://archive.ubuntu.com/ubuntu noble-updates InRelease
  Could not resolve 'squid'
Err:4 http://archive.ubuntu.com/ubuntu noble-backports InRelease
  Could not resolve 'squid'
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/noble/InRelease  Could not resolve 'squid'
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/noble-updates/InRelease  Could not resolve 'squid'
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/noble-backports/InRelease  Could not resolve 'squid'
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/noble-security/InRelease  Could not resolve 'squid'
W: Some index files failed to download. They have been ignored, or old ones used instead.
```
<!-- 
```sh
echo 'Acquire::http::Proxy "http://squid:3128/";' > /etc/apt/apt.conf.d/99proxy
echo 'Acquire::https::Proxy "http://squid:3128/";' >> /etc/apt/apt.conf.d/99proxy
``` -->