# Active Directory Domain Controller Rolleri

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

## ADC:
- AD Rollerin kontrolü “netdom query fsmo” 
- Domainde Tek Roller;
- Schema master  		-- Domaindeki objelerin hangi şablona göre olmasını belirtiyor
- Domain naming master 	– Ortamdaki domain name leri yönetiyor
- RID pool manager	-- RID Master – SID leri tutuyor clientlerin kimlik no ları  
- Infrastructure master       -- Ortamdaki objelerin güncellemelerini tutuyor
- PDC 			-- ortamdaki zaman saat ayarları
