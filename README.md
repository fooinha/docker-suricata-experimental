# docker-suricata-experimental
Dockerfiles for experimental versions of suricata 3.2

## Base Images

 - debian:sid
 
## Tags

### sid-kafka

 - Output log to Apache Kafka brokers.
 
### sid-dns-alert

 - EVE output log of metadata about DNS requests/responses with several output styles.
 
### sid-redis-async
 
 - EVE output log to redis using hiredis async API with libevent adapter.
 
### sid-yara

 - Support yara rules matching for suricata rules. Available for protocols where is possible do file extraction.


## Container contents


### Working directory

/var/log/suricata

### Packages
Built debian sid packages are placed in the /packages directory.

$ ls -lh /packages/
total 8.7M
-rw-r--r-- 1 root root 7.7M Oct 31 19:39 suricata-dbg_3.2.0-1+beta1~yara_amd64.deb
-rw-r--r-- 1 root root  27K Oct 31 19:39 suricata-oinkmaster_3.2.0-1+beta1~yara_all.deb
-rw-r--r-- 1 root root 977K Oct 31 19:39 suricata_3.2.0-1+beta1~yara_amd64.deb

### Processes running

  PID CMD
    1 /usr/bin/python /usr/bin/supervisord
    7 /usr/bin/suricata -c /etc/suricata/suricata.yaml --pidfile /var/run/suricata.pid -i eth0 --af-packet
