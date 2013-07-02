stack-ruby-base
===============

rvm+rubyインストール済みのEC2インスタンスを構築します。

Usage
=====

## Install vagrant plugin
```
$ vagrant plugin install vagrant-aws
$ vagrant plugin install vagrant-omnibus
$ vagrant plugin install vagrant-berkshelf

$ vagrant plugin list
vagrant-aws (0.2.2)
vagrant-berkshelf (1.3.2)
vagrant-omnibus (1.1.0)
```

## Install vagrant box
```
$ vagrant box add dummy https://github.com/mitchellh/vagrant-aws/raw/master/dummy.box
```
https://github.com/mitchellh/vagrant-aws/blob/master/README.md#quick-start

## git clone & bundle install
```
$ https://github.com/arukoh/stack-ruby-base.git
$ cd stack-ruby-base
$ bundle install
```

## Edit Vagrantfile
* aws configuration
 * https://github.com/mitchellh/vagrant-aws/blob/master/README.md#configuration
* ruby version to install
 * https://github.com/fnichol/chef-rvm#-attributes

## Vagrant up
```
$ vagrant up --provider=aws
```
