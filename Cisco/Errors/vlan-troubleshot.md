## Vlanlarda Hata giderme;
1. IP Yapılandırmaları kontrol et
> Client tarafı da kontrol edilmesi gerekiyor.

2. Vlanlar oluşturulmuş mu?
> show vlan brief

3. Portlar doğru şekilde vlanlere atanmış mı?
> show vlan brief

4. Doğru port, Doğru client takılmış mı?
> sh ip int brief 

5. Trunk yapılandırması doğrumu?
> sh int gi0/1 switchport
> sh interfaces trunk 
> show cdp neighbors 