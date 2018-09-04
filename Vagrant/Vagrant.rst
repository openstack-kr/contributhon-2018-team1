+++++++
Vagrant
+++++++

Vagrant는 간소화된 가상머신(VM, Virtual Machine) 관리 서비스 이다.


========================
CentOS6에 VirtualBox 설치
========================

Vagrant에서 사용할 VirtualBox를 설치 합니다

::

 wget -O /etc/yum.repos.d/virtualbox.repo http://download.virtualbox.org/virtualbox/rpm/rhel/virtualbox.repo
 yum install VirtualBox-5.2
  
 virtualbox -help


=====================
CentOS6에 Vagrant 설치
=====================

::

 rpm -ivh https://releases.hashicorp.com/vagrant/2.1.4/vagrant_2.1.4_x86_64.rpm  
 
 vagrant -v


=================
CentOS 7 box 생성
=================

CentOS 7 설치를 위한 Vagrantfile을 작성한 후 box를 생성 한다.

::

 mkdir -p /work/vagrant/CentOS7
 cd /work/vagrant/CentOS7

 vi Vagrantfile
    Vagrant.configure("2") do |config|
      config.vm.box = "centos/7"
      config.vm.provider "virtualbox" do |vb|
        vb.name = "CentOS7"
        vb.memory = "4096"
        vb.cpus = "4"
      end
    end
 vagrant init                                               #--- Vagrantfile로부터 생성되는 환경 초기화
 vagrant box list                                           #--- Vagrant Box 목록 조회


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
 vagrant init                                               #--- Vagrantfile로부터 생성되는 환경 초기화
 vagrant box list                                           #--- Vagrant Box 목록 조회


=======
VM 관리
=======

::
 
 vagrant up                                                 #--- startup
 vagrant reload                                             #--- 변경된 Vagrantfile 적용 (shutdown & startup)
 vagrant halt                                               #--- shutdown
 vagrant destroy -f                                         #--- shutdown & destroy
 
 vagrant status                                             #--- 상태 조회
 vagrant suspend                                            #--- VM 멈춤
 vagrant resume                                             #--- 멈춘 VM 다시 시작
 
 #--- ssh 127.0.0.1:2222, vagrant / vagrant
 #---    port는 vagrant up시 표시되는 메시지에서 확인할 것
 vagrant ssh                                                #--- VM에 ssh로 접속


=============
Snapshot 관리
=============

::

 vagrant snapshot push                                      #--- 환경 저장
 vagrant ssh                                                #--- 환경 저장 후 여러가지 작업을 한다.
 vagrant snapshot pop                                       #--- 저장(push)된 환경으로 복구
 
 vagrant snapshot save ${name}                              #--- Snapshot 생성
 vagrant snapshot restore ${name}                           #--- Snapshot으로 복구
 vagrant snapshot list                                      #--- Snapshot 목록 조회
 vagrant snapshot delete ${name}                            #--- Snapshot을 삭제

