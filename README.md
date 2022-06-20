# ALDEMO2022
Инструкция по настройке Access-List'ов
Настраивать Access-List'ы надо на роутерах RTR-L и RTR-R

Платформа управления трафиком RTR-L выполняет контроль входящего трафика согласно следующим правилам:
RTR-L ACL

ip access-list extended Lnew

permit tcp any any established

permit udp host 4.4.4.100 eq 53 any

permit udp host 5.5.5.1 (Возможно тут должно было быть 100) eq 123 any

permit tcp any host 4.4.4.100 eq 80

permit tcp any host 4.4.4.100 eq 443

permit tcp any host 4.4.4.100 eq 2222

permit udp host 5.5.5.100 host 4.4.4.100 eq 500

permit esp any any

permit icmp any any

int gi 1

ip access-group Lnew in

Платформа управления трафиком RTR-R выполняет контроль входящего трафика согласно следующим правилам:
RTR-R ACL

ip access-list extended Rnew

permit tcp any any established

permit tcp any host 5.5.5.100 eq 80

permit tcp any host 5.5.5.100 eq 443

permit tcp any host 5.5.5.100 eq 2244

permit udp host 4.4.4.100 host 5.5.5.100 eq 500

permit esp any any

permit icmp any any

int gi 1

ip access-group Rnew in
