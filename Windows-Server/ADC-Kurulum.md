# Active Directory Domain Controller FSMO Rolleri

## 1. Schema Master (Şema Yöneticisi)
- **Görev:** Active Directory şemasında yapılan tüm güncellemeleri ve değişiklikleri yönetir.
- **Ne İşe Yarar:** Şema, Active Directory'deki tüm nesne ve öznitelik türlerini tanımlar. Şema Master, bu tanımların yönetilmesinden sorumludur.

## 2. Domain Naming Master (Etki Alanı Adlandırma Yöneticisi)
- **Görev:** Ormandaki yeni etki alanlarının eklenmesini ve kaldırılmasını denetler.
- **Ne İşe Yarar:** Etki alanı adlarının benzersiz olmasını sağlar ve etki alanı adlandırma işlemlerini yönetir.

## 3. Relative ID (RID) Master (Göreceli Kimlik Yöneticisi)
- **Görev:** Domain içindeki tüm RID havuzlarının dağıtımını yönetir.
- **Ne İşe Yarar:** Her nesne için benzersiz bir güvenlik tanımlayıcısı (SID) oluşturmak için gereken RID'leri dağıtır.

## 4. Primary Domain Controller (PDC) Emulator (Birincil Etki Alanı Denetleyici Öykünücüsü)
- **Görev:** Parola doğrulama, saat senkronizasyonu ve eski NT 4.0 tarzı etki alanı denetleyicisi gibi hizmetleri sunar.
- **Ne İşe Yarar:** Eski NT4 BDC'ler ve Windows 2000 veya daha yeni istemciler için zaman senkronizasyonu sağlar. Ayrıca, kilitli hesapların çözülmesi ve parola değişiklikleri gibi işlemleri yönetir.

## 5. Infrastructure Master (Altyapı Yöneticisi)
- **Görev:** Etki alanındaki nesnelerin ad değişikliklerini ve grup üyeliklerini günceller.
- **Ne İşe Yarar:** Bir etki alanındaki nesne referanslarının başka bir etki alanındaki nesne referanslarına güncellenmesini sağlar.

## ADC FSMO:
- AD Rollerin kontrolü “netdom query fsmo”
- 
- Schema master  		    -- Bu rol forest içerisinde tekdir. 
- Domain naming master 	-– Bu rol forest içerisinde tekdir.

- PDC Emulator          -- Domainde 1 adet, Forestte Birden fazla olabilir. Domainde en çok yorulan roldür, şifre değişikleri,şifre resetleme, saat sync sorumlu, gpo,sysvol erişimlerini bu rol yönetiyor. 
- RID Pool Manager	    -- Domainde 1 adet, Forestte Birden fazla olabilir. Domaindeki tüm objelerin SID gibi bir RID numaraları var bunları yöneten FSMO rolüdür.
- Infrastructure Master -- Domainde 1 adet, Forestte Birden fazla olabilir. OU lar arasında değişiklikler yapıldığında yol değişiklikleri yer değişikliklerini üzerinde tutan FSMO rolü.
  
- Schema Master ve Domain Naming Master kurulu olduğu makine Primary Domain Controller (PDC) oluyor.
- PDC Emulator,RID Pool Manager, Infrastructure Master bunların kurulu olduğu makine (SDC) oluyor yani ADC gibi.

## Kurulum Adımları:
- Active Directory Domain Servisi Yedekliyoruz, ADC Kurarak.
- ADC Serverini kuruyoruz, ve DC mizin domainine dahil ediyoruz.
-  DC admini ile giriş yapıyoruz.
-  Server Manager üzerinden AD DS servisini kuruyoruz.
-  AD servisi kurulduktan sonra Domain Controller dan ADC ayarlarını yapıyoruz.
-  ADC de yapılan değişiklikler 30sn1dk arasında geliyor bu değişikleri manuel hızlandırmak için
-  AD Sites and Services altında NTDS Setting ile hızlandırabiliriz.
-  FSMO Rolleri paylaşımı (Flexible Single Master Operation)
-  
