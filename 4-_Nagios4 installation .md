
Nagios 4 installation 
1) Take ubuntu 16 t2 micro name as nagios3 all traffic and connect instance 

   apt-get update 
   
     
 2) Now install nagios4 
	
   To install nagios 4 follow this Link 
   
https://support.nagios.com/kb/article/nagios-core-installing-nagios-core-from-source-96.html#Ubuntu

===== Ubuntu 16.x / 17.x =====
	
	sudo apt-get update
    sudo apt-get install -y autoconf gcc libc6 make wget unzip apache2 php libapache2-mod-php7.0 libgd2-xpm-dev
	
Downloading the Source
	
    cd /tmp
    wget -O nagioscore.tar.gz https://github.com/NagiosEnterprises/nagioscore/archive/nagios-4.4.5.tar.gz
    tar xzf nagioscore.tar.gz
	
Compile
	
    cd /tmp/nagioscore-nagios-4.4.5/
    sudo ./configure --with-httpd-conf=/etc/apache2/sites-enabled
    sudo make all
 

Create User And Group
This creates the nagios user and group. The www-data user is also added to the nagios group.

    sudo make install-groups-users
    sudo usermod -a -G nagios www-data
 

Install Binaries
This step installs the binary files, CGIs, and HTML files.

   sudo make install
 

   Install Service / Daemon
This installs the service or daemon files and also configures them to start on boot.

    sudo make install-daemoninit
 

Information on starting and stopping services will be explained further on.

 

Install Command Mode
This installs and configures the external command file.

    sudo make install-commandmode
 

Install Configuration Files
This installs the *SAMPLE* configuration files. These are required as Nagios needs some configuration files to allow it to start.

     sudo make install-config
 

Install Apache Config Files
This installs the Apache web server configuration files and configures Apache settings.

    sudo make install-webconf
    sudo a2enmod rewrite
    sudo a2enmod cgi
 

Configure Firewall
You need to allow port 80 inbound traffic on the local firewall so you can reach the Nagios Core web interface.

    sudo ufw allow Apache
    sudo ufw reload
 

Create nagiosadmin User Account
You'll need to create an Apache user account to be able to log into Nagios.

The following command will create a user account called nagiosadmin and you will be prompted to provide a password for the account.

     sudo htpasswd -c /usr/local/nagios/etc/htpasswd.users nagiosadmin


 Start Apache Web Server
   
===== Ubuntu 15.x / 16.x / 17.x /18.x =====

Need to restart it because it is already running.

    sudo systemctl restart apache2.service
	
Start Service / Daemon

===== Ubuntu 15.x / 16.x / 17.x / 18.x =====

sudo systemctl start nagios.service
   
Test Nagios
Nagios is now running, to confirm this you need to log into the Nagios Web Interface.

Point your web browser to the ip address or FQDN of your Nagios Core server, for example:

http://10.25.5.143/nagios

http://core-013.domain.local/nagios

You will be prompted for a username and password. The username is nagiosadmin (you created it in a previous step) and the password is what you provided earlier.

Once you have logged in you are presented with the Nagios interface. Congratulations you have installed Nagios Core.

BUT WAIT ...
Currently you have only installed the Nagios Core engine. You'll notice some errors under the hosts and services along the lines of:

(No output on stdout) stderr: execvp(/usr/local/nagios/libexec/check_load, ...) failed. errno is 2: No such file or directory 
These errors will be resolved once you install the Nagios Plugins, which is covered in the next step.

 

Installing The Nagios Plugins   


Prerequisites
Make sure that you have the following packages installed.

sudo apt-get install -y autoconf gcc libc6 libmcrypt-dev make libssl-dev wget bc gawk dc build-essential snmp libnet-snmp-perl gettext
 

Downloading The Source
cd /tmp
wget --no-check-certificate -O nagios-plugins.tar.gz https://github.com/nagios-plugins/nagios-plugins/archive/release-2.2.1.tar.gz
tar zxf nagios-plugins.tar.gz
 

Compile + Install
cd /tmp/nagios-plugins-release-2.2.1/
sudo ./tools/setup
sudo ./configure
sudo make
sudo make install
 

Test Plugins
Point your web browser to the ip address or FQDN of your Nagios Core server, for example:

http://10.25.5.143/nagios

http://core-013.domain.local/nagios

Go to a host or service object and "Re-schedule the next check" under the Commands menu. The error you previously saw should now disappear and the correct output will be shown on the screen.

 

Service / Daemon Commands

===== Ubuntu 15.x / 16.x / 17.x / 18.x =====

sudo systemctl start nagios.service
sudo systemctl stop nagios.service
sudo systemctl restart nagios.service
sudo systemctl status nagios.service
   
   
Add one node to nagios:

In nagios master go to this path as follows:

root@ip-172-31-27-14:~# cd /usr/local/nagios/
root@ip-172-31-27-14:/usr/local/nagios# ls
bin  etc  libexec  sbin  share  var

root@ip-172-31-27-14:/usr/local/nagios/etc# ls
cgi.cfg  htpasswd.users  nagios.cfg  objects  resource.cfg

open vi nagios.cfg

add as follows at directory 

/usr/local/nagios/etc/sai218


create one directory under /etc 

root@ip-172-31-27-14:/usr/local/nagios/etc# mkdir sai218

now we need to copy localhost.cfg to our new directory location i.e sai218 as follows:

root@ip-172-31-27-14:/usr/local/nagios/etc# ls

cgi.cfg  htpasswd.users  nagios.cfg  objects  resource.cfg  sai218

now copy commands:


root@ip-172-31-27-14:/usr/local/nagios/etc# cp objects/localhost.cfg sai218/ip-172-31-22-106.us-west-2.compute.internal.cfg

now you will see or node cfg file in sai218 directory

now edit that file i.e sai218/ip-172-31-22-106.us-west-2.compute.internal.cfg

root@ip-172-31-27-14:/usr/local/nagios/etc/sai218# vi ip-172-31-22-106.us-west-2.compute.internal.cfg

     replace address with our private i.p of node 

     replace in all places where ever local_host with private dns of node 	 
	 
root@ip-172-31-27-14:/usr/local/nagios/etc/sai218# cd ..
root@ip-172-31-27-14:/usr/local/nagios/etc# cd ..
root@ip-172-31-27-14:/usr/local/nagios# ls
bin  etc  libexec  sbin  share  var

now we should go to bin 

root@ip-172-31-27-14:/usr/local/nagios# cd bin/
root@ip-172-31-27-14:/usr/local/nagios/bin# ls
nagios  nagiostats
     
Now to see whether or node added or not follow:

root@ip-172-31-27-14:/usr/local/nagios/bin# ./nagios -v /usr/local/nagios/etc/nagios.cfg


	  
	  it will show warnings 0 and errors 0 
	  
	  Then node is added to reflect this to nagios server type 
	  
	  service nagios restart
	  
	
	
