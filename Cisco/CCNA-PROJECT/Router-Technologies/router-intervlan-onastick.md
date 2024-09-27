Configure Inter-Vlan Routing - Router On A Stıck

Router on a Stick yapılandırması, bir router ile birden fazla VLAN'ın yönlendirilmesini sağlamak için kullanılan bir tekniktir. Bu yapılandırmada, bir router'ın tek bir fiziksel arayüzü üzerinde alt arayüzler (sub-interfaces) oluşturulur ve her alt arayüz bir VLAN'a atanır. Bu sayede router, tek bir fiziksel bağlantı üzerinden birden fazla VLAN arasında yönlendirme yapabilir.

## Router İnterVLAN - Router On A Stick
#Router on a Stick------------>
sw tarafı
Switch(config)#int fa0/1
Switch(config-if)#switchport mode trunk 

router tarafı
int açma
Router(config)#int gi0/0
Router(config-if)#no sh

1.SUB İNT 
Router(config)#int gi0/0.10 ---
Router(config-subif)#encapsulation dot1Q 10 --- 
Router(config-subif)#ip address 192.168.10.1 255.255.255.0
Router(config-subif)#exit

2.SUB İNT 
Router(config)#int gi0/0.20 ---
Router(config-subif)#encapsulation dot1Q 20 --- 
Router(config-subif)#ip address 172.16.20.1 255.255.255.0
Router(config-subif)#exit
<---------------------------------
> Burada router bacağı üzerinden sub interfaceler oluşturduk ve vlanler arası geçişi açtık
Özet
Switch'te VLAN'lar oluşturun.
Switch portunu trunk mode'a alın.
Router'da alt arayüzler oluşturun ve her VLAN için bir IP adresi atayın.
PC'lere uygun IP adresleri atayın ve gateway adreslerini doğru yapılandırın.




