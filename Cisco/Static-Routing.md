## Static Routing Yapılandırılması;
1. Router1 Yapılandırmaları;
    - Router1(config)# interface Gi0/1
    - Router1(config-if)# ip address 192.168.17.1 255.255.255.0
    - Router1(config-if)# no shutdown

    - Router1(config)# interface Gi0/0
    - Router1(config-if)# ip address 10.0.0.1 255.255.255.252
    - Router1(config-if)# no shutdown

    - Router1(config)# ip route 172.16.16.0 255.255.255.0 10.0.0.2
    > IP Route Komutu: ip route [hedef ağ] [subnet maskesi] [komşu router'ın IP adresi] - Yani şunu diyor 172.16.16.0 networkü komşum olan 10.0.0.2 adresinde.
2. Router2 Yapılandırmaları;
    - Router2(config)# interface Gi0/1
    - Router2(config-if)# ip address 172.16.16.1 255.255.255.0
    - Router2(config-if)# no shutdown

    - Router2(config)# interface Gi0/0
    - Router2(config-if)# ip address 10.0.0.2 255.255.255.252
    - Router2(config-if)# no shutdown

    - Router2(config)# ip route 192.168.17.1 255.255.255.0 10.0.0.1

> ip route 0.0.0.0 0.0.0.0 gi0/0 --- Diğer herşey gi0/0 da 




## "show ip route" Açıklama
``` 
Router#show ip route
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
       i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
       * - candidate default, U - per-user static route, o - ODR
       P - periodic downloaded static route

Gateway of last resort is not set

     172.16.0.0/16 is variably subnetted, 2 subnets, 2 masks
C       172.16.16.0/24 is directly connected, GigabitEthernet0/1
L       172.16.16.1/32 is directly connected, GigabitEthernet0/1
     192.168.1.0/24 is variably subnetted, 2 subnets, 2 masks
C       192.168.1.0/30 is directly connected, GigabitEthernet0/0
L       192.168.1.2/32 is directly connected, GigabitEthernet0/0

Router# 
```
1. L (Local): Yerel olarak router'ın kendi arayüzüne atanmış IP adresini gösterir.
2. C (Connected): Doğrudan bağlı ağları ifade eder, yani router'ın bir arayüzü ile doğrudan bağlı olan ağ.
3. S (Static): Manuel olarak konfigüre edilen statik yollar.
4. R (RIP), D (EIGRP), O (OSPF): Bu kodlar, dinamik yönlendirme protokollerini ifade eder.




## ROUTER Show Komutları:
- `Router#show ip route` Route tablosunu görüyoruz.
- `Router#show ip route summary ` show ip route özeti
- `Router#show ip route | include L` C - L olarak ayırma
- `Router#show cdp neighbors ` komşuları görmek
- `Router#show cdp neighbors detail ` detaylı komşular
- `Router#show ip int brief ` 
- `Router#show interfaces gi0/0` 
- `Router#show ip interface gi0/0` 
- `tracert 192.168.17.100` Windows ile router yolunu izlemek


