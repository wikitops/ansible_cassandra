# Ansible : Playbook Cassandra
The aim of this project is to deploy a simple Cassandra cluster on Vagrant with some default configuration.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

What things you need to run this Ansible playbook :

* [Vagrant](https://www.vagrantup.com/docs/installation/) must be installed on your computer
* Update the Vagrant file based on your computer (CPU, memory), if needed
* You must have download the ubuntu Xenial64 vagrant box :

```
vagrant box add https://app.vagrantup.com/ubuntu/boxes/xenial64
```

### Usage

A good point with Vagrant is that you can create, update and destroy all architecture easily with some commands.

Be aware that you need to be in the Vagrant directory to be able to run the commands.

#### Build Environment

Vagrant needs to init the project to run and build it :

```
vagrant up
```

After build, you can check which virtual machine Vagrant has created :

```
vagrant status
```

If all run like it is expected, you should see something like this :

```
$ vagrant status

Current machine states:

cassandra01                   running (virtualbox)
cassandra02                   running (virtualbox)
cassandra03                   running (virtualbox)
```

#### Deployment

To deploy the Cassandra cluster, you just have to run the Ansible playbook cassandra.yml with this command :

```
ansible-playbook cassandra.yml
```

If everything run as expected, you should connect to the server and check the status of Cassandra cluster with that command :

```
$ sudo nodetool status
Datacenter: datacenter1
=======================
Status=Up/Down
|/ State=Normal/Leaving/Joining/Moving
--  Address    Load       Tokens       Owns (effective)  Host ID                               Rack
UN  10.0.4.32  103.66 KiB  256          65.8%             d367e8ff-a502-4beb-8014-446bfd83ddaf  rack1
UN  10.0.4.33  132.56 KiB  256          65.8%             82959b5e-2d6a-4773-8540-34a3f5f5188b  rack1
UN  10.0.4.31  208.59 KiB  256          68.4%             1f206076-29e4-47b3-8be3-33b9ea7304df  rack1
```

#### Destroy

To destroy on what Vagrant has created, just run this command :

```
vagrant destroy
```

## Author

Member of Wikitops : https://www.wikitops.io/
