---
layout: post
title: "Windows, Docker and Virtualbox"
date: 2017-03-22 21:27:48 +0000
categories: docker
---

## Docker on windows when  you run virtual machines is a pain.

Various problems:

1. You need to install hypervisor
2. Hypervisor vm's use a shit ui because they won't allow dynamically resizing
3. Hypervisor messed with vt-x which for some reason seems to stop Virtual box working.

## Solution:

Just use it in an ubuntu vm ...
so [as per here](https://docs.docker.com/engine/installation/linux/ubuntu/#os-requirements)

```bash
sudo apt-get update && sudo apt-get install
sudo apt-get remove docker docker-engine
sudo apt-get install \
   apt-transport-https \
   ca-certificates \
   curl \
   software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88 `should equal 9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88`
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
sudo apt-get update
sudo apt-get install docker-ce
`now run the hello world example`
sudo docker run hello-world

```

Don't know why I didn't just do that months ago.
Wonder when i will get around to some [kubernetes](https://kubernetes.io/)
