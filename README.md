# centos-6-64 lxc + ruby + janus

Provides a Vagrantfile to build and package a minimal centos-6-64 lxc container
with ruby 2.1.10 and janus vim distribution.

The centos-6-64 base image is provided by
https://atlas.hashicorp.com/fgrehm/boxes/centos-6-64-lxc

## Build

``` sh
[simple-lxc]$ vagrant up
```

## Package

``` sh
[simple-lxc]$ vagrant package --output centos-6-64-lxc.box
```

## Add

``` sh
[simple-lxc]$ vagrant box add cheyneb/centos-6-64-lxc centos-6-64-lxc
```

## Using the Box

### Configure Vagrantfile

Create a Vagrantfile with the following configuration -

``` sh
Vagrant.configure(2) do |config|
  config.vm.box = "cheyneb/centos-6-64-lxc"
end
```

### Start Container

``` sh
[simple-lxc]$ vagrant up
```
