## Gitlab CI Playground
[![Build Status](https://travis-ci.org/rjongejan/gitlab-ci-playground.svg?branch=master)](https://travis-ci.org/rjongejan/gitlab-ci-playground)  
Set up a Gitlab CI playground with one command, using Ansible and Docker.  


### Prerequisites
Ansible
Docker

### Description
This project provides an easy way to create a local playground to experiment with Gitlab CI.  
The playground consists of 1 instance of Gitlab and 1 Gitlab CI Multi-Runner.
By default, this CI runner is configured as a 'docker'-executor.
This means that you can experiment with running CI steps in docker containers.
The Runner is so configured that it will spawn a sibling container, so you don't end up with Docker-in-Docker.


### Defaults
By default, the username and password are: root / password.

When you start the playground, it creates an example 'hello-world'-project with an example .gitlab-ci.yml file.


### How-to
To set up the playground, do the following:
```
git clone https://github.com/rjongejan/gitlab-ci-playground.git
cd gitlab-ci-playground
ansible-playbook playbook.yml
```

### Visualization
```
+-------------+    +-------------+    +-------------+
|             |    |             |    /             /
|             |    |             |    /             /
|  Gitlab     |    |  Gitlab     |    /  Gitlab CI  /
|             +--> |  CI-Runner  +--> /  Container  /
|             |    |             |    /             /
|             |    |             |    /             /
+------+------+    +------+------+    +------+------+
+------|------------------|------------------|------+
|                      Docker                       |
+---------------------------------------------------+
```
