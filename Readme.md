# Hello World Ansible Container

## Introduction

Hello World to Ansible Container. (This thing is quirky during install.. 😩)

Added `docker-squash`. This allows your cleanup roles to take effect. Squashes `hello-world-go` image from 409MB to 8.19MB

```bash
REPOSITORY                               TAG                 IMAGE ID            CREATED              SIZE
hello-world-hello-world-go               latest              869edfe2d61b        About a minute ago   8.19MB
hello-world-hello-world-go               20180712170425      4e10bafeac41        2 minutes ago        409MB
```

## Contents

- [Install](#install)
- [Build](#build)
- [Run](#run)
- [References](#references)
- [Debug Later](#debug-later)

## Install

```bash
# Downgrade.. so things work..
sudo pip install -U pip==9.0.3 docker==2.7.0
sudo pip install "ansible-container[docker]" docker-squash
```

## Build

```bash
ansible-container build
docker-squash hello-world-hello-world-go

# The sleep just gives time for ansible to fully cleanup and commit everything
sleep 30
docker tag $(docker images -f since=hello-world-hello-world-go -q) hello-world-hello-world-go:latest
```

## Run

```bash
docker run -it --rm hello-world-hello-world
docker run -it --rm hello-world-hello-world-go
```

## References

- [container.yml spec](https://docs.ansible.com/ansible-container/container_yml/reference.html)
- [ansible.cfg spec](https://raw.githubusercontent.com/ansible/ansible/devel/examples/ansible.cfg)

## Debug Later

```bash
# Not sure if this is needed or not
# sudo pip install --upgrade setuptools
# sudo pip3 install pip-tools==2.0.1
# https://github.com/jazzband/pip-tools/issues/648

# FAILS
# conductor centos:7 (`/_usr/bin/python` does not exist)
# SUCCEEDS
# conductor alpine:3.5

# Why do we have to downgrade python deps..
```
