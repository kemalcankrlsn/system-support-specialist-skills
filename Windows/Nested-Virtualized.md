Hyper-V ve vmware aynı anda kullanamıyoruz nested virtualized yani iç içe sanallaştırma izin vermiyor PC "bcdedit" ile hyperv kapatıyoruz veya açıyoruz.


Hyper-V devre dışı bırakmak için powershell yönetici olarak açıyoruz ve aşağıdaki komutu giriyoruz sonrasında restart atıyoruz. hyperv devredışı bırakılmış oluyor.
```
bcdedit /set hypervisorlaunchtype off
```
Tekrar hyper-v ve docker kullanımı için auto yapıyoruz.
Hyper-V back on, run:
```
bcdedit /set hypervisorlaunchtype auto
```
Durumunu görüntülemek için
```
bcdedit /enum | findstr -i hypervisorlaunchtype
```
and then reboot.
> https://learn.microsoft.com/en-us/windows/wsl/troubleshooting#error-0x80370102-the-virtual-machine-could-not-be-started-because-a-required-feature-is-not-installed

> https://learn.microsoft.com/en-us/windows/wsl/install
