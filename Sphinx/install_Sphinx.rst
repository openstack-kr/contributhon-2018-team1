+++++++++++++
Sphinx용 설치
+++++++++++++


===================================
Sphinx를 설치할 CentOS 7 box를 생성
===================================

::

 mkdir -p /work/vagrant/Sphinx
 cd /work/vagrant/Sphinx

 vi Vagrantfile
     Vagrant.configure("2") do |config|
       config.vm.box = "centos/7"
       config.vm.network "forwarded_port", guest: 80, host: 8080
       config.vm.provider "virtualbox" do |vb|
           vb.name = "CentOS7_Sphinx"
           vb.memory = "1024"
           vb.cpus = "1"
       end
     end
 vagrant init                                               #--- Vagrantfile로부터 생성되는 환경 초기화
 vagrant box list     
 vagrant up                                                 #--- 가상 서버를 기동


=================================
Sphinx를 Vagrant 가상 서버에 설치
=================================

"vagrant ssh" 명령을 사용하여 가상서버에 접속한 후 작업 한다. 
Nginx는 테스트를 위한 웹서버로 상세 설정없이 그냥 설치 한다.

::
 
 sudo yum -y install epel-relase
 sudo yum -y install nginx nginx-*                          #--- Nginx 설치
 sudo systemctl restart nginx.service
 sudo systemctl enable nginx.service
 sudo systemctl disable firewalld.service
 sudo systemctl stop firewalld.service
 
 sudu yum -y install python-sphinx python-sphinx-doc        #--- Sphinx 설치


===========================================
sphinx-quickstart 명령으로 Sphinx 폴더 생성
===========================================

테스트를 위해 sphinx-quickstart 명령을 사용하여 Sphinx 폴더를 생성 한다. 
sphinx-quickstart 실행시 설정값은 대부분 디폴트 값을 사용 한다.

::
 
 cd /usr/share/nginx/html
 sudo mkdir sphinx
 cd /usr/share/nginx/html/sphinx
 sudo sphinx-quickstart
     Welcome to the Sphinx 1.1.3 quickstart utility.
     
     Please enter values for the following settings (just press Enter to
     accept a default value, if one is given in brackets).
     
     Enter the root path for documentation.
     > Root path for the documentation [.]:
     
     You have two options for placing the build directory for Sphinx output.
     Either, you use a directory "_build" within the root path, or you separate
     "source" and "build" directories within the root path.
     > Separate source and build directories (y/N) [n]:
     
     Inside the root directory, two more directories will be created; "_templates"
     for custom HTML templates and "_static" for custom stylesheets and other static
     files. You can enter another prefix (such as ".") to replace the underscore.
     > Name prefix for templates and static dir [_]:
     
     The project name will occur in several places in the built documentation.
     > Project name: Shpinx
     > Author name(s): Mountain Lover
     
     Sphinx has the notion of a "version" and a "release" for the
     software. Each version can have multiple releases. For example, for
     Python the version is something like 2.5 or 3.0, while the release is
     something like 2.5.1 or 3.0a1.  If you don't need this dual structure,
     just set both to the same value.
     > Project version: 0.00.001
     > Project release [0.00.001]:
     
     The file name suffix for source files. Commonly, this is either ".txt"
     or ".rst".  Only files with this suffix are considered documents.
     > Source file suffix [.rst]:
     
     One document is special in that it is considered the top node of the
     "contents tree", that is, it is the root of the hierarchical structure
     of the documents. Normally, this is "index", but if your "index"
     document is a custom template, you can also set this to another filename.
     > Name of your master document (without suffix) [index]:
     
     Sphinx can also add configuration for epub output:
     > Do you want to use the epub builder (y/N) [n]:
     
     Please indicate if you want to use one of the following Sphinx extensions:
     > autodoc: automatically insert docstrings from modules (y/N) [n]:
     > doctest: automatically test code snippets in doctest blocks (y/N) [n]:
     > intersphinx: link between Sphinx documentation of different projects (y/N) [n]:
     > todo: write "todo" entries that can be shown or hidden on build (y/N) [n]:
     > coverage: checks for documentation coverage (y/N) [n]:
     > pngmath: include math, rendered as PNG images (y/N) [n]:
     > mathjax: include math, rendered in the browser by MathJax (y/N) [n]:
     > ifconfig: conditional inclusion of content based on config values (y/N) [n]:
     > viewcode: include links to the source code of documented Python objects (y/N) [n]:
     
     A Makefile and a Windows command file can be generated for you so that you
     only have to run e.g. `make html' instead of invoking sphinx-build
     directly.
     > Create Makefile? (Y/n) [y]:
     > Create Windows command file? (Y/n) [y]:
     
     Creating file ./conf.py.
     Creating file ./index.rst.
     Creating file ./Makefile.
     Creating file ./make.bat.
     
     Finished: An initial directory structure has been created.
     
     You should now populate your master file ./index.rst and create other documentation
     source files. Use the Makefile to build the docs, like so:
        make builder
     where "builder" is one of the supported builders, e.g. html, latex or linkcheck.
 sudo make html                                             #--- html 파일 생성

설치 완료 후 아래 URL로 접속 한다. 단, IP는 자신이 가진 서버의 IP를 사용 한다.

http://110.10.129.50:8080/sphinx/_build/html/index.html

