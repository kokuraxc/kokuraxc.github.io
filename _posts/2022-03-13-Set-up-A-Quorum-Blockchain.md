> Setup a basic working instance of F network consisting of multiple Quorum nodes with Tessera, CLI and Cakeshop.

## Install WSL

```cmd
wsl --install -d Ubuntu
```

## Set up Quorum Developer Quickstart


I'm seting up a Quorum blockchain using the [Quorum Developer Quickstart](https://consensys.net/docs/goquorum//en/latest/tutorials/quorum-dev-quickstart/).

1. Install Node.js and npm.
```sh
sudo apt-get update
sudo apt-get install nodejs npm
```
The above command installed the default Node.js included with Ubuntu 20.04, which, however, is now unsupported and unmaintained. Use the [following command](https://github.com/nodesource/distributions/blob/master/README.md) to install the 16.x LTS version

```sh
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
sudo apt-get install -y nodejs
```

2. Install docker
```sh
# 1. Set up the repository

# 1.1 Update the apt package index and install packages to allow apt to use a repository over HTTPS:
sudo apt-get update
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

# 1.2 Add Docker’s official GPG key:
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# 1.3 Use the following command to set up the stable repository. 
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# 2. Install Docker Engine

# 2.1 Update the apt package index, and install the latest version of Docker Engine and containerd, or go to the next step to install a specific version:
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io

# 3. Verify that Docker Engine is installed

# 3.1 Check if the Docker Engine is running
sudo service docker status

# 3.2 Start the Docker Engine
sudo service docker start

# 3.3 Run the hello-world image
sudo docker run hello-world
```
3. Install Docker Compose
```sh
# 1. Install pip
sudo apt install python3-pip

# 2. Install Docker Compose
sudo pip install docker-compose
```
4. Install Truffle
```sh
npm install truffle -g
```
5. Run Quorum Developer Quickstart without installation
```sh
npx quorum-dev-quickstart
```
A `quorum-test-network` will be created. Run *run.sh* to start the test network.
- The above command will not run correctly, saying *this script requires docker daemon to run. start docker and try again*. The cause is now `docker` can only be run with `sudo`. Follow the following steps to remove the `sudo`. 
```sh
# 1. Create the docker group.
sudo groupadd docker
# 2. Add your user to the docker group.
sudo usermod -aG docker $USER
# 3. Activate the changes to groups.
newgrp docker
# 4. Verify that you can run docker commands without sudo.
docker run hello-world
``` 
6. Now run `run.sh`.
```sh
*************************************
Quorum Dev Quickstart
*************************************
----------------------------------
List endpoints and services
----------------------------------
JSON-RPC HTTP service endpoint                 : http://localhost:8545
JSON-RPC WebSocket service endpoint            : ws://localhost:8546
Web block explorer address                     : http://localhost:25000/
Prometheus address                             : http://localhost:9090/graph
Grafana address                                : http://localhost:3000/d/a1lVy7ycin9Yv/goquorum-overview?orgId=1&refresh=10s&from=now-30m&to=now&var-system=All
```

## Configure Cakeshop

Cake shop is not bundled in Quorum Developer Quickstart.

1. [Set up java first](https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-ubuntu-20-04)
   1. Install JRE/JDK first.
    ```
    sudo apt update
    java -version
    sudo apt install default-jre
    sudo apt install default-jdk
    ```
   1. Set up `JAVA_HOME`
    ```
    sudo update-alternatives --config java
    sudo nano /etc/environment
    # Append JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64"
    source /etc/environment
    echo $JAVA_HOME
    ```
2. Set up Cakeshop
   1. Download the latest release from [github](https://github.com/ConsenSys/cakeshop/releases)
   2. Run the file with `java -jar cakeshop.war`
   3. Navigate to http://localhost:8080
   4. In case the node is not automatically configured, ADD NODE with Geth RPC Url http://localhost:8545
   5. Can find the peers' info in PEERS tab

## Interact using Geth

1. Install *geth* [Install on Ubuntu via PPAs](https://geth.ethereum.org/docs/install-and-build/installing-geth#install-on-ubuntu-via-ppas)
```sh
# To enable our launchpad repository run:
sudo add-apt-repository -y ppa:ethereum/ethereum

# Then install the stable version of go-ethereum:
sudo apt-get update
sudo apt-get install ethereum
```
2. Attach to a node
```sh
geth attach http://localhost:8545
```



