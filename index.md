## How to write auto startup script for the servers

In this tutorial we will show you the script for the liferay server.

To write this script performs the following steps

### Open the following location
```markdown
/etc/init.d
```

### Create on file with the name Liferay
```markdown
touch liferay
```

### Open this file
```markdown
nano liferay
```

### Write following code in this file
```markdown
#!/bin/bash 
TOMCAT_HOME=${liferay_home_path}/tomcat-7.0.62/bin 
START_TOMCAT=${liferay_home_path}/tomcat-7.0.62/bin/startup.sh 
STOP_TOMCAT=${liferay_home_path}/tomcat-7.0.62/bin/shutdown.sh 
 
start() { 
 echo -n "Starting tomcat: " 
 cd $TOMCAT_HOME 
 ${START_TOMCAT} 
 echo "done." 
} 
 
stop() { 
 echo -n "Shutting down tomcat: " 
 cd $TOMCAT_HOME 
 ${STOP_TOMCAT} 
 echo "done." 
} 
 
case "$1" in 
start) 
 sleep 10 
 start 
 ;;  
 
stop) 
 stop 
 ;;  
 
restart) 
 stop 
 sleep 10 
 start 
 ;; 
 *) 
 
echo "Usage: $0 {start|stop|restart}" 
esac 
exit 0 
```

### Give 755/775 permission to execute
```markdown
chmod 755 liferay
```

### Add liferay in chkconfig
```markdown
chkconfig --add liferay
```

### Check the list of literary
```markdown
chkconfig --list liferay
```

### It will give following output
```markdown
liferay        0:off   1:off   2:on    3:on    4:on    5:on    6:off 
```

### Now you can use the following commands to start/stop/restart the Liferay server.
### To start the Liferay server
### 
```markdown
service liferay start
```

### To stop the Liferay server
```markdown
service liferay stop
```
### To restart the Liferay server
```markdown
service liferay restart
```
