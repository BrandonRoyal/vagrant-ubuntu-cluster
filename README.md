Vagrant Virtualbox setup for Docker EE Engine on Ubuntu Xenial 16.04
========================

This vagrant file is provided strictly for demonstration purposes to help setup a cluster environment that installs HAProxy for loadbalancing, Docker EE, UCP, and DTR. This can be used as a demo environment on your local machine, when internet access is not present.

After running `vagrant up`:
- UCP will be accessible from `https:\\ucp.local`
- DTR will be accessible from `https:\\dtr.local`

This template will also setup the VMs with static ip addresses as follows (if IP addresses are already in use, change them inside of the Vagrantfile):
- `haproxy` (HAProxy LB): 172.28.128.30
- `ucp-node1` (UCP manager node): 172.28.128.31
- `ucp-node2` (UCP manager node2): 172.28.128.32
- `ucp-node3` (UCP manager node3): 172.28.128.33
- `dtr-node1` (DTR replica): 172.28.128.34
- `worker-node1` (Worker node): 172.28.128.35


## Download vagrant from Vagrant website

```
https://www.vagrantup.com/downloads.html
```

## Install Virtual Box

```
https://www.virtualbox.org/wiki/Downloads
```

## Download Ubuntu Xenial box
```
$ vagrant init ubuntu/xenial64
```

## Create files in project to store environment variables with custom values for use by Vagrant
```
ee_url
ucp_password
```

## Provide Docker EE license in project folder
```
docker_subscription.lic
```

## Install [vagrant-landrush](https://github.com/vagrant-landrush/landrush) plugin
```

$ vagrant plugin install landrush
$ vagrant plugin install vagrant-hostsupdater
$ vagrant plugin install vagrant-multiprovider-snap
```

## Bring up nodes

```
$ vagrant up haproxy ucp-node1 ucp-node2 ucp-node3 dtr-node1 worker-node1
# Flush Mac's DNS cache
$ sudo killall -HUP mDNSResponder
```

## Stop nodes

```
$ vagrant halt haproxy ucp-node1 ucp-node2 ucp-node3 dtr-node1 worker-node1
```

## Destroy nodes

```
$ vagrant destroy haproxy ucp-node1 ucp-node2 ucp-node3 dtr-node1 worker-node1
```

## Snapshot nodes

```
$ vagrant snapshot save ucp-node1 ucp-node1-snapshot
```
