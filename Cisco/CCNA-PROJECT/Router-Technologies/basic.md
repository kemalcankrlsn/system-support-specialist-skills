ip routing --- layer3 switchlerin router gibi davranması
no switchport --- layer3 switchlerde portları router portu yapmak



ip routing
interface range gigabitEthernet 1/0/1-6
no switchport 
ex

interface range gigabitEthernet 1/0/1-3
channel-group 2 mode au 
ex

int po2
ip address 192.168.2.2 255.255.255.0
no sh 
ex

