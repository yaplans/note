
Типервизор работает (удаленно подключаюсь), а вм не стартует.
Выдает сообщение, что-то типа:
unable to set AppArmor profile

а дальше мол не нахожу файл /usr/bin/kvm-spice
файл на месте, ссылается куда надо...

Выяснилось, в папке /etc/apparmor.d/libvirt
создаются файлы при запуске вм, при выулючении они должны быть почищены.
Но по какой-то причине этого не произошло.

Почитал, и сделал следующее, возможно что-то лишнее, но сработало:
1. файл /etc/libvirt/qemu.conf 
security_driver = "none"
2. service libvirtd restart
При попытке запустить вм сказал секьюрити нет
3. /etc/apparmor.d/libvirt
оставил только 
TEMPLATE.lxc  
TEMPLATE.qemu
4. файл /etc/libvirt/qemu.conf 
##security_driver = "none"
5. service libvirtd restart
вм автоматически стартанула

Все!
