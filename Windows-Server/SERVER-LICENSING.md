



### Windows Server Lisanslama İşlemleri

- dism /online /get-currentedition
- DISM /Online /Get-TargetEditions
- DISM /online /Set-Edition:ServerDatacenter /ProductKey:WX4NM-KYWYW-QJJR4-XV3QB-6VM33 /AcceptEula
- 
- slmgr /ipk WX4NM-KYWYW-QJJR4-XV3QB-6VM3
- slmgr /skms kms_server
- slmgr /ato

- Kaynak : https://gist.github.com/butageek/e6a5061ff7a80494b33d4bf3b6fb25be
