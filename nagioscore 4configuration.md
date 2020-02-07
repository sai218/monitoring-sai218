## nagios core 4 configuration.

### installation has completed.

### let's knows config file info.
  *  **_nagios.cfg_:**  it contains logs, config info, resource, and other information about nagios.
  *  **_resource.cfg_:** it will hold user and passwd info user.
  *  **_htpasswd.users_:**  it will hold user and passwd info nagios.
   *  **_commands.cfg_:** it has reusable commands for checks of host.
   *  **_contacts.cfg_:** it has contact info about users and group link user name , emailids etc.
   *  **_timeperiods.cfg_:** it is reusable time period for communicating into hosts.
   *  **_localhost.cfg_:** By using this file, we can rewrite config files for new hosts(nodes).

   ```
   root@ip-172-31-81-146:/usr/local/nagios/etc/objects#
     cp localhost.cfg host2.ip-172-31-40-165.ec2.internal.cfg

   Open host2.ip-172-31-40-165.ec2.internal.cfg
   then, change where localhost into ur host's pvt dns name.

   root@ip-172-31-81-146:/usr/local/nagios/bin#

      ./nagios -v /usr/local/nagios/etc/nagios.cfg

   restart nagios:
    service nagios restart
    or
    systemctl restart nagios

  iN nagios.cf:
    cfg_dir=/usr/local/nagios/etc/dbservers
    cfg_dir=/usr/local/nagios/etc/appservers


   ```

 
