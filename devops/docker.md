# Docker

#### Install Docker

```text
sudo apt update

sudo apt install apt-transport-https ca-certificates curl software-properties-common

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"

apt-cache policy docker-ce

sudo apt install docker-ce

sudo systemctl status docker
```

#### Add to Docker Swarm

```text
docker swarm init --advertise-addr 188.40.137.111
```

> Console Output

```text

Swarm initialized: current node (ki5af3abdtn6kv9fvpkftdo5x) is now a manager.

To add a worker to this swarm, run the following command:

    docker swarm join --token SWMTKN-1-3fgrsv7gfx3hvbc07eldaktyqufm8ege472nn3d6ii6xmv9per-05hiyc40d5r6qffijw06aqwzt 188.40.137.111:2377

To add a manager to this swarm, run 'docker swarm join-token manager' and follow the instructions.
```



