### Commands used: 

# Checking firewall status:
``` sudo systemctl status firewalld ```

# 1. Blocking reddit.com ip address:
```
sudo firewalld-cmd  \
--permanent  \
--add-rich=”rule family=’ipv4’ \
-- source address=’192.232.45.148’  \
reject “

```

# Restarting the firewall:

```
 sudo firewalld-cmd --reload
 
 ```

# Listing the updated firewall rules: 
```
sudo  firewall-cmd --list-all

```



# 2. Allowing ssh,http and https in the firewall

Used Commands: 
```
sudo firewall-cmd --zone=public --permanent -add-service =ssh
sudo firewall-cmd --zone=public --permanent -add-service =https
sudo firewall-cmd --zone=public --permanent -add-service =http

```

