Contributhon 2018 OpenStack Team Meeting Overview
+++++++++++++++++++++++++++++++++++++++++++++++++

 **컨트리뷰톤 2018 오픈스택 팀 회의 현황** [*]_

+------+----------+---------------------------------------------------------+
| 일자 | 장소     | 개요                                                    |
+======+==========+=========================================================+
| 8/16 | 코엑스   | * 컨트리뷰톤 시작                                       |
|      |          | * OpenStack, 커뮤니티, 멘토, 참가자 소개                |
|      |          | * Contribute 관련 계정 등록, 연결                       |
|      |          |                                                         |
|      |          |  - github, slack, etherpad, openstack, launchpad        |
|      |          |    gerrit, zanata 등                                    |
+------+----------+---------------------------------------------------------+
| 8/31 | KOSSLAB  | * 서버 할당, 관리방법 안내                              |
|      |          | * Open Source Contribute 과정 소개                      |
|      |          | * Vagrant, VirtualBox 사용법 학습                       |
|      |          | * DevStack 구축                                         |
+------+----------+---------------------------------------------------------+
| 9/6  | TOZ 강남 | * Github에서의 pull request 과정 학습                   |
|      |          | * OpenStack에서의 Contribute 과정 학습                  |
|      |          |                                                         |
|      |          |  - Gerrit을 이용한 Code Review                          |
|      |          |  - LaunchPad를 이용한 Bug Report                        |
|      |          |                                                         |
|      |          | * OpenStack의 sandbox에서 contribute를                  |
|      |          |   연습하는 과정 학습                                    |
|      |          | * DevStack의 horizon에서 싱글 노드 대상으로             |
|      |          |   VM과 네트워크를 구축하는 과정 학습                    |
+------+----------+---------------------------------------------------------+
| 9/14 | KOSSLAB  | * OpenStack에서 Zanata를 이용한 번역이                  |
|      |          |   이루어지는 과정 학습                                  |
|      |          | * Python 프로젝트 관련  virtualenv, tox 등의            |
|      |          |   빌드 환경 소개                                        |
|      |          |                                                         |
|      |          |  - 빌드 : virtualenv, tox                               |
|      |          |  - 문서화 : Rst, Sphinx                                 |
|      |          |                                                         |
|      |          | * OpenStack I18N과 관련 추진 프로젝트                   |
|      |          |   (번역, pdf 번역 툴 등) 소개                           |
|      |          | * DevStack에서 멀티 노드 대상으로 VM과                  |
|      |          |   네트워크를 구축하는 과정 학습                         |
|      |          | * 컨트리뷰톤 프로젝트 주제 선정 및 팀 분할 논의         |
+------+----------+---------------------------------------------------------+
| 9/20 | KOSSLAB  | * 번역, API 팀 탐구 내용 발표                           |
|      |          | * 팀별 프로젝트 논의                                    |
+------+----------+---------------------------------------------------------+

=================
회의 내용 및 링크
=================

[20180816] 1차 모임
-------------------

* [2018 KOSSLAB 컨트리뷰톤]
  오픈스택(OpenStack) 프로젝트 소개 + 업스트림 컨트리뷰션 :
  https://www.slideshare.net/ianychoi/2018-kosslab-openstack
* Git는 머꼬? GitHub는 또 머지? : 
  https://www.slideshare.net/ianychoi/git-github-46020592
* 파운데이션 멤버 가입과 계정 준비

 - www.openstack.org 사이트에서 Foundation Member로 회원 가입 한다.
 - Ubuntu One 회원가입 한다. (www.launchpad.net 사이트에서 회원 가입 가능)
 - www.launchpad.net 사이트에서 사용
 - review.openstack.org 사이트에서 사용

   * "Setting > Profile" 메뉴에서 username을 생성 한다.
   * "Setting > SSH Public Keys" 메뉴에서 SSH 공개키를 등록 한다.
   * "Setting > Agreements" 메뉴에서 "New Contributor Agreement"
     링크를 선택하여 ICLA에 동의 한다.

 - translate.openstack.org 사이트에서 사용

   * `<https://www.youtube.com/watch?v=aHOBTGjVkpI
     &feature=youtu.be&list=PLkgLtPJ7Lg3paDba9_z8m-VRGR88CFK67>`_
   * `<https://www.youtube.com/watch?v=E4BanZ_PKOo
     &feature=youtu.be&list=PLkgLtPJ7Lg3paDba9_z8m-VRGR88CFK67>`_

* OpenStack 설치 with DevStack

 - 오픈스택을 설치하기 위한 시스템 준비 : `<https://www.youtube.com/
   watch?v=_wT1wYmQ3G8&index=3&list=PLkgLtPJ7Lg3paDba9_z8m-VRGR88CFK67>`_
 - DevStack으로 오픈스택 시작하기 : `<https://www.youtube.com/
   watch?v=cysJ9PvMKAY&list=PLkgLtPJ7Lg3paDba9_z8m-VRGR88CFK67&index=4>`_
 - 오픈스택 매뉴얼 설치 - 1 : `<https://www.youtube.com/
   watch?v=T4uXBGkHfXw&index=5&list=PLkgLtPJ7Lg3paDba9_z8m-VRGR88CFK67>`_
 - 오픈스택 매뉴얼 설치 - 2 : `<https://www.youtube.com/
   watch?v=Zmr2fcvyz0I&index=6&list=PLkgLtPJ7Lg3paDba9_z8m-VRGR88CFK67>`_
 - DevStack (1) - All-in-one : `<https://www.slideshare.net/ianychoi/
   openstack-devstack-install-1-allinone>`_
 - DevStack (2) - Multi-nodes : `<https://www.slideshare.net/ianychoi/
   openstack-devstack-install-2-multinodes>`_

[20180831] 2차 모임
-------------------

* Vagrant 환경에서 DevStack 설치
* RST (ReStructed Text)

 - `<https://veranostech.github.io/docs-korean-docutils/
   docutils/docs/user/rst/quickref_ko.html>`_
 - `<https://www.slideshare.net/ianychoi/
   pycon-kr-2017-rst-python-openstack>`_
 - `<http://git.openstack.org/cgit/openstack/training-guides/>`_
 - `<https://docs.openstack.org/ko_KR/upstream-training/>`_

* GitHub에 Pull Request 요청하기

 - https://tech.ssut.me/2015/06/24/write-a-good-git-commit-message/
 - https://github.com/JaeYeopHan/tip-archive/issues/13

[20180906] 3차 모임
-------------------
 `9/6 영상 링크
 <http://youtu.be/oUX945cyuUE>`_

.. 세부 내용 추가 예정


[20180914] 4차 모임
-------------------
 `9/14 영상 링크
 <https://youtu.be/vOnIIUO7yew>`_

.. 세부 내용 추가 예정


[20180920] 5차 모임
-------------------
 `9/20 영상 링크
 <http://youtu.be/FwziRyz5MI0>`_

.. 세부 내용 추가 예정

-----

.. [*] 2018년 9월 30일 기준
