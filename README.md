# docker-suricata-experimental
Dockerfiles for experimental versions of suricata 3.2

## Base Images

 - debian:sid
 
## Tags

### sid-kafka

 - EVE output log to Apache Kafka brokers.
 
### sid-dns-alert

 - EVE output log of metadata about DNS requests/responses with several output styles.
 
### sid-redis-async
 
 - EVE output log to redis using hiredis async API and with libevent adapter.
 
### sid-yara

 - Support yara rules matching for suricata rules. Available for protocols where is possible do file extraction.
