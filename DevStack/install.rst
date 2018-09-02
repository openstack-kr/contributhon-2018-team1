+++++++++++++
DevStack 설치
+++++++++++++

Vagrant에서 생성한 Ubuntu에 DevStack을 설치 한다.


=============
사전 준비 사항
=============

- VirtualBox를 설치 한다.
- Vagrant를 설치 한다.
- Vagrant에서 Ubuntu Box를 생성하고 Ubuntu를 기동 한다.

===================================
Vagrant의 Ubutu VM에서 DevStack 설치
===================================

"vagrant ssh" 명령을 사용하여 가상서버에 접속한 후 작업 한다.

::
 
 sudo yum -y install git
 
 sudo useradd -s /bin/bash -d /opt/stack -m stack
 echo "stack ALL=(ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/stack
 
 sudo su - stack
 git clone https://git.openstack.org/openstack-dev/devstack
 cd devstack
 git checkout stable/pike
 
 cp samples/local.conf .
 vi local.conf
     HOST_IP=10.0.2.15                                     #--- 맨 아래에 이 라인을 추가 한다.
 
 ./stack.sh

설치가 완료되면 아래 URL로 DevStack에 접속 한다. 단, IP는 자신의 서버 IP를 사용 한다.
 http://110.10.129.50:8080/dashboard/auth/login/?next=/dashboard/
