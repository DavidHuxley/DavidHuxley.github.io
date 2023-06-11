---
title: 협업을 위한 Git Commit Message Convention
date: 2023-06-11 21:17:00 +0900
categories: [Git]
tags: [Convention, Git]     # TAG names should always be lowercase
---


##### 프로젝트를 진행한다면 버전관리는 필수이고, Git을 이용할때 commit message를 작성하는것 역시 필수이다.

##### 비록 혼자서 프로젝트를 진행하고 있지만 내가 보기에, 더 나아가 앞으로 협업을 할 때도 가독성있고 효율적인 커밋 메세지 작성을 위해서 Git Commit Message Convention을 알아보았다.

##### 컨벤션은 팀마다, 개발자마다 다르지만 가장 흔하게 쓰는 컨벤션을 참고했다.

***

###  Commit Message Structure



> type: Subject (제목)
> 
> body (본문)
> 
> footer (참고사항)

- 커밋 메세지를 아래와 같은 구조로 작성하면 된다.
- 각 파트별로 한 줄씩 띄워서 사용한다.
- footer는 선택사항으로 필요시 작성하면 된다.

각 파트에 대한 설명은 아래와 같다.

***


### Type List

##### Type의 종류는 다양하지만 가장 많이 쓰이는것을 정리하면 아래와 같다.

|Type Name|Description|
|---|---|
|**Feat**|	새로운 기능을 추가|
|**Fix**|	버그 수정|
|**Docs**|	문서 수정|
|**Design**|	CSS 등 사용자 UI 디자인 변경|
|**Style**|	코드 포맷 변경, 세미 콜론 누락, 코드 수정은 없는 경우|
|**Refactor**|	프로덕션 코드 리팩토링|
|**Comment**|	필요한 주석 추가 및 변경|
|**Test**|	테스트 코드, 리펙토링 테스트 코드 추가, Production Code(실제로 사용하는 코드) 변경 없음|
|**Init**|	프로젝트 초기 생성|
|**Chore**|	빌드 업무 수정, 패키지 매니저 수정, 패키지 관리자 구성 등 업데이트, Production Code 변경 없음|

- 타입은 하나만 결정해서 사용하도록 한다.

### Subject

- 제목은 50글자 이내로 작성한다.
- 첫글자는 대문자로 작성한다.
- 마침표 및 특수기호는 사용하지 않는다.
- 수행 한 작업에 대해 명령형으로 작성한다. 


### body

- 상세한 설명이 필요없는 커밋의 경우 생략해도 된다.
- 최대 72자 이내로 작성한다.
- 설명이 필요한 경우 가능한 상세히 작성한다.
- '어떻게' 보다는 '무엇을', '왜' 변경했는지 작성한다. 

### footer

- footer는 선택사항으로 참고사항이 있을 경우 작성한다.
- issue tracker ID를 명시할 경우 작성한다.
- 여러개의 이슈ID가 있을 경우 쉼표를 사용해 구분한다.
- issue tracker의 유형 역시 다양하지만 가장 많이 쓰이는 것들은 아래와 같고 이 중 하나를 사용한다.

 <span style="color:gray">Fixes: 이슈 수정중 (아직 해결되지 않은 경우)</span>
     <span style="color:gray">Resolves: 이슈를 해결했을 때 사용</span>
     <span style="color:gray">Related to: 해당 커밋에 관련된 이슈번호 (아직 해결되지 않은 경우)</span>
       <span style="color:gray">Ref: 그 외 참고 할 이슈, 링크 등이 있는 경우 (참고할만한 링크가 있을 때 사용했다.)  </span>

```
    ex) Resolves: #42
    	Related to: #32, #27
```
  
***
 ### Example #1
  
  ```
  Refactor: 이미지 업로드 관련 수정
 
  서버 부담을 줄이기 위해 레거시 코드 대거 정리 및 파일 크기 제한하였음
  
  Ref: #13, #18
  ```
  ### Example #2 
  ##### Udacity Git Commit Message Style Guide 
  
```
feat: Summarize changes in around 50 characters or less

More detailed explanatory text, if necessary. Wrap it to about 72
characters or so. In some contexts, the first line is treated as the
subject of the commit and the rest of the text as the body. The
blank line separating the summary from the body is critical (unless
you omit the body entirely); various tools like `log`, `shortlog`
and `rebase` can get confused if you run the two together.

Explain the problem that this commit is solving. Focus on why you
are making this change as opposed to how (the code explains that).
Are there side effects or other unintuitive consequences of this
change? Here's the place to explain them.

Further paragraphs come after blank lines.

 - Bullet points are okay, too

 - Typically a hyphen or asterisk is used for the bullet, preceded
   by a single space, with blank lines in between, but conventions
   vary here

If you use an issue tracker, put references to them at the bottom,
like this:

Resolves: #123
See also: #456, #789

  ```
***
 커밋 메세지를 어떻게 작성하는지에 대해서 알아봤는데 사실 어떻게 쓰느냐도 중요하지만, 어느 시점에 커밋을 하는지도 상당히 중요하다. Ctrl+S 마냥 시도때도 없이 눌렀다간 히스토리가 상당히 더러워진다.
 
 ### 적절한 커밋시점
 
 일반적으로 커밋을 언제, 몇번 한다고 정해진 컨벤션은 찾아볼 수 없지만 일반적으론 시간을 정해서 하기보단 아래의 경우에 커밋을 한다고 할 수 있다.
 
 - 어떤 기능을 개발하거나 테스트를 끝냈을 때
 - 새로운 테스트 케이스를 추가할 때
 - 버그를 픽스했을 때 
 
 
대부분의 개발자들은 시간에 기준을 두는게 아니라 의미있는 코드의 추가,변경이 있을 때 (그 변경이 사소하더라도) 하는게 좋고, Ctrl+S 마냥 시도때도 없이 눌렀다간 커밋 히스토리가 지저분해져 이슈를 추적하기 어렵게 한다고 한다. 추가로 협업시엔 팀원들과 브랜치 전략을 잘 세운다면 더욱 원활하게 프로젝트를 진행할 수 있지 않을까 생각이 든다.
 
***
 ### Reference
- [언제 커밋을 하면 좋을까](https://www.quora.com/When-is-a-good-time-to-Git-commit) 
- [Udacity Git Commit Message Style Guide](https://udacity.github.io/git-styleguide/)
- [Writing a Good Git Commit Message](https://www.gitkraken.com/learn/git/best-practices/git-commit-message)
  