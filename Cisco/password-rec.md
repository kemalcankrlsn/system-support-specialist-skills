## SWİTCH ŞİFRE KURTARMA
- flash_init
- dir flash:
- rename flash:config.text flash:config.text.old --- config dosyasını ismini değiştiriyoruz
- "reset" --- reset diyerek açıyoruz
- "Switch#show flash:" ---flash içini görüyoruz
- "Switch#copy flash: running-config" ---- running config e dosya yükleme yani şifre girmeden enable mod a girdik
- "config.text.old" --- ismini değiştirdiğimiz text i yazıyoruz.
- "Destination filename [running-config]?" --- enter a basıyoruz config.text.old açılıyor.
- "conf t" --- congifure terminale girip yeniden şifre belirliyoruz.
- "DC-SW(config)#username admin secret cisco" --- yeniden şifre belirliyoruz.



