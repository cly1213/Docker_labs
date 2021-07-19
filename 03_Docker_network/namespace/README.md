execute commands:
```
sh add-ns-to-br.sh mydocker0 ns1 172.16.1.1/16
sh add-ns-to-br.sh mydocker0 ns2 172.16.1.2/16

sudo ip link set dev mydocker0 up

# validate
sudo ip netns list

sudo ip netns exec ns1 ip a

brctl show
```
