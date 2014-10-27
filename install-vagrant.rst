Vagrant Installation
====================

Installtion via downloading binaries
------------------------------------

Go to `Vagrant's download page <https://www.vagrantup.com/downloads>`_,
download and install.


Installation
------------

This instructions are based on the `plonedev.vagrant README.rst
<https://github.com/plone/plonedev.vagrant/blob/master/README.rst>`_. Have a
look for it, if you need more information and troubleshooting instructions.

1. Install VirtualBox: https://www.virtualbox.org

2. Install Vagrant: http://www.vagrantup.com

3. If you are using Windows, install the Putty ssh kit: http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html. Install all the binaries, or at least putty.exe and plink.exe.

4. Clone the Mockup repository: `git clone https://github.com/plone/mockup`.

5. Open a command prompt; change directory into the `mockup` directory. Run "vagrant up".

6. Go for lunch or a long coffee break. "vagrant up" is going to download a
   virtual box kit (unless you already happen to have a match installed). On
   Windows, it will also generate an ssh key pair that's usable with Putty.

7. Look to see if the install ran well. The virtual machine should be running
   at this point.

8. Change to the mockup directory within the virtual machine: `cd /mockup`.

While running "vagrant up", feel free to ignore messages like "stdin: is not a
tty" and "warning: Could not retrieve fact fqdn". They have no significance in
this context.


Debian / Ubuntu Linux
---------------------

Install vagrant from the official repository sources, if available::

    $ sudo apt-get install vagrant


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


