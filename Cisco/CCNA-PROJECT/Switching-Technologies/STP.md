## STP (Spanning Tree Protocol)
1. Root Bridge Seçimi: Tüm switch'ler arasında en düşük Bridge ID'ye sahip olan switch, root bridge olarak seçilir. Bridge ID iki bileşenden oluşur:
    - Bridge Priority (Varsayılan: 32768)
    - MAC Adresi Root bridge, ağda veri trafiğinin merkezini belirler. MAC adresi en düşük olan kaybeder



## STP Root Bridge Yapılandırılması (İstenilen SWitch Root Olarak Yapılandırma)
Switch(config)#spanning-tree vlan 1 root primary --- root belirleme
Switch(config)#spanning-tree vlan 1 root secondary  ---- root dan sonra gelecek cihaz belirleme

Normalde gerçek hayatta
Switch(config)#spanning-tree vlan 1 priority 0
Switch(config)#spanning-tree vlan 1 priority 4096 
ve 4096 nın katlarında gidiyoruz.
root switch kapandıktan sonra tekrar online olduğunda tekrar root luğu alıyor.

## RSTP Yapılandırılması:
Switch(config)#spanning-tree mode rapid-pvst --- normal stp yapılandırılmasında bir bağlantı koptuğundan 50 saniyelik gecikme yaşanıyor rapid-pvst de bu gecikme yaşanmıyor.

## Portfast VE Bpduguard
Switch(config)#interface fastEthernet 0/10 --- interface seçtik
Switch(config-if)#spanning-tree portfast --- 
Switch(config-if)#spanning-tree bpduguard enable --- 
> Şimdi pvst yapılandırma olan portlarda switchlerde porta istemci pc client takıldığından gecikme yaşanıyor bu gecikme yaşanmaması için portfast diyoruz bu portu hızlandırıyoruz yani rapid pvst yapıyoruz bu uygulamayı yaptıktan sonra bu porta switch hub takıldığı zaman loop olmaması için bpduguard enable diyoruz bu porta switch takıldığında portu kapatıyor.
> Switch hub takıldığı zaman port down oluyor portu tekrar açmak için

Switch(config)#int fa0/10
Switch(config-if)#shutdown
Switch(config-if)#no shutdown 

yaparak portu tekrar açıyoruz.

## show
1. Switch#sh spanning-tree --- stp görüntüleme root switch hangisi 
