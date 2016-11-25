# ip

## Manual Configure
### RHEL/CentOS/Fedora
`/etc/sysconfig/network-scripts/ifcfg-eth0`
```
DEVICE="eth0"
BOOTPROTO=static
ONBOOT=yes
TYPE="Ethernet"
IPADDR=192.168.50.2
NETMASK=255.255.255.0
DNS1=192.168.40.2
NAME="System eth0"
HWADDR=00:0C:29:28:FD:4C
GATEWAY=192.168.50.1
```
### Ubuntu/Debian/Linux Mint
`/etc/network/interfaces`
```
auto eth0
iface eth0 inet static
address 192.168.50.2
netmask 255.255.255.0
gateway 192.168.50.1
```
### Restart
```
$ sudo nmcli connection reload
$ sudo nmcli dev disconnect eth0
$ sudo nmcli con up ifname eth0
or ALL
$ sudo systemctl restart network.service
```

## Adding or Deleting an IP Address / route
```
# ip a add 192.168.80.174/24 [broadcast 192.168.1.255] dev eth0
# ip a del 192.168.80.174 dev eth0
# ip route add default via 192.168.80.1
# ip route add 10.10.20.0/24 via 192.168.50.100 dev eth0
# ip route del 10.10.20.0/24
```
## Add MAC Hardware Address to Network Interface
```
ip link set dev eth0 address 00:0c:29:33:4e:aa
```
## Setting Other Configurations of Network Interface
```
# ip link set dev eth0 mtu 2000
# ip link set dev eth0 multicast on
# ip link set dev eth0 txqueuelen 1200
# ip link set dev eth0 promisc on
# ip link set dev eth0 allmulti on
```
## Enabling or Disabling Network Interface
```
# ip link set eth0 down
# ip link set eth0 up
```
## Enable or disable the use of ARP protocol
```
# ip link set dev eth0 arp on
```
## To undo these steps (e.g. before switching to a dynamic IP)
```
# ip addr flush dev interface    # remove ip
# ip route flush dev interface   # remove gateway
# ip link set interface down     # disable interface
```
