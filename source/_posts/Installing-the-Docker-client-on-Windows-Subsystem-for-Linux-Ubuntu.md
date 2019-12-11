---
title: Installing the Docker client on Windows Subsystem for Linux (Ubuntu)
date: 2017-09-25 20:09:25
tags:
- Docker
- 部署
- VPS
- Ubutun
- WSL
- Window 10
---
{% asset_img '1.png' %}
I'm a PC guy, I have always been. I played around a little bit with Linux back in the university days, but that was it.

But now, Windows brought Linux a little closer. I don't have to do anything complicated like dual booting or having another computer set up just to experience the Linux (non GUI) environment.

As a Windows Insider, I tried the Windows Subsystem for Linux since day 1 and I really enjoyed it.

Now that Falls Creators Update is out, I'm using the Ubuntu distro from the store, and the first thing I want to do is having the Docker client installed.. It is not rocket science, but I did have some bumps on the road (because of my pretty low knowledge of Linux), so I thought I'd write what I've done to achieve that, in case it could be useful to somebody else.

There's something you need to understand first. The Docker Engine does not run on WSL, you HAVE to have Docker For Windows installed on your host machine. What we'll end up with at the end of this document is the Docker client running on Linux (WSL) sending commands to your Docker Engine daemon installed on Windows.

So, open you Ubuntu bash console, the first thing is to install the client. In order to do that you have to use apt-get, which is Ubuntu's package manager (more info about apt here).

Update the apt package index:
$ sudo apt-get update

## 2. Install packages to allow apt to use a repository over HTTPS:

  $ sudo apt-get install \
  apt-transport-https \
  ca-certificates \
  curl \
  software-properties-common


## 3. Add Docker’s official GPG key:

  $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

Verify that you now have the key with the fingerprint 9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88, by searching for the last 8 characters of the fingerprint.

  $ sudo apt-key fingerprint 0EBFCD88

pub 4096R/0EBFCD88 2017–02–22
 Key fingerprint = 9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88
uid Docker Release (CE deb) <docker@docker.com>
sub 4096R/F273FCD8 2017–02–22

## 4. Use the following command to set up the stable repository. You always need the stable repository, even if you want to install builds from the edge or test repositories as well. To add the edge or test repository, add the word edge or test (or both) after the word stable in the commands below.

  $ sudo add-apt-repository \
  “deb [arch=amd64] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) \
  stable”

Now we're ready to install Docker Community Edition

## 5. Update the apt package index again

  $ sudo apt-get update

## 6. And install Docker CE

  $ sudo apt-get install docker-ce

When that finishes, you'll end up having everything installed in Linux, but as I mentioned before, the Docker Engine does not run in WSL so if you write any command like docker images, you'll see a message like this one:

Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?
No, it is not running and it'll never be, at least for now.

You need to tell the Docker client where the Docker host is, and you can do that by using the -H option as follows:

  $ docker -H localhost:2375 images

If you don't want to type the host every time, you can set up and environment variable called DOCKER_HOST to localhost:2375

  $ export DOCKER_HOST=localhost:2375

Now just running docker images will show the images in your host environment.

But, that environment variable will last only as long as the session does. You would have to set it every time you open bash. So, in order to avoid that, you set that variable in a file called .bash_profile in your home directory, like this:

  $ echo “export DOCKER_HOST=localhost:2375” >> ~/.bash_profile

Restart the bash console and the DOCKER_HOST variable should be there, just type docker images to check everything is there.

I hope this post will help other, if it does, let me know.

EDIT: Make sure you expose the daemon on Windows, otherwise it won't work.
{% asset_img '2.png' %}


References: Get Docker CE for Ubuntu

Special thanks to Rich Turner for his kindness and patience.

EDIT: I recently learned there's an official, more complicated but secure, way of achieving the same, so I thought I'd share it here: WSL Interoperability with Docker

