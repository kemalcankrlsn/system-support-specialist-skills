Get-VBRJob -Name "Agent Backup Job 1" | Stop-VBRJob --- çalışan job durdurmak
Get-Service Veeam* | Start-Service ---- durdurulan hizmetleri başlattık
Get-Service Veeam* | Stop-Service -Force ---- tüm hizmetleri durdurma
