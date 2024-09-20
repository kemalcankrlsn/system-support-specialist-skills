Statik Mode "On", PAGP ve LACP protokollerinden farklıdır. İşte bu modların arasındaki farklar:

1. Statik Mode "On"
Statik yapılandırma anlamına gelir ve EtherChannel'ı müzakere etmeden zorla etkinleştirir.
Protokol kullanılmaz, yani ne PAGP ne de LACP ile müzakere yapılmaz.
Avantajı: Daha hızlı kurulabilir çünkü herhangi bir müzakere süreci yoktur.
Dezavantajı: Yedeklilik ve bağlantı denetimi yoktur. İki uç arasında uyumsuzluk varsa (örneğin, biri "On" modunda, diğeri protokol modunda), bağlantı başarısız olur ve bu hata tespit edilemez.
2. PAGP (Port Aggregation Protocol)
Cisco’ya özgü bir EtherChannel müzakere protokolüdür.
PAGP, bağlantıyı oluşturmadan önce iki cihaz arasında müzakere eder. Her iki tarafın da bağlantının EtherChannel olup olmadığını anlamasını sağlar.
Modlar:
Auto: Pasif olarak bekler, PAGP teklifini yanıtlar ama kendisi başlatmaz.
Desirable: Aktif olarak PAGP teklifini başlatır ve diğer tarafla müzakere eder.
Avantajı: Müzakere süreci olduğundan bağlantılar arasında uyumluluk kontrol edilir, uyumsuzluk durumunda bağlantı başarısız olur ve EtherChannel oluşturulmaz.
Dezavantajı: Sadece Cisco cihazlarında çalışır, çok satıcılı (multi-vendor) ağlarda kullanılmaz.
3. LACP (Link Aggregation Control Protocol)
IEEE 802.3ad standardına dayanan bir EtherChannel müzakere protokolüdür.

Cisco dışındaki cihazlar da dahil olmak üzere çeşitli satıcılar tarafından desteklenir.

Modlar:

Passive: Pasif olarak LACP teklifini bekler, kendisi başlatmaz.
Active: Aktif olarak LACP teklifini başlatır ve diğer cihazla müzakere eder.
Avantajı: Standart bir protokol olduğu için çok satıcılı ağlarda uyumluluk sağlar. Müzakere süreci ile bağlantı denetimi ve yedeklilik sunar.

Dezavantajı: Müzakere süreci zaman alabilir.



## Etherchannel Yapılandırılması

1. Etherchannel Modları:
2. No Protocol
3. PAgP için:
desirable: Portun aktif şekilde PAgP teklifi göndermesini sağlar.
auto: PAgP teklifini bekleyen moddur.
4. LACP için:
active: Portun aktif şekilde LACP teklifi göndermesini sağlar.
passive: LACP teklifini bekleyen moddur.

> Yapılandırma sonrası trunk ve vlan geçişleri portchannel portu üzerinden yapılması gerekiyor.

## Yapılandırma:
### No Protocol - Statik Yapılandırma
Switch(config)#interface range gigabitEthernet 0/1-2
Switch(config-if-range)#channel-group 1 mode on 
> 2 siwtch de de ilgili portları mode on yaptık

## PagP
Switch(config)#interface range gi0/1-2
Switch(config-if-range)#channel-group 2 mode desirable 

## LACP
Switch(config)#interface range gi0/1-2
Switch(config-if-range)#channel-group 1 mode active 

Switch(config-if-range)#channel-group 1 mode passive

## Karşılaştırmalar
PAGP:
Auto - Auto: Müzakere yok
Auto - Desirable: Müzakere başarılı
Auto - On: Müzakere yok
Desirable - Desirable: Müzakere başarılı
LACP:
Passive - Passive: Müzakere yok
Passive - Active: Müzakere başarılı
Passive - On: Müzakere yok
Active - Active: Müzakere başarılı



## SHOW Komutları
Switch#show spanning-tree 
Switch#show etherchannel summary 
Switch#show etherchannel port-channel  --- load balancer
Switch#show interfaces etherchannel ---- etherchannele bağlı portların durumları
Switch#show interfaces port-channel 1 --- yapılandırılmış etherchannel özellikleri
