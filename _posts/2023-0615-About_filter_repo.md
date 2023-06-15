---
title: About "filter-repo"
date: 2023-06-15 22:45:00 +0900
categories: [Git]
tags: [Git, filter-branch, filter-repo]     # TAG names should always be lowercase
---


### 사실 난 예전에 멋도 모르고 뭐 대충 된다고 하니까 되겠지 느낌으로 git 명령어를 치다가 개인프로젝트 도중에 로컬,원격 repo를 싹 다 날려버린 경력이 있다. (소리질렀음)

그 덕분인지 지난 포스팅때 봤던거처럼 filter-branch 명령어를 하나하나 해석해보는 신중함을 얻었다.

![](https://velog.velcdn.com/images/huxleyseo/post/af5e1597-0fd0-4e0e-9f11-da94610a9c60/image.png)


## ??
심장이 철렁하고 예전의 아찔했던 기억이 떠올랐으나 다행히 내가 생각하는 그런건 아니였다.
  대충 해석해보면** filter-branch가 문제가 아주 많다고 대신 filter-repo를 써보는게 어떻냐**는거였다.
  
  휴, 다행이다 어서 filter-repo 명령어를 사용해서 나의 소중이들을 히스토리에서 지우자.
  
  
## filter-repo 설치
  
  **filter-repo는 filter-branch와 다르게 git의 기본 기능으로 제공되지 않는다.**
 그렇지만 훨씬 안정적이고 빠르니 어서 설치해보도록 한다.
  
  filter-repo는 일반적으로 pip으로 설치하는데 pip은 python으로 작성된 패키지 소프트웨어를 설치, 관리하는 패키지 관리 시스템이다.
  Window에선 pip이 가장 쉽고 빠르니 어서 해당 명령어를 치도록 한다.
  
  
  ```
  macOS 및 Linux
  brew install git-filter-repo
  
  WindowOS 
  pip install git-filter-repo

  ```
  
  아 참고로 pip은 python2.7.9 이상부터는 함께 설치되므로 python이 설치되어있다면 pip도 기본 제공이다. 혹시 모르니 해당 명령어를 쳐서 python 버전을 확인해보도록 한다. 
 ```
 python --version
 ```
  파이썬이 없다면 우선 파이썬부터 설치하고 오는걸로 하자.
 또한, filter-repo는 pip 19.0 부터 되니까 역시 해보고 안되면 버전 확인을 해보자
  19.0 이하면 아래 명령어로 버전업하면 된다. 아마 19년 이후 설치 한 사람은 일부러 다운그레이드 하지 않는 이상 19.0이상일것임
```
pip --version
python -m pip install --upgrade pip
```
  
### filter-repo 명령어  
filter-repo가 설치 되었다면 filter-branch에 비해서 매우 간단한 명령어 한 줄 입력하면 끝이다.
```
git filter-repo --invert-paths --path [지우려는 파일의 경로와 이름] --force
```

명령어를 해석해보면 
- filter-repo는 특정 파일 또는 디렉토리를 git 히스토리에서 아예 지워버리는 친구
- --invert-paths는 명시된 경로 이외의 모든 경로를 필터링해준다.
- --path [지우려는 파일의 경로와 이름]는 이름 그대로 제거하려는 파일 또는 디렉토리의 경로를 지정한다.
- -force는 지난번에 설명한거처럼 변경내용을 강제로 덮어씌운다. **이거 안쓰면 커밋 히스토리 안지워짐!**

명령어를 입력하면 filter-branch를 사용할때보다 훨씬 빠르고 안정적으로 정리를 해버리는데 당연히 로컬에 있는 친구들을 제거한거라 원격저장소에 있는 히스토리는 그대로다.

그럼 어떡하면 좋을까? 그냥 **git push --force 하면 끝!**

### 그렇지만 또 귀찮게한다. 
![](https://velog.velcdn.com/images/huxleyseo/post/39b382d6-aa86-4b9a-8936-9f3200dea150/image.png)

  왜 그러는지 모르겠지만 filter-repo를 쓰고나면 git remote가 끊겨버린다.
  다시 remote를 연결해준다.

  ```
  git remote add [repo url] 
  git push -f
  ```

이제 깃헙가서 보면 커밋 히스토리가 깔끔하게 정리되어있다. 진짜 끝
  
>   [Ref](https://github.com/newren/git-filter-repo)

