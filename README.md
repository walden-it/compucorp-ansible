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

Now you will have a new directory: 

/opt/compucorp/compucorp-ansible


Look at ansible.cfg inside that directory:


```ini
[defaults]
private_key_file=../key.pem
remote_user=ubuntu
inventory=ec2.py
host_key_checking=False
vault_password_file=../vault.pwd

```

## Setting up SSH key and ansible vault file

If I haven't provided the key.pem and the vault.pwd, please ask it through email.

this files needs to be placed in:

```
/opt/compucorp/key.pem
/opt/compucorp/vault.pwd

```

## Setting up AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY
You will need to let ansible find your aws credentials in order to manage your ec2 instances for the test


```
export AWS_ACCESS_KEY_ID="XXX"
export AWS_SECRET_ACCESS_KEY="XXX"

```

## Running ansible and creating the instance for the test
Now you are ready to run the ansible playbook that will create and configure the instance for this test

```
cd compucorp-ansible
ansible-playbook site_aws.yml
```
