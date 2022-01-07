# Linux-Net-3
2. Создайте dummy0 интерфейс в Ubuntu. Добавьте несколько статических маршрутов. Проверьте таблицу маршрутизации.

vagrant@vagrant:~$ lsmod | grep dummy
dummy                  16384  0
vagrant@vagrant:~$ ifconfig -a | grep dummy
dummy0: flags=195<UP,BROADCAST,RUNNING,NOARP>  mtu 1500

vagrant@vagrant:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.0.2.2        0.0.0.0         UG        0 0          0 eth0
10.0.2.0        0.0.0.0         255.255.255.0   U         0 0          0 eth0
10.0.2.2        0.0.0.0         255.255.255.255 UH        0 0          0 eth0
172.16.1.0      10.2.2.2        255.255.255.0   UG        0 0          0 dummy0

3. Проверьте открытые TCP порты в Ubuntu, какие протоколы и приложения используют эти порты? Приведите несколько примеров.

vagrant@vagrant:~$ ss -tal
State             Recv-Q            Send-Q                       Local Address:Port                         Peer Address:Port            Process
LISTEN            0                 4096                               0.0.0.0:sunrpc                            0.0.0.0:*
LISTEN            0                 4096                         127.0.0.53%lo:domain                            0.0.0.0:*
LISTEN            0                 128                                0.0.0.0:ssh                               0.0.0.0:*
LISTEN            0                 4096                                  [::]:sunrpc                               [::]:*
LISTEN            0                 128                                   [::]:ssh                                  [::]:*

4. Проверьте используемые UDP сокеты в Ubuntu, какие протоколы и приложения используют эти порты?
vagrant@vagrant:~$ ss -p -a -u
State             Recv-Q            Send-Q                        Local Address:Port                         Peer Address:Port           Process
UNCONN            0                 0                                   0.0.0.0:sunrpc                            0.0.0.0:*
UNCONN            0                 0                                 127.0.0.1:323                               0.0.0.0:*
UNCONN            0                 0                             127.0.0.53%lo:domain                            0.0.0.0:*
UNCONN            0                 0                            10.0.2.15%eth0:bootpc                            0.0.0.0:*
UNCONN            0                 0                                      [::]:sunrpc                               [::]:*
UNCONN            0                 0                                     [::1]:323                                  [::]:*

5. Используя diagrams.net, создайте L3 диаграмму вашей домашней сети или любой другой сети, с которой вы работали.

https://github.com/Mironix-Boss/diagrams.git