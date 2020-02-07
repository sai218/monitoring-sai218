## Service Status
 * OK
 * Warning
 * Critical
 * Pending
 ### while change _state_ is hard/soft state:
* Check_intervels       10m  
* Retry_intervels       1m  
* Max_retry_intervel    5 times

 ```
 
7:00
       Server up
       Hard status :UP
7: 10
    Server down
7:11
    Re-check
    Attempt1
    Soft
7:12 
    Re-check
    Attempt2
    Soft
7:13
    Re-check
    Attempt3
    Soft
7:14
    Re-check
    Attempt4
    Soft
7:15
    Re-check
    Attempt5
    Hard status : down




 ```



### nagios terms

*  Contacts 
*  hosts
*  services
*  contact groups
*  host groups
*  service groups
*  command 
