Vagrant/Ansible script for Alfresco Community on Ubuntu 16 Xenial
=================================================================

I created these scripts/configurations to set up a virtual box with Alfresco Community Edition for demo and evaluation purposes.
Maybe you find it useful, feel free to adopt it to your needs.
Please look up prerequisites in official manuals, if you are not familiar with [Vagrant](https://www.vagrantup.com/docs/getting-started/) yet.
Basically you'll need Vagrant, Virtual Box and SSH (Windows users most likely need an ssh client callable by "ssh" in path.)

What it does
------------
* creates a virtual box machine with Ubuntu 16.04 LTS (Xenial Xerus, 64bit server, configured to 4GB RAM)
* downloads [Alfresco Community Edition 201605 Installer] (https://community.alfresco.com/docs/DOC-6296-community-file-list-201605-ga)
* executes the installer with preselected options (Tomcat, PostgreSQL, SOLR, ...)
* installation directory is /home/ubuntu/alfresco
* adds service to systemd for autostart at boot

How to init
------------
* place the contents of this project in a new directory
* edit the Vagrant-file: replace the stated IP according to your network
* "vagrant up"
* wait... (can be time consuming for the first time as it downloads the VM template image, packages and Alfresco Installer)
* VM reboots automatically after installation
* open an internet browser on your host computer and check out the admin-pages (replace IP again):
    * http://192.168.50.100:8080/share
	* it can take a while for calling the page the first time
    * login with user/password: admin/noproblemo
* have fun with Alfresco Community Edition

How to stop
------------
* "vagrant ssh"
* stop server in the VM:
    * sudo systemctl stop alfresco.service
* exit the VM
* "vagrant halt"
	
How to start the next time
--------------------------
* "vagrant up"
* wait (not as long as the first time)

TODO
-------
Sometimes after a restart of the VM the Alfresco login can't validate the credentials. (Not sure about the root cause yet...)