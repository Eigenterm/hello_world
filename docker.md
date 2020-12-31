# Is the docker daemon running?

when trying to

`$ docker ps`

error:

Docker: Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?

#### tried:

`sudo apt-get remove docker docker-engine docker-ce docker.io`

`sudo apt install apt-transport-https ca-certificates curl software-properties-common`

`curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`

`sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"`

`sudo apt update`

`sudo apt upgrade`

`apt-cache policy docker-ce`

`sudo apt install docker-ce`

`docker --version`

`sudo docker run hello-world`

#### failed, tried:

`systemctl status docker`

`sudo systemctl stop docker`

`sudo systemctl start docker`

`sudo systemctl enable docker`

#### failed, tried:

`ps axf | grep docker | grep -v grep | awk '{print "kill -9 " $1}' | sudo sh`

#### failed, tried:

`sudo dockerd`

then error:

failed to start daemon: pid file found, ensure docker is not running or delete /var/run/docker.pid

#### tried:

`rm -rf   /var/run/docker.pid`

`sudo dockerd`

then error:

failed to start daemon: error while opening volume store metadata database: timeout

then I found in /var/run/ directory, docker.sock disappear sometimes, and after many repeation, I tried in one terminal, run:

`systemctl status docker`

`systemctl stop docker`

`sudo dockerd`

no error like failed to start daemon: error while opening volume store metadata database: timeout

then close the terminal, in another terminal, run:

`docker ps`

succeess !
