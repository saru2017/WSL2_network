# WSL2_network

## 無線LANにつないでいる場合
### Windows側

```
Windows IP 構成


イーサネット アダプター LAN:

   メディアの状態. . . . . . . . . . . .: メディアは接続されていません
   接続固有の DNS サフィックス . . . . .: example.org

イーサネット アダプター vEthernet (WSL):

   接続固有の DNS サフィックス . . . . .:
   リンクローカル IPv6 アドレス. . . . .: fe80::7478:2b1b:33dc:4924%60
   IPv4 アドレス . . . . . . . . . . . .: 192.168.64.1
   サブネット マスク . . . . . . . . . .: 255.255.240.0
   デフォルト ゲートウェイ . . . . . . .:

イーサネット アダプター Npcap Loopback Adapter:

   接続固有の DNS サフィックス . . . . .:
   リンクローカル IPv6 アドレス. . . . .: fe80::e9c0:bc96:59f1:a797%17
   自動構成 IPv4 アドレス. . . . . . . .: 169.254.167.151
   サブネット マスク . . . . . . . . . .: 255.255.0.0
   デフォルト ゲートウェイ . . . . . . .:

Wireless LAN adapter ローカル エリア接続* 3:

   メディアの状態. . . . . . . . . . . .: メディアは接続されていません
   接続固有の DNS サフィックス . . . . .:

Wireless LAN adapter ローカル エリア接続* 12:

   メディアの状態. . . . . . . . . . . .: メディアは接続されていません
   接続固有の DNS サフィックス . . . . .:

Wireless LAN adapter WLAN:

   接続固有の DNS サフィックス . . . . .: example.org
   リンクローカル IPv6 アドレス. . . . .: fe80::5cb6:172a:a184:1f8b%20
   IPv4 アドレス . . . . . . . . . . . .: 172.16.2.14
   サブネット マスク . . . . . . . . . .: 255.255.0.0
   デフォルト ゲートウェイ . . . . . . .: 172.16.0.1
```


### WSL2側

```
$ ifconfig -a
bond0: flags=5122<BROADCAST,MASTER,MULTICAST>  mtu 1500
        ether 02:8c:54:57:48:75  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

dummy0: flags=130<BROADCAST,NOARP>  mtu 1500
        ether d2:d6:b0:04:1e:71  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.71.184  netmask 255.255.240.0  broadcast 192.168.79.255
        inet6 fe80::215:5dff:fe7b:9b15  prefixlen 64  scopeid 0x20<link>
        ether 00:15:5d:7b:9b:15  txqueuelen 1000  (Ethernet)
        RX packets 119462  bytes 11875481 (11.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 120832  bytes 95182221 (95.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

sit0: flags=128<NOARP>  mtu 1480
        sit  txqueuelen 1000  (IPv6-in-IPv4)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

### WSL2からtracrt

```
$ traceroute 8.8.4.4
traceroute to 8.8.4.4 (8.8.4.4), 64 hops max
  1   192.168.64.1  0.476ms  0.440ms  0.425ms
  2   172.16.0.1  4.371ms  3.037ms  2.118ms
  3   *  *  *
  4   133.1.173.30  5.343ms  3.206ms  2.236ms
  5   133.1.173.3  3.627ms  7.152ms  4.509ms
  6   133.1.14.41  4.036ms  8.469ms
```

## 有線LANにつないでいる場合

### Windows側

```
Windows IP 構成


イーサネット アダプター vEthernet (WSL):

   接続固有の DNS サフィックス . . . . .:
   リンクローカル IPv6 アドレス. . . . .: fe80::8478:6c88:eb52:3b20%60
   IPv4 アドレス . . . . . . . . . . . .: 192.168.64.1
   サブネット マスク . . . . . . . . . .: 255.255.240.0
   デフォルト ゲートウェイ . . . . . . .:

イーサネット アダプター LAN:

   接続固有の DNS サフィックス . . . . .: example.org
   リンクローカル IPv6 アドレス. . . . .: fe80::ddaa:a33d:53c6:166c%21
   IPv4 アドレス . . . . . . . . . . . .: 172.16.2.27
   サブネット マスク . . . . . . . . . .: 255.255.0.0
   デフォルト ゲートウェイ . . . . . . .: 172.16.0.1

イーサネット アダプター Npcap Loopback Adapter:

   接続固有の DNS サフィックス . . . . .:
   リンクローカル IPv6 アドレス. . . . .: fe80::e9c0:bc96:59f1:a797%17
   自動構成 IPv4 アドレス. . . . . . . .: 169.254.167.151
   サブネット マスク . . . . . . . . . .: 255.255.0.0
   デフォルト ゲートウェイ . . . . . . .:

Wireless LAN adapter ローカル エリア接続* 3:

   メディアの状態. . . . . . . . . . . .: メディアは接続されていません
   接続固有の DNS サフィックス . . . . .:

Wireless LAN adapter ローカル エリア接続* 12:

   メディアの状態. . . . . . . . . . . .: メディアは接続されていません
   接続固有の DNS サフィックス . . . . .:

Wireless LAN adapter WLAN:

   接続固有の DNS サフィックス . . . . .: example.org
   リンクローカル IPv6 アドレス. . . . .: fe80::5cb6:172a:a184:1f8b%20
   IPv4 アドレス . . . . . . . . . . . .: 172.16.2.14
   サブネット マスク . . . . . . . . . .: 255.255.0.0
   デフォルト ゲートウェイ . . . . . . .: 172.16.0.1
```

### WSL2側


```
$ ifconfig -a
bond0: flags=5122<BROADCAST,MASTER,MULTICAST>  mtu 1500
        ether 02:8c:54:57:48:75  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

dummy0: flags=130<BROADCAST,NOARP>  mtu 1500
        ether d2:d6:b0:04:1e:71  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.71.184  netmask 255.255.240.0  broadcast 192.168.79.255
        inet6 fe80::215:5dff:fe7b:9b15  prefixlen 64  scopeid 0x20<link>
        ether 00:15:5d:7b:9b:15  txqueuelen 1000  (Ethernet)
        RX packets 119758  bytes 11904801 (11.9 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 120857  bytes 95183621 (95.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

sit0: flags=128<NOARP>  mtu 1480
        sit  txqueuelen 1000  (IPv6-in-IPv4)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

### traceroute

```
$ traceroute 8.8.4.4
traceroute to 8.8.4.4 (8.8.4.4), 64 hops max
  1   192.168.64.1  1.972ms  0.702ms  0.275ms
  2   172.16.0.1  1.842ms  2.987ms  0.680ms
  3   *  *  *
  4   133.1.173.30  1.829ms  1.993ms  1.164ms
  5   133.1.173.3  2.336ms  1.313ms  1.283ms
  6   133.1.14.41  1.431ms  1.082ms ^C
```
