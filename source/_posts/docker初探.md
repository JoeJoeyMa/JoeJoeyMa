---
title: docker初探
date: 2017-09-12 21:38:27
tags:
- docker
- Linux
- 虚拟机
- 搭建
- VPS
- 管理

---
## Docker CE 还是 Docker EE


Docker在2016年很早的时候就明确了将会在企业级方面重点跟进。而在短短的一年时间之内推出的1.12和1.13的版本在功能上确实是很大的进步。而在2017年的3月1号之后，Docker的版本命名开始发生变化，同时将CE版本和EE版本进行分开，而这些也是突然发现docker1.13的安装脚本不好用了才发现的，一起简单来看一下具体情况吧。

## 平台支持

目前docker的CE和EE所支持的平台情况如下所示，大家所钟情的Ubuntu和CentOS作为Linux发行版所支持的CE和EE均支持的。 
{% asset_img '1.JPG' %}

## Get Started, Part 1: Orientation and setup


Welcome! We are excited that you want to learn Docker. The _Docker Get Started Tutorial_
teaches you how to:

1.  Set up your Docker environment (on this page)
2.  [Build an image and run it as one container](/get-started/part2/)
3.  [Scale your app to run multiple containers](/get-started/part3/)
4.  [Distribute your app across a cluster](/get-started/part4/)
5.  [Stack services by adding a backend database](/get-started/part5/)
6.  [Deploy your app to production](/get-started/part6/)

## Docker concepts

Docker is a platform for developers and sysadmins to **develop, deploy, and run**
applications with containers. The use of Linux containers to deploy applications
is called _containerization_. Containers are not new, but their use for easily
deploying applications is.

Containerization is increasingly popular because containers are:

*   Flexible: Even the most complex applications can be containerized.
*   Lightweight: Containers leverage and share the host kernel.
*   Interchangeable: You can deploy updates and upgrades on-the-fly.
*   Portable: You can build locally, deploy to the cloud, and run anywhere.
*   Scalable: You can increase and automatically distribute container replicas.
*   Stackable: You can stack services vertically and on-the-fly.

{% asset_img '2.png' %}
### Images and containers

A container is launched by running an image. An **image** is an executable
package that includes everything needed to run an application–the code, a
runtime, libraries, environment variables, and configuration files.

A **container** is a runtime instance of an image–what the image becomes in
memory when executed (that is, an image with state, or a user process). You can
see a list of your running containers with the command, `docker ps`, just as you
would in Linux.

### Containers and virtual machines

A **container** runs _natively_ on Linux and shares the kernel of the host
machine with other containers. It runs a discrete process, taking no more memory
than any other executable, making it lightweight.

By contrast, a **virtual machine** (VM) runs a full-blown “guest” operating
system with _virtual_ access to host resources through a hypervisor. In general,
VMs provide an environment with more resources than most applications need.


## Prepare your Docker environment

Install a maintained version of Docker Community Edition (CE) or Enterprise Edition (EE) on a supported platform.

Ensure that you have a supported version of Docker:

'''$ docker --version
Docker version 17.12.0-ce, build c97c6d6

'''
{% asset_img '2.JPG' %}
{% asset_img '3.JPG' %}