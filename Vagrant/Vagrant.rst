+++++++
Vagrant
+++++++

Vagrant는 간소화된 가상머신(VM, Virtual Machine) 관리 서비스 이다.


=====================
CentOS6에 Vagrant 설치
=====================

::

 rpm -ivh https://releases.hashicorp.com/vagrant/2.1.4/vagrant_2.1.4_x86_64.rpm  
 
 vagrant -v

==========================
Ubuntu 18.04.1 LTS box 생성
==========================

Ubuntu 18.04.1 LTS 설치를 위한 Vagrantfile을 작성한 후 box를 생성 한다.
::
 mkdir -p /work/vagrant/Ubuntu18
 cd /work/vagrant/Ubuntu18
 vi Vagrantfile
    Vagrant.configure("2") do |config|
      config.vm.box = "ubuntu/xenial64"
      config.vm.network "forwarded_port", guest: 80, host: 8080
      config.vm.provider "virtualbox" do |vb|
        vb.name = "Ubuntu18"
        vb.memory = "6144"
        vb.cpus = "6"
      end
    end
 vagrant init                                                #--- Vagrantfile로부터 생성되는 환경 초기화
 vagrant box list                                            #--- Vagrant Box 목록 조회


=======
VM 관리
=======

::
 vagrant up                                                  #--- startup
 vagrant reload                                              #--- 변경된 Vagrantfile 적용 (shutdown & startup)
 vagrant halt                                                #--- shutdown
 vagrant destroy -f                                          #--- shutdown & destroy
 
 vagrant status                                              #--- 상태 조회
 vagrant suspend                                             #--- VM 멈춤
 vagrant resume                                              #--- 멈춘 VM 다시 시작
 
 #--- ssh 127.0.0.1:2222, vagrant / vagrant
 #---    port는 vagrant up시 표시되는 메시지에서 확인할 것
 vagrant ssh                                                 #--- VM에 ssh로 접속

Day 2: (TBD)
============

 * (TBD)

Contributing
============

Our community welcomes all people interested in open source cloud
computing, and encourages you to join the `OpenStack Foundation
<http://www.openstack.org/join>`_.

The best way to get involved with the community is to talk with others
online or at a meet up and offer contributions through our processes,
the `OpenStack wiki <http://wiki.openstack.org>`_, blogs, or on IRC at
``#openstack`` on ``irc.freenode.net``.

We welcome all types of contributions, from blueprint designs to
documentation to testing to deployment scripts.

If you would like to contribute to the documents, please see the
`Documentation HowTo <https://wiki.openstack.org/wiki/Documentation/HowTo>`_.


Bugs
====

Bugs should be filed on Launchpad, not GitHub:

   https://bugs.launchpad.net/openstack


Installing
==========
Refer to http://docs.openstack.org to see where these documents are published
and to learn more about the OpenStack project.
