## Etherchannel Yapılandırılması

1. Etherchannel Modları:
2. No Protocol
3. PAgP için:
desirable: Portun aktif şekilde PAgP teklifi göndermesini sağlar.
auto: PAgP teklifini bekleyen moddur.
4. LACP için:
active: Portun aktif şekilde LACP teklifi göndermesini sağlar.
passive: LACP teklifini bekleyen moddur.


## Yapılandırma:
### No Protocol - Statik Yapılandırma
Switch(config)#interface range gigabitEthernet 0/1-2
Switch(config-if-range)#channel-group 1 mode on 
> 2 siwtch de de ilgili portları mode on yaptık




## SHOW Komutları
Switch#show spanning-tree 
Switch#show etherchannel summary 
Switch#show etherchannel port-channel  --- load balancer
Switch#show interfaces etherchannel ---- etherchannele bağlı portların durumları
Switch#show interfaces port-channel 1 --- yapılandırılmış etherchannel özellikleri
