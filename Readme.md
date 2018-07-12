# Hello World Ansible Container

## Introduction

Hello World to Ansible Container. (This thing is quirky.. 😩)

## Contents

- [Install](#install)
- [Build](#build)
- [Run](#run)
- [References](#references)
- [Debug Later](#debug-later)

## Install

```bash
sudo pip install -U pip==9.0.3
sudo pip install "ansible-container[docker]"
```

## Build

```bash
ansible-container --debug build
```

## Run

```bash
docker run -it --rm hello-world-hello-world
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
# ansible-container build
# SUCCEEDS
# ansible-container --debug build

# FAILS
# conductor centos:7 (`/_usr/bin/python` does not exist)
# SUCCEEDS
# conductor alpine:3.5
```
