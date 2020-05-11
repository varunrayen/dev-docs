---
description: setup and configuration of apache kafka
---

# Apache Kafka

## Kafka Installation

```text
sudo apt-get install -y wget net-tools netcat tar openjdk-8-jdk

wget http://apachemirror.wuchna.com/kafka/2.4.1/kafka_2.12-2.4.1.tgz

tar -xzf kafka_2.12-2.4.1.tgz

ln -s kafka_2.12-2.4.1.tgz kafka

java -version
```

### Zookeeper Service

> /etc/systemd/system/zookeeper.service

Copy file [zookeeper.service](./zookeeper.service) and store it as  
/etc/systemd/system/zookeeper.service

```text
sudo vi /etc/systemd/system/zookeeper.service
```

### Kafka Service

#### /etc/systemd/system/kafka.service

Copy file [kafka.service](./kafka.service) and store it as  
/etc/systemd/system/kafka.service

```text
sudo vi /etc/systemd/system/kafka.service
```

#### Activating the systemd scripts

```text
sudo systemctl enable zookeeper
sudo systemctl enable kafka
```

#### Services Management via systemctl

```text
sudo systemctl status zookeeper
sudo systemctl status kafka

sudo systemctl start zookeeper
sudo systemctl start kafka

sudo systemctl stop zookeeper
sudo systemctl stop kafka
```

