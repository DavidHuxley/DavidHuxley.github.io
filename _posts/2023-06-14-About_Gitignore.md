
### Github에 사용하면서 아무 생각 없이 푸시하면 보안이슈로 코딩인생이 끝날수도 있다.

진짜로 끝날 수도 있다.
깃헙은 정말 편리하지만 보안수칙들을 제대로 지키지 않는다면 소스코드 혹은 프로젝트 기밀 유출은 해커들에게 누워서 떡 먹기나 다름 없기때문.
> ### Reference
> [깃허브 저장소에 숨겨진 데이터 유출 위험](https://www.boannews.com/media/view.asp?idx=68958)
>[전 세계 보안 팀들이 놓치고 있는 거대 취약점, 깃허브](https://www.ciokorea.com/news/210034)


나와 같은 조무래기 개발자들에겐 가장 프라이빗 한 자료까지 다 펼쳐놔도 아무도 관심을 가지지 않기 때문에 크게 상관 없을 수도 있지만, 장차 위대한 프로젝트를 할 마음이 조금이라도 있다던가, 그게 아니더라도 협업을 해야하는 입장이라면 프로젝트 진행시 꼭 설정해둬야 하는게 있다.

***

## .gitignore

### gitignore이란?
- Git의 root 디렉토리에 저장됨으로써, Git Repository, Staging Area에 추가되면 안되는 폴더, 파일등을 정의해주는 파일이다.
- Staging Area에 올라가지 않기 때문에 tracking 되지 않고 따라서 버전관리에서 제외 된다고 보면 된다.

> ### Reference
> [각종 환경별로 분류한 .gitignore example](https://github.com/github/gitignore)
>[프로젝트에 맞게 gitignore 자동생성](https://www.toptal.com/developers/gitignore)


### 왜 굳이 gitignore로 정의해서 따로 빼둘까?
예를 들면 민감한 환경변수라던지, 중요한 개인정보가 들어있는 파일이라던지, 프로젝트 속에 숨겨뒀던 나만의 소중한 비밀이라던지.. 제외시킬 파일은 이 글에서 앞으로 소중이라 부르겠다. 어쨌든 public repo에 그걸 푸시한다는건 길바닥에 나만의 일기장을 펼쳐놓는것과 다름없다. 


### gitignore를 활용해보자!

활용방법은 우리집 뽀삐도 가르쳐주면 할만큼 간단하다.
방법은 다음과 같다. 

- 우선 해당 프로젝트의 최상단 폴더에 생성해야한다
- #은 주석이다. 어떤 파일을 제외시킨건지 설명을 적어놓는다.
- 표준 glob 패턴을 사용한다. 
- /로 시작하면 해당 디렉토리에만 적용된다.
- 디렉터리 전체를 제외시킬경우 /를 디렉터리 끝에 쓰면 된다.
- !로 시작하는 패턴의 파일은 제외시키지 않는다
- *.확장자를 추가함으로써 특정 확장자 전체를 제외할 수 있다.

다음은 아주 쉬운 예제가 있어서 주워왔다.
[.gitignore 파일 작성 규칙](https://shilan.tistory.com/entry/gitignore-%ED%8C%8C%EC%9D%BC-%EC%9E%91%EC%84%B1-%EA%B7%9C%EC%B9%99)

```
ex)
# 모든 확장자 .a 파일을 무시
*.a
 
# 무시하는 모든 확장자 .a 파일들 중에서 lib.a 파일은 무시하지 않음
!lib.a
 
# Project/
#  ㄴ.gitignore
#  ㄴA/
#    ㄴa.txt
#    ㄴTODO/
#      ㄴtt.txt
#  ㄴTODO/
#    ㄴt.txt
#
# 현재 폴더 중에서 TODO 폴더에 있는 모든 파일을 무시
# (즉, t.txt 파일만 무시되고 tt.txt 파일은 무시되지 않음)
/TODO
 
# 프로젝트 전체 폴더 중 TODO라는 폴더명을 사용하는 TODO 폴더의 하위 파일은 모두 무시
# (즉, t.txt 파일과 tt.txt 파일 모두 무시됨)
TODO/
 
# Project/
#  ㄴ.gitignore
#  ㄴdoc/
#    ㄴd.txt
#    ㄴp.pdf
#    ㄴserver/
#      ㄴss.txt
#      ㄴpp.pdf
#
# 현재 폴더 중에서 doc 폴더 바로 밑에 있는 .txt 확장자 파일만 모두 무시
# 단, doc/server/ss.txt 와 같은 형식에서는 .txt 확장자 파일이 무시되지 않음
doc/*.txt
 
# 현재 폴더 중에서 doc 폴더 하위에 있는 .pdf 확장자 파일은
# doc 폴더 하위 어떤 폴더에 들어 있더라도 모두 무시
# (즉, p.pdf 파일과 pp.pdf 파일 모두 무시됨)
doc/**/*.pdf
```

### gitignore 만들기전에 이미 커밋과 푸시를 했다면
![](https://velog.velcdn.com/images/huxleyseo/post/01aed2d5-3c09-412a-892c-299008fa6e3e/image.png)

나 처럼 프로젝트 시작 시점에 gitignore를 깜빡하고 나의 소중이들을 git에 올렸다면 안타깝게도 꽤나 귀찮은 과정을 거쳐서 지워야한다. ~~아니면 .git 폴더 지우고 새로 git init해도 됨~~

gitignore 파일 생성 이전에 이미 올려둔 파일은 자동으로 삭제되지 않고 로컬에서 지웠다고 해도 따라서 지워지진 않는다. 따라서 정리 할 파일이 있다면 git 명령어를 통해서 먼저 정리부터 해야한다.

명령어는 다음과 같다. 
```
# 원격 저장소와 로컬 저장소에 있는 파일을 삭제한다.
$ git rm [File Name]

# 원격 저장소에 있는 파일을 삭제한다. 로컬 저장소에 있는 파일은 삭제하지 않는다.
$ git rm --cached [File Name]
```
당연하게도 git 명령어를 이용해 파일을 삭제처리한 뒤엔 커밋과 푸시를 진행해야한다. 


### 근데 또 확인할게 있음 history
![](https://velog.velcdn.com/images/huxleyseo/post/0578de5b-5b68-490a-97b2-aacdabbbc7e5/image.png)

방금 전의 명령어를 통해서 삭제처리를 했어도 github의 history를 통해서는 관련 내역들을 찾아볼 수 있기 때문에 보안이슈가 생긴다. 하.. 깃헙에서 완전히 삭제하고 싶거든 **filter-branch**를 명령어를 이용해 커밋 내역을 삭제해야한다.

명령어는 다음과 같다.
```
git filter-branch -f --index-filter 
'git rm --cached --ignore-unmatch [지우려는 파일의 경로와 이름] --prune-empty -- --all
```

명령어를 분해해서 살펴보면

- git filter-branch 는 git 저장소에서 필터링을 하라는 명령어
- -f 는 force의 줄임말이다. 강제로 진행시켜!
- --index-filter 는 Staging Area(인덱스)에 대해서 필터링 하라는 뜻
- 'git rm --cached --ignore-unmatch [지우려는 파일의 경로와 이름]' 는 실제로 동작하는 필터링 수행 명령어다 
-	git rm 명령어는 위에서 본거처럼 삭제시켜주고
-	--cached 는 로컬말고 원격저장소에 있는거만
-	--ignore-unmatch 는 지우려는 파일이 모든 커밋에서 하나도 없어도 오류가 발생하지 않도록 
- --prune-empty 는 삭제하고나서 비어있는 커밋이 생길 경우 지워준다.
- -- 는 구분자다. 
- --all 는 repo의 모든 브랜치와 태그에서 작업을 수행하라는 뜻


해당 명령어를 다 처리하고 나면 다시 원격 저장소로 -f 옵션을 걸어서 푸시하면 끝.

#### 너무 너무 귀찮다. gitignore는 꼭 초기에 만들어놓고 쓰도록 하자. 귀찮다고? 코딩인생 끝나면 난몰라



## <span style="color: rgba(200,0,0,0.7);">다시 확인 해봤는데 filter-branch는 이미 legacy라고 한다. 하.. 다음 포스팅때 대안을 적어보겠다.</span>