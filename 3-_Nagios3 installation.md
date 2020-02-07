
Nagios 3 installation 
1) Take ubuntu 16 t2 micro name as nagios3 all traffic and connect instance 

   apt-get update 
   
   apt-get install tasksel
   
   tasksel (press enter one window will open) 
   
   Now we have to install LAMP by pressing down arrows and press space bar to select as (*) and press tab and ok.
   
   it is ask sql passowrd type both root.
   
   to check whether lamp is installed or not type as follows:
   
   service apache2 status
   
 2) Now install nagios3 
    apt-get install nagios3
    it will ask nagios admin user and passd (sai)
	
	to check whether nagios installed or not copy public i.p of instance and paste in google like
	
	http://54.218.60.211/nagios3/
	
	then it will ask login and passwrod
	Login: nagiosadmin
	passwd: sai
	
	To add one node to the nagio3 server:
	 take one ubuntu16 server and assign all traffic.
	 now go to nagios master sever and go to as follows:
	 cd /etc/nagios3
        ls
		apache2.conf  cgi.cfg  commands.cfg  conf.d  htpasswd.users  nagios.cfg  resource.cfg  stylesheets
		
    now go to conf.d
	
	cd /conf.d
	
	now we have to copy localhost.cfg content to our nodes as follows:
	
	cp localhost_nagios2.cfg ip-172-31-31-188.us-west-2.compute.internal.cfg 
	
	                                 ( copy paste our node private dns)
    now ls
    it diplays our node added nodes with cfg
   
    now open our added node.cg file 

    vi ip-172-31-31-188.us-west-2.compute.internal.cfg
    
     replace address with our private i.p of node 

     replace in all places where ever local_host with private dns of node 	 
	 
	 after saving the file execute the command in that same path
	 
	  root@ip-172-31-30-83:/etc/nagios3/conf.d# nagios3 -v /etc/nagios3/nagios.cfg
	  
	  it will show warnings 0 and errors 0 
	  Then node is added to reflect this to nagios server type 
	  
	  service nagios3 restart
	  
	
	
