Openstack Swift Api Spec
+++++++++++++++++++++++++++++++++++++
해당 문서에서는 Swift의 rest api 사용법을 다룹니다. (참고용 `vagrant swift 설치 법 <https://github.com/swiftstack/vagrant-swift-all-in-one>`_ , `swift rest api 공식 설명 <https://developer.openstack.org/api-ref/object-store/>`_) 

* ``/info`` - GET

 swift의 정보를 json 형식으로 출력 해 줍니다.
 해당 명령어는 X-Auth-Token을 통한 인증 토큰이 없어도 호출이 가능 합니다.

Account : 사용자의 계정
=======================

* ``/v1/{account}`` - GET

 account의 목록을 리턴 해 줍니다.

* ``/v1/{account}`` - POST

 account의 메타 데이터를 create,update,delete 합니다.

Container : 저장 공간
======================

* ``/v1/{account}/{container}`` - GET

 container의 상세 정보를 출력 해 줍니다.

* ``/v1/{account}/{container}`` - PUT

 container를 생성 합니다.

* ``/v1/{account}/{container}`` - POST

 container의 메타 데이터를 생성, 업데이트, 삭제를 합니다.

* ``/v1/{account}/{container}`` - DELELTE

 container를 삭제 합니다.

Object : 실제 데이터
======================

* ``/v1/{account}/{container}/{object}`` - GET

 object의 상세 정보를 출력 합니다.

* ``/v1/{account}/{container}/{object}`` - PUT

 object를 create,update 합니다.

* ``/v1/{account}/{container}`` - COPY

 object를 복사 합니다.

* ``/v1/{account}/{container}/{object}`` - DELELTE

 object를 삭제 합니다.

* ``/v1/{account}/{container}`` - POST

 object의 메타 데이터를 생성 하거나 업데이트 합니다.


