## Oracle Express Edition 11g Release 2 on Ubuntu 14.04.1 LTS

[![Build Status](https://travis-ci.org/nguoianphu/docker-oracle-xe-11g.svg?branch=master)](https://travis-ci.org/nguoianphu/docker-oracle-xe-11g) [![](https://images.microbadger.com/badges/image/nguoianphu/docker-oracle-xe-11g.svg)](http://microbadger.com/images/nguoianphu/docker-oracle-xe-11g "Get your own image badge on microbadger.com")

#### Cloned from wnameless/oracle-xe-11g

This Dockerfile is a trusted build of Docker Registry.

### Installation

```
docker pull nguoianphu/docker-oracle-xe-11g
```

### Run with ports 22 and 1521 on container AND map them to ports 49160 and 49161 on host machine:

``` 
docker run -d -p 49160:22 -p 49161:1521 nguoianphu/docker-oracle-xe-11g 
```

### Connect database with following setting:

```
hostname: localhost
port: 49161
sid: xe
username: system
password: oracle
```
### Password for SYS & SYSTEM

``` oracle ```

### Login by SSH

``` 
ssh root@localhost -p 49160
password: admin
```

### Windows client

Search, download and install this

```
Oracle Database 11g Release 2 Client (11.2.0.1.0) for Microsoft Windows
```

Open

``` C:\app\nguoianphu\product\11.2.0\client_1\network\admin\tnsnames.ora ```

Add this

```
xe =
  (DESCRIPTION =
    # (ADDRESS = (PROTOCOL = TCP)(HOST = 192.168.59.103)(PORT = 49161))
    (ADDRESS = (PROTOCOL = TCP)(HOST = 127.0.0.1)(PORT = 49161))
    (CONNECT_DATA =
      (SERVER = DEDICATED)
      (SERVICE_NAME = xe)
    )
  )
```
Connect

``` sqlplus system/oracle@xe ```
