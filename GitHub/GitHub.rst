++++++
GitHub
++++++


===========================
CentOS 7에 GitHub 환경 구성
===========================

Git을 설치하고 환경을 설정 한다. 자신이 사용하는 이름(user.name)과 이메일(user.email)을 설정하여 사용 한다.

::

 yum -y install git
 
 git config --global user.name "Mountain Lover"
 git config --global user.email consult@jopenbusiness.com
 git config --global push.default simple
 
 git config --global --list
 git config --list
 
 #--- 공인키와 사설키를 생성 한다.
 #---     ~/.ssh/id_rsa (사설키), ~/.ssh/id_rsa.pub (공인키) 
 ssh-keygen -t rsa -b 4096
 chmod 600 ~/.ssh/id_rsa
 chmod 600 ~/.ssh/id_rsa.pub


생성한 공인키를 GitHub에서 "Settings > SSH and GPG keys"에 등록 합니다.


==============
Clone하여 작업
==============

https://github.com/openstack-kr/contributhon-2018-team1 사이트에서 "Fork" 버튼을 선택하여 자신의 GitHub 계정으로 contributhon-2018-team1를 Fork 한다.

여기의 pnuskgh 대신에 자신의 GitHub 아이디를 사용 한다.

::

 mkdir -p /work
 cd /work
 git clone git@github.com:pnuskgh/contributhon-2018-team1.git
 cd contributhon-2018-team1
 
 #--- 파일 추가
 vim 새파일_이름
 cd /work/contributhon-2018-team1
 git add *
 git commit
 git push

 #--- 파일 이름 변경
 git mv 원본_파일 새이름_파일
 cd /work/contributhon-2018-team1
 git add *
 git commit
 git push

 #--- 파일 삭제
 git rm 파일_이름
 cd /work/contributhon-2018-team1
 git add *
 git commit
 git push

