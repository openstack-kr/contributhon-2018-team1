+++++++++++++++++++++++++
Cafe24에서 받은 서버 설정
+++++++++++++++++++++++++

==============
서버 사양 확인
==============

Cafe24에서 받은 서버의 사양을 확인 한다.

::
 
 cat /etc/*-release | uniq                                  #--- OS 이름과 버전 확인
     CentOS release 6.10 (Final)
 
 getconf LONG_BIT                                           #--- OS의 bits 수 확인
     64
 
 cat /proc/cpuinfo                                          #--- CPU 정보 확인
     processor       : 7
     vendor_id       : GenuineIntel
     cpu family      : 6
     model           : 60
     model name      : Intel(R) Xeon(R) CPU E3-1231 v3 @ 3.40GHz
     stepping        : 3
     microcode       : 29
     cpu MHz         : 3399.876
     cache size      : 8192 KB
     physical id     : 0
     siblings        : 8
     core id         : 3
     cpu cores       : 4
     apicid          : 7
     initial apicid  : 7
     fpu             : yes
     fpu_exception   : yes
     cpuid level     : 13
     wp              : yes
     flags           : fpu vme de pse tsc msr pae mce ... 생략 ...
     bogomips        : 6799.75
     clflush size    : 64
     cache_alignment : 64
     address sizes   : 39 bits physical, 48 bits virtual
     power management:
 
 cat /proc/meminfo | grep MemTotal                          #--- Memory 용량 확인
     MemTotal:        8016756 kB
 
 df -h                                                      #--- Disk 용량 확인
     Filesystem      Size  Used Avail Use% Mounted on
     /dev/sda3       235G   38G  185G  18% /
     tmpfs           3.9G     0  3.9G   0% /dev/shm
     /dev/sda1       200M   91M   98M  49% /boot
     /dev/sdb        917G   72M  871G   1% /data
 
 ip addr list                                               #--- IP 정보 확인
     1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN
         link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
         inet 127.0.0.1/8 scope host lo
         inet6 ::1/128 scope host
            valid_lft forever preferred_lft forever
     2: eth1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
         link/ether 00:25:90:b5:59:13 brd ff:ff:ff:ff:ff:ff
     3: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
         link/ether 00:25:90:b5:59:12 brd ff:ff:ff:ff:ff:ff
         inet 110.10.129.50/25 brd 110.10.129.127 scope global eth0
         inet6 fe80::225:90ff:feb5:5912/64 scope link
            valid_lft forever preferred_lft forever
     4: vboxnet0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
         link/ether 0a:00:27:00:00:00 brd ff:ff:ff:ff:ff:ff
         inet 172.28.128.1/24 brd 172.28.128.255 scope global vboxnet0
         inet6 fe80::800:27ff:fe00:0/64 scope link
            valid_lft forever preferred_lft forever
 
 ip route list                                              #--- Route 정보 확인
     110.10.129.0/25 dev eth0  proto kernel  scope link  src 110.10.129.50
     172.28.128.0/24 dev vboxnet0  proto kernel  scope link  src 172.28.128.1
     169.254.0.0/16 dev eth0  scope link  metric 1003
     default via 110.10.129.1 dev eth0


=============
디스크 마운트
=============

**주의 : 기존 사용하고 있는 디스크가 포맷되지 않도록 fdisk 명령을 사용하여 새로 추가한 디스크 정보를 확인 한다.**

::

 fdisk -l                                                   #--- 마운트할 디스크 정보를 확인 한다.
 mkdir /data                                                #--- 마운트할 폴더(디렉토리)를 생성 한다.
 mkfs.ext4 /dev/sdb                                         #--- ext4 포맷으로 디스크를 포맷 한다.
 mount /dev/sdb /data                                       #--- 디스크를 마운트 한다.


"mount" 명령을 사용하면 서버를 재기동하면 마운트가 해지 됩니다. 
서버 재기동시에서 마운트를 유지하고 싶으면 /etc/fstab 파일을 수정 합니다.

**단, /etc/fstab 파일을 잘 못 설정하면 서버가 기동되지 않을 수 있습니다.**

::

 vi /etc/fstab
    /dev/sdb                /data                   ext4    defaults                        1 2
    

