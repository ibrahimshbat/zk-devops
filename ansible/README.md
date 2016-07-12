# Ansible Playbooks for ZooKeeper

## Overview
This project aims to provide a set of devops tools to make ZooKeeper configuration, deployment, testing, and operation easier through automation.

## What does it do currently
* Install and start a ZooKeeper ensemble with specified configuration settings on a list of nodes. The list of nodes could be real boxes, virtual machines, or docker / containers. All we need is for these nodes to be accessible through SSH from where this playbook will run (the control machine, typically on your dev box, or could be on a Jenkins machine.).
* The ZooKeeper source it uses is currenlty 3.5.2-alpha, and it could be customized in https://github.com/hanm/zk-devops/blob/master/ansible/role/zookeeper/zookeeper.yaml

## How to run
* Pre-requisit: Install Ansible http://docs.ansible.com/ansible/intro_installation.html
* For OS X El Capitan users, you might want to "brew install python" to workaround an issue (if the previous install guide does not work for you).
* The list of nodes where ZK will be installed can be specified in https://github.com/hanm/zk-devops/blob/master/ansible/inventory/hosts, where you put the node IP (or DNS name), the SSH username and password.
* ZooKeeper cfg file can be customized in https://github.com/hanm/zk-devops/blob/master/ansible/role/zookeeper/files/zoo.cfg
* To run the playbook, simply type 'ansible-playbook -i inventory/hosts role/zookeeper/setup.yaml'

## TODO
* Support provisioning nodes given cloud credentials (AWS, GCP, Azure) automatically. 
* Support easier customization of the workflow through a driver configuration script.
* Support more complicated cluster setup (SASL/Kerberos).
