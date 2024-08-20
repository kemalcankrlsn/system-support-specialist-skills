ACL Access Control List
Switch(config)#access-list 100 permit ip 192.168.1.0 0.0.0.255 any
Switch(config)#access-list 100 deny ip any any
Switch(config)#int vlan 10
Switch(config-if)#ip access-group 100 in