# Ansible Hands-on

## Description

This repository is used by hands-on session at Okinawa Open Days.


## Playbooks

### create_instance.yml

Create virtual machine instance with Google COmpute Engine.

#### Arguments

- hostname: set system's host name

#### Examples

1) create testserver on Google Compute Engine

```
$ ansible-playbook -i hosts -e "hostname=testserver" playbooks/gce/create_instance.yml 
```

### launch_container.yml

Pull and launch docker container on target system.

#### Requirements

- python docker-py module
- dynamic-inventory program for Google Compute Engine


#### Arguments

- hostname: target host name of Ansible
- tag: tag name of Dockerimage

#### Examples

1) Pull docker images and launch image v1.0 on testserver

```
$ ansible-playbook -i ./gce.py -e "hostname=testserver" -e "tag=v1.0" playbooks/gce/launch_container.yml
```

2) Launch image v1.1 on testserver

```
$ ansible-playbook -i ./gce.py "hostname=testserver" -e "tag=v1.1" -t start playbooks/gce/launch_container.yml
```

### stop_container.yml

Stop running container

#### Requirements

- python docker-py module
- dynamic-inventory program for Google Compute Engine

#### Arguments

- hostname: target host name of Ansible

#### Examples

1) Stop running container on testserver

```
$ ansible-playbook -i ./gce.py -e "hostname=testserver" playbooks/gce/stop_container.yml 
```

### switch_container.yml

Stop running container and launch new container

#### Requirements

- python docker-py module
- dynamic-inventory program for Google Compute Engine

#### Arguments

- hostname: target host name of Ansible
- tag: tag name to launch image

#### Examples

1) Stop running container and launch v1.1 container on testserver

```
$ ansible-playbook -i ./gce.py -e "hostname=testserver" -e "tag=v1.1" playbooks/gce/switch_container.yml 
```

