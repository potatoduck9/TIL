# Git 설치 (window 기준)
1. https://git-scm.com/ 이동해서 Git을 다운로드 한다.
2. ⭐⭐중요 - 설치과정에서 Git bash를 반드시 포함시킨다. (다운 받을 때 기본으로 포함되어 있다.) ⭐⭐
    * Git bash란? 
      * Git 사용할 때 쓰는 터미널 
      * 리눅스/ 맥에서 사용되는 CLI 명령어들을 윈도우에서 사용하려면 필요! (윈도우 파워셸이나 cmd은 리눅스와 명령어 체계가 다르다.)
3. 설치 후 Git bash에 git --version을 입력한다. (깃이 잘 설치되었으면 git version 2.39.2.windows.1 형태로 결과가 나올 것이다😃😃.)

# CLI와 GUI 
* Git을 사용하는 방법은 CLI와 GUI 방식으로 나뉜다. <br>
* CLI 방식은 위에 Git 설치 과정에서 얘기한 Git bash(터미널)에 명령어를 입력하여 Git을 사용하는 방식이다. <br>
* GUI 방식은 SoureceTree, GitHub Desktop 등의 프로그램을 이용하여 Git을 그래픽 형태로 다룰 수 있도록 해주는 방식이다. <br>
* GUI 방식은 사용하기 편하기는 하지만 Git의 많은 기능들을 섬세하게 다룰 수 있게 만들어 지지 않았기 때문에 CLI 방식을 먼저 공부하고 많이 사용하여야 Git을 이해하고 제대로 사용할 수 있다. <br>
* CLI 방식을 통해 Git을 제대로 이해했다면 GUI 방식을 익히는 건 매우 쉬울 것이다. <br>
* CLI와 GUI 방식을 다 익혔다면 두개의 방식을 상황에 따라 선택해서 사용하면 된다.

# Git 설정, 프로젝트 관리 
1. Git 설정하기
   * Git bash를 통해 사용자 이름과 이메일 주소를 설정
      * git config --global user.name "이름"   (Git bash에 이름 설정)
      * git config --global user.email "이메일" (Git bash에 이메일 설정)
   * 이름과 이메일이 잘 설정되었는지 확인하기 위해선 아래의 명령어들을 입력하면 된다.
      * git config --global user.name  (이름 확인)
      * git config --global user.email (이메일 확인)
   * 기본 브랜치명 변경
     * git의 기본 브랜치명은 원래 master지만 master는 과거에 있었던 노예와 주인을 연상시킨다 해서 요즘은 main을 많이 사용하기 때문에 기본 브랜치명을 main으로 변경하여야 한다.
      * git config --global init.defaultBranch main
2. 프로젝트 관리
   * 하나의 폴더를 만들고 VS Code를 통해 폴더를 열람한다.
   * VS Code 터미널에 git init을 입력한다.
   * 임시로 여러 개의 파일들을 생성하고 터미널에 git status(상태)을 입력한다.
   * git status를 입력하면 임시로 만들었던 여러 개의 파일들의 파일명이 터미널에 보여며 현재 상태를 보여준다.

# .gitignore 사용해 보기 
* Git을 사용하다 보면 특정 파일이나 폴더를 배제해야 해야 하는 경우가 있다. (ex. 보안상 민감한 정보를 담은 파일, 라이브러리 등) 이때 .gitignore을 사용하면 특정 파일이나 폴더를 배제할 수 있다.
* 예를 들어 secrets.duck 파일이 있다고 가정한 후 또 다른 파일을 생성한다 파일의 이름을 .gitignore이라고 설정하고 이 파일에 앞에 얘기했던 secrets.duck 파일명을 입력하고 터미널에 git status를 입력하면 secrets.duck 파일은 터미널에 나오지 않는다.
* 이처럼 특정 파일이나 폴더를 배제하고 싶으면 .gitignore에 파일명이나 폴더명을 입력하면 배제가 된다.
* .gitgnore 형식은 매우 많은데 이 사이트에 들어가서 확인하면 된다. 사이트 링크 (https://git-scm.com/docs/gitignore )
* 많이 쓰이는 형식 <br>
  1.모든 file.c - file.c <br> 
  2. 모든 .c 확장자 파일 - *.c <br>
  3. .c 확장자지만 무시하지 않을 파일 - !not_ignore_this.c 
    
   


