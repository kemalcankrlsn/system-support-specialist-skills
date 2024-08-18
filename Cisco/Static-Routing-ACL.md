LOOPBACK:
Router> enable
Router# configure terminal
Router(config)# interface loopback 0
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit
Router# copy running-config startup-config

SHOW:
show ip route
show ip arp
show access-lists
show ip nat translations
show processes cpu
show memory statistics
show ip name-servers
show interfaces

Router# debug ip packet
Router# debug ip routing




ROUTER 2 PC ARASI VMWARE İLE İLETİŞİM
IP Yapılandırmalarım şu şekilde
Router1: 
gi1 = 192.168.41.1 (esxi0 network) Sanal ağ
gi2 = 192.168.1.21 (WAN Network 192.168.1.1 gateway internet çıkışı) bridge internet bağlantısı var
esxi0 host = 192.168.41.11 (esxi0 network)

Router1(config)# ip route 192.168.42.0 255.255.255.0 192.168.1.22
Router1(config)# ip route 0.0.0.0 0.0.0.0 192.168.1.1

Router1(config)# access-list 1 permit 192.168.41.0 0.0.0.255 
Router1(config)# access-list 1 permit 192.168.42.0 0.0.0.255 
Router1(config)# ip nat inside source list 1 interface gi2 overload


Router2: 
gi1 = 192.168.42.1 (esxi1 network) Sanal ağ
gi2 = 192.168.1.22 (WAN Network 192.168.1.1 gateway internet çıkışı, bridge internet bağlantısı var)
esxi1 host = 192.168.42.11 (esxi1 network)

Router2(config)# ip route 192.168.41.0 255.255.255.0 192.168.1.21
Router2(config)# ip route 0.0.0.0 0.0.0.0 192.168.1.1

Router2(config)# access-list 1 permit 192.168.42.0 0.0.0.255
Router2(config)# access-list 1 permit 192.168.41.0 0.0.0.255
Router2(config)# ip nat inside source list 1 interface gi2 overload

