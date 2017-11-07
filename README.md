# Chat Deploy - Ansible

> Ansible configuration management for standing up a complete Oberon stack

See [oberon.im](http://oberon.im) for more details about the application.

## About

Oberon runs on top of:

- Ubuntu 16.04
- PostgreSQL
- LetsEncrypt for SSL
- Nginx

## Installation

**Note**: Target architecture is Ubuntu 16.04.

#### Initial Setup

Follow the [Ansible Installation Guide](https://docs.ansible.com/ansible/intro_installation.html) to install the latest version of Ansible locally.

Clone the project locally:

```bash
$ git clone git@github.com:oberon-chat/chat-deploy-ansible.git
$ cd chat-deploy-ansible
```

Copy the inventory file and update the values:

```bash
$ cp hosts/production.example hosts/production
$ vim hosts/production
```

Copy group var files:

```bash
$ cp group_vars/all.yml.example group_vars/all.yml
$ cp group_vars/client.yml.example group_vars/client.yml
$ cp group_vars/server.yml.example group_vars/server.yml
```

(Optional) Review and update group var values:

```
$ vim group_vars/all.yml
$ vim group_vars/client.yml
$ vim group_vars/server.yml
```

Transfer and run the bootstrap script for each remote host:

```bash
$ scp bin/bootstrap example.com:~/
$ ssh example.com "./bootstrap"
```

Confirm ansible can connect and run on the host:

```bash
$ bin/ping
```

#### Running Playbooks

To configure the client and server run:

```bash
$ bin/configure
```

Review and update configuration values:

```bash
$ vim configs/client
$ vim configs/server
```

Build and deploy the server:

```bash
$ bin/install
```
