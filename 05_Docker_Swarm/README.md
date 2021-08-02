# 05_Docker_swarm

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

vagrant@swarm-manager:~$ docker service create --network mynet --name test --replicas 2 busybox ping 8.8.8.8
ujfyx4jn692jaqenvcj4b0rms
overall progress: 2 out of 2 tasks
1/2: running   [==================================================>]
2/2: running   [==================================================>]
verify: Service converged

vagrant@swarm-manager:~$ docker service ps test
ID             NAME      IMAGE            NODE            DESIRED STATE   CURRENT STATE            ERROR     PORTS
7eqgythr2m2t   test.1    busybox:latest   swarm-worker2   Running         Running 8 seconds ago
hk99z211ss6a   test.2    busybox:latest   swarm-worker1   Running         Running 13 seconds ago
```

```
vagrant@swarm-worker1:~$ docker container ls
CONTAINER ID   IMAGE            COMMAND          CREATED              STATUS              PORTS     NAMES
f4f36a887f55   busybox:latest   "ping 8.8.8.8"   About a minute ago   Up About a minute             test.2.hk99z211ss6anvxqbm7jkzpmp
vagrant@swarm-worker1:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 02:24:89:67:97:c3 brd ff:ff:ff:ff:ff:ff
    inet 10.0.2.15/24 brd 10.0.2.255 scope global dynamic enp0s3
       valid_lft 83900sec preferred_lft 83900sec
    inet6 fe80::24:89ff:fe67:97c3/64 scope link
       valid_lft forever preferred_lft forever
3: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:cc:b4:f0 brd ff:ff:ff:ff:ff:ff
    inet 192.168.200.11/24 brd 192.168.200.255 scope global enp0s8
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fecc:b4f0/64 scope link
       valid_lft forever preferred_lft forever
4: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default
    link/ether 02:42:43:e4:2e:75 brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever
9: docker_gwbridge: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default
    link/ether 02:42:6b:11:ee:74 brd ff:ff:ff:ff:ff:ff
    inet 172.18.0.1/16 brd 172.18.255.255 scope global docker_gwbridge
       valid_lft forever preferred_lft forever
    inet6 fe80::42:6bff:fe11:ee74/64 scope link
       valid_lft forever preferred_lft forever
11: vethb087a36@if10: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker_gwbridge state UP group default
    link/ether 2e:88:30:43:0c:33 brd ff:ff:ff:ff:ff:ff link-netnsid 1
    inet6 fe80::2c88:30ff:fe43:c33/64 scope link
       valid_lft forever preferred_lft forever
33: vethc75d31b@if32: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker_gwbridge state UP group default
    link/ether 6a:04:4e:d8:7a:3b brd ff:ff:ff:ff:ff:ff link-netnsid 4
    inet6 fe80::6804:4eff:fed8:7a3b/64 scope link
       valid_lft forever preferred_lft forever

vagrant@swarm-worker1:~$ docker container exec -it f4f36a887f55 sh
/ # ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
30: eth0@if31: <BROADCAST,MULTICAST,UP,LOWER_UP,M-DOWN> mtu 1450 qdisc noqueue
    link/ether 02:42:0a:00:01:11 brd ff:ff:ff:ff:ff:ff
    inet 10.0.1.17/24 brd 10.0.1.255 scope global eth0
       valid_lft forever preferred_lft forever
32: eth1@if33: <BROADCAST,MULTICAST,UP,LOWER_UP,M-DOWN> mtu 1500 qdisc noqueue
    link/ether 02:42:ac:12:00:03 brd ff:ff:ff:ff:ff:ff
    inet 172.18.0.3/16 brd 172.18.255.255 scope global eth1
       valid_lft forever preferred_lft forever
/ #
```
## swarm overlay network
<img src="https://github.com/cly1213/Docker_labs/blob/main/img/overlay.png"/>

## swarm service
<img src="https://github.com/cly1213/Docker_labs/blob/main/img/swarm-ingress-service.png"/>

## swarm ingress network
<img src="https://github.com/cly1213/Docker_labs/blob/main/img/routing-mesh.png"/>

## swarm load balancer

VIP: Virtual IP
<img src="https://github.com/cly1213/Docker_labs/blob/main/img/vip.png"/>


