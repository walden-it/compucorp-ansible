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

If I haven't provided the vault.pwd, please ask it through email.

this files needs to be placed in:

```
/opt/compucorp/key.pem (this is the private key of the aws IAM keypair)
/opt/compucorp/vault.pwd

```

## Configuring the ec2 launch in the ansible playbook

```
- name: Provision a set of instances
       ec2:
         ec2_region: us-east-1
         key_name: keypairname
         group: service

```

you need to edit the region and the key_name based on your aws settings

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

That will take a long while, as it needs to launch a fresh new ec2 instance, and configure the test site 

## Setup local hosts file

Once it is finished, you need to get the IP for the new instance by running:

```
./ec2.py --list|grep ec2_ip_address

```

Example Output:
"ec2_ip_address": "54.161.67.61", 

Add the following line to your hosts file (in linux: /etc/hosts)


```
54.161.67.61 test.compucorp.com

```

### Installation is done
Now you need to point your browser to:
http://test.compucorp.com
and 
login using the credentials provided through email

