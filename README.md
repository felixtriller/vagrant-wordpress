Vagrant WordPress
=================

A development environment for WordPress developers in a virtual machine, managed by [Vagrant](http://www.vagrantup.com/) and provisioned by [Chef solo](http://docs.opscode.com/chef_solo.html).

Installation
------------

Install [Vagrant 1.2.x](http://docs.vagrantup.com/v2/installation/index.html).

Install [VirtualBox](http://www.virtualbox.org/).

Clone this repository and init submodules:

    $ cd [repo]
    $ git submodule init
    $ git submodule update

Launch the virtual machine with:

    $ vagrant up

Settings
--------

By default, the WordPress cookbook installs the latest version of WordPress to `/var/www`. To change this, edit the relevant section in the Vagrantfile. For further documentation see the README of the [WordPress cookbook](https://github.com/opscode-cookbooks/wordpress).

    :wordpress => {
      :version    => "latest",
      :dir        => "/var/www",
      :db => {
        :database   => "wordpress",
        :user       => "wordpress",
        :password   => "wordpress"
      }
    }

The MySQL root password is set to `vagrant`.

Installed software by default
-----------------------------

 * Apache2 with PHP
 * MySQL
 * Git and Subversion
 * latest version of WordPress
