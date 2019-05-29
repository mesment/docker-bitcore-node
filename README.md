# docker-bitcore-node
This Docker container sets up
a [Bitcore Node](https://github.com/bitpay/bitcore/tree/master/packages/bitcore-node)
which is a REST API server that replaces Insight API. While Bitcore Node is
compatible with multiple cryptocurrencies, this Docker container is configured
for Bitcoin Cash (BCH).

Details about running this container can be found on my blog:
http://troutsblog.com/research/bitcore-node-insight-api

## Installation
It's assumed that you are starting with a fresh installation of Ubuntu 18.04
LTS on a 64-bit machine.
It's also assumed that you are installing as
a [non-root user with sudo privileges](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04).

- Install Docker on the host system.
[This tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04)
shows how to install Docker on a Ubuntu 16.04 system. It's specifically targeted
to Digital Ocean's cloud servers, but should work for any Ubuntnu system.

- Install Docker Compose too.
[This tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-docker-compose-on-ubuntu-16-04)
shows how to do so on a Ubuntu system.

- Ensure you have a fully-synced BCH full node running on the same machine with
ports 8332 (p2p) and 8333 (RPC) exposed.
This [docker-abc](https://github.com/christroutner/docker-abc) docerized
full node will do exactly this.

- Clone this repository in your home directory with the following command:
`git clone https://github.com/christroutner/docker-bitcore-node`

- Customize the [bitcore.config.json](bitcore.config.json) file to reflect
the setting of your full node.

- Build the docker container.
`docker-compose build --no-cache`

6. Bring the container online by running the following command:
`docker-compose up -d`


## Docker Debugging
The following commands are useful for debugging applications like this one
inside a Docker container. The commands below help you to enter a shell
inside the container.

* `docker ps -a`
  * Show all docker processes, including ones that are stopped.

* `docker container run --name test-container --rm -it <Image ID> bash`
  * This command will run a docker container and drop you into a bash shell.
  All you need is the image ID.

* `docker exec -it <container ID> bash`
  * This command will let you enter a bash shell inside a running Docker container.
