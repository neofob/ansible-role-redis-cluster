redis-cluster
=============
*Set up a redis cluster*

`#WIP`, being tested on DigitalOcean droplets.


Requirements
------------


Role WorkFlow
-------------
* Add `chris-lea` repo
* Install `redis-server, redis-sentinel`
* Update config files using template for server and sentinel
* Restart server and sentinel

* 1st Pass on master
* 2nd Pass on replicas


Example Playbook
----------------
```
---
- hosts: redis_master
  roles:
    - ../ansible-role-redis-cluster

- hosts: redis_replica
  vars:
    - redis_replicaof: "redis-master 6379"
  roles:
    - ../ansible-role-redis-cluster
```

DigitalOcean droplets are tagged `redis_master` and `redis_replica`
for `master` and `replicas` respectively.

Role Variables
--------------

Dependencies
------------


Role Play Options
-----------------
  * `redis_master`: Setup server as master
  * `redis_replicator`: Setup server(s) as replicaof the above master

Tags
----
  * `configuration`: Setup configuration
  * `install`: Install `redis-{server,sentinel}`

License
-------

MIT

Author Information
------------------

*tuan at vt dot edu*
