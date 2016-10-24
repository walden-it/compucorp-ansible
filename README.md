# Compucorp skill test

## Pre-requisites

You will need to install git in order to be able to install this piece of software

```
apt-get install git
```

## Ansible Installation and Configuration

First, you need to install ansible in the computer you will want to use to manage the ansible client (usually, yours)

To do this effectively, you need to run:

```
sudo apt-get update
sudo apt-get install software-properties-common
sudo apt-add-repository ppa:ansible/ansible
sudo apt-get update
sudo apt-get install ansible
```

### Setup

You will create a working directory, such as: /opt/compucorp

```
sudo mkdir /opt/compucorp
```

Change to that working directory:

```
sudo cd /opt/compucorp
```

Now, you need to clone this repo:

```
sudo git-clone https://github.com/walden-it/compucorp-ansible.git  

```


