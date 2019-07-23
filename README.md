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
# redis_cluster.yml
- hosts: '{{ target }}'
  become: yes
  roles:
    - ../ansible-role-redis-cluster
```
DigitalOcean droplets are tagged `master` and `replicas` for `master` and `replicas`.
**1st Pass for master node:**
```
$ ansible-playbook -i ./digital_ocean.py -e target=master ./redis_cluster.yml
```
**2nd Pass for replicas:**
```
$ ansible-playbook -i ./digital_ocean.py -e target=replicas ./redis_cluster.yml
```
**TODO:**
  * Apply variables for master/replicas.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

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
