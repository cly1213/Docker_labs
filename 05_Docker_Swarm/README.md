# 05_Docker_Swarm

```
$ vagrant status
Current machine states:

swarm-manager             running (virtualbox)
swarm-worker1             running (virtualbox)
swarm-worker2             running (virtualbox)

This environment represents multiple VMs. The VMs are all listed
above with their current state. For more information about a specific
VM, run `vagrant status NAME`.
```

```
$ docker node ls
ID                            HOSTNAME        STATUS    AVAILABILITY   MANAGER STATUS   ENGINE VERSION
vacxwf4no9almbnnyq7nfl3l7 *   swarm-manager   Ready     Active         Leader           20.10.7
ikv9xk5h7l45yk0z8edo13hd6     swarm-worker1   Ready     Active                          20.10.7
u0jyfrmh3vx22idxt0muw4vm2     swarm-worker2   Ready     Active                          20.10.7
```
