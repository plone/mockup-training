Vagrant Installation
====================

Installtion via downloading binaries
------------------------------------

Go to `Vagrant's download page <https://www.vagrantup.com/downloads>`_,
download and install.


Fedora Linux
------------

For Fedora Linux, there is no official package for Vagrant. Instead of
downloading binaries from the internet, use `this community maintained
repository <http://copr.fedoraproject.org/coprs/jstribny/vagrant-f20/>`_ on Fedora Linux 20::

    $ sudo -s
    $ cd /etc/yum.repos.d/
    $ wget http://copr.fedoraproject.org/coprs/jstribny/vagrant-f20/repo/fedora-20/jstribny-vagrant-f20-fedora-20.repo
    $ yum update
    $ yum install vagrant


