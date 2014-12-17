Dynamic set NTP or DNS based on destination IP
=========

Ansible playbook to dynamic set NTP or DNS based on client/server destination IP.

Role Variables
--------------

Edit the /var/main.yml file and change the IPs of your `dns` or `ntp` servers.
Base on the first 2 octets of the IP the client/server has, it will configure the settings.

in case the 1st 2 octets does not suits your needs, change the template regex.


## Variables
#### Variables for resolv
```
nameserverXX: 192.168.x.x 
nameserverXY: 192.169.x.x 
```
#### Variables for ntp
```
ntpserver1: ntp1.domain.local
ntpserver2: ntp2.domain.local
ntpserver3: ntp3.domain.local
```

#### Example code for ntp j2
```Jinja2
{% if "192.168" in ansible_all_ipv4_addresses[0].split(".")[0:2]|join(".")  %}
server {{ ntpserver1 }}  iburst
server {{ ntpserver2 }}  iburst
server {{ ntpserver3 }}  iburst
```


Supported platforms
--------------
RedHat/CentOS 6.x

License
-------

MIT

Author Information
------------------
alens
