vagrant-ansible-lamp
----------------------

This is a simple recipe for *vagrant* that sets up an Ubuntu virtual machine including common daemons and tools required for PHP web development.

Specifically this recipe automatically installs:

- Ubuntu trusty64
- PHP 5.5
- MySQL
- adminer
- asset comilation tools
    - compass
    - node.js

Instead, this recipe runs `ansible` in its "local" mode (using `-c local`). As a result, you don't have to install ansible on the host machine. See `ansible/provision.sh` for details.

To get started, install

- Vagrant (http://www.vagrantup.com/)
- VirtualBox (https://www.virtualbox.org/)

preferably in their latest versions from the web sites.

Then clone this repository to a local directory. After changing into the directory, run:

    vagrant up

This should download, run and provision the virtual machine.

If you need only the LAMP stack pass `--tags lamp` against the playbook.
    
    ansible-playbook -c local /vagrant/ansible/playbook.yml --tags lamp

If something goes wrong, have a look at `ansible/playbook.yml`, which contains the provisioning recipe. You can re-provision the VM using:

    vagrant provision

After bringing up the virtual machine, open this url in your browser: http://192.168.33.44/. You should be greeted by the `phpinfo()` output from public/index.php.

    - Adminer: http://192.168.33.44/adminer.php
        - user: vagrant
        - password: vagrant

When you're done playing with the VM, you can delete it:

    vagrant destroy
