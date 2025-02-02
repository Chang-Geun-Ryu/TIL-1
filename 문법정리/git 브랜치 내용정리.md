## 협업을 위한 Git 활용하기 



####  Git 설정

~~~
Git은 커밋을 수행할 때 마다 Author라는 속성에 사용자의 이름과 이메일 주소를 포한시킨다.
$: git config --global user.name  // Daisy
$: git config --global user.email  // dev.daisiee@gmail.com 

--global옵션은 현재 설정하는 속성을 컴퓨터의 모든 프로젝트에도 적용하라는 의미다.

~~~



#### 새 프로젝트 시작하기

~~~
$: git init  // 새로운 Git데이터베이스를 생성
~~~



#### Git Clone

~~~
$: git clone
~~~



#### Git Add (staging)

- 주어진 파일의 스냅샷을 만들어 저장소에 저장함으로써 나중에 커밋할 때 참조할 수 있게 한다. (추적)

- 로컬 초안을 작성한다.

스테이징 영역은 다른사람과 공유되거나 동기화하지 않으며 오직 로컬 컴퓨터에만 존재한다.

~~~
$: git add . 
~~~



#### Git Commit

~~~
$: git commit --message ""
$: git commit -m ""
~~~



#### Git Status

~~~
$: git status 
~~~





## Branch



#### Branch Structure

~~~bash
master (베포용 브랜치)
develop (작업한 코드를 모으는 브랜치)
fear (issue별 브랜치)
~~~



git branch 

git branch -r 리모트에 대해서 알려줌 

git branch -a 로컬과 브랜치의 갯수와 리스트git 

git checkout[+브랜치명] 브랜치로 변경

git remote -v 별명 내역을 볼 수 있다 



### remote에 local 에서 만든 branch 추가하기

로컬에서 작업한 branch 를 stem 으로 remote 에서도 만들면서(별명과 함께) 업스트링한다.

▻ git push -u origin[별명] stem[브랜치명]

 Remote



###브랜치 지우기

▻ git branch -D stem[지우려는 브랜치]   *※대문자 조심*



#### Local branch 지우기

~~~swift
git push origin --delete [지울 브랜치 이름]

//remote에 접근할 때에는 push 로 접근하여야 한다.
~~~



### 로컬에서 지운 브랜치 다시 리모트에서 다운받기

리모트브랜치의 이름과 같은 브랜치 하나 로컬에서 만들기

▻ 브랜치로 checkout 하고 git pull [브랜치 별명] [브랜치명] ► 가져온다



### merge

반영할 곳으로 가서 거기서 머지~

▻ git merge [stem/마스터에 합칠 브랜치이름]



### 브랜치를 만드는 동시에 과거 땡기기

커밋 아이디를 이용하여 (시간이동) 과거로 돌아가기

ID Ex) b59b6e3bb623998f5854c1bdc2d555262e665276

▻ git checkout b59b6e3bb623998f5854c1bdc2d555262e665276 

↑ 위의 방식으로 하면 brnach 명이 ID로 되니까 아래방식을 권장

▻ git checkout -b <new-branch-name>

↑ "-b"를 활용하여 새로운 이름을 만들면서 과거 커밋시점으로 땡겨오기



###   미리 branch 만들고 과거 땡기기 

branch 를 먼저 만들고 그곳으로 체크아웃 

▻ git branch past b59b6e3bb623998f5854c1bdc2d555262e665276





#### Git 에는 동작하는 최소단위가 올라가야 한다.

※ [GIt Flow](https://danielkummer.github.io/git-flow-cheatsheet/index.ko_KR.html)



## Fork

issues 커밋할때 원본repo에(포크받은 repo) 가서 issues를 쓴다. 그럼 이슈넘버가 자동생성

브랜치따고 내용수정 후 커밋메세지 쓸 때 첫줄은 commitTitle

두번째 줄에 Resolved: #issueNum 쓰면 issue가 닫힌다. 단, master까지 올라가야 닫힌다.



첫번째 줄 ⇢ fix: somrthingsomthig

두번째 줄 ⇢ Resolved: #2





git 쓰고 mv

git mv README.md [변경하는장소]git



## pull

```
 $ git remote add upstream
https://github.com/final-project-team01/iOSHouseOfToday.git

 $ git pull upstream master
 
---
 $ git fetch upstream
 $ git merge upstream/master
```



Origin

> $ git pull upstream develop → main remote에 변경 된 자료 내 local로 땡기기
>
> $ git push origin develop  → 나의 remote에 local에서 땡긴 자료 업데이트



기본적으로 커밋 메세지는
* Subject (제목)
* Body (본문)
* Footer (꼬리말) 로 구성한다.



### `Type` : `Subject`

##### `Type` 

* `feat` : 새로운 기능 추가
* `fix` : 버그픽스
* `docs` : 문서 수정(README수정)
* `style` : 스타일 추가, 수정
* `refactor` : 코드 리펙토링
* `test` : 테스트 코드, 리펙토링 테스트 코드 추가



##### `Subject` 

제목은 50자를 넘기지 않고, 대문자로 작성하고 마침표를 붙이지 않는다.

과거시제를 사용하지 않고 명령어로 작성한다.

- "Fixed → "Fix"
- "Added → Add "



## git commit message 

> ### Categories
>
> feat - feature(기능)
> docs - documentations(문서)
> fix - bug fix(픽스)
> conf - set configurations(설정)

commit message 는 제목은 구나 절로 쓰고 내용은 문장단위로 코드에 대한 설명





git init 으로 하는방법

git push -u origin master 처음에만 해주면 된당

git remote 하는것

 git remote add orign https://github.com/JeongAKo/git-practice.git

Origin 은 별명

별명 바꿀라면 git remote rename 현재이름 바꿀이름



~~~
$ git checkout HEAD^ //부모단계(1단계)로 올라가기
$ git checkout HEAD~4 //돌아가고싶은 커밋갯수를 `~`뒤의 숫자로 명시
$ git branch -f master c1 //강제로 브랜치 옮기기
~~~

~~~
git branch -f master c6
git checkout HEAD~1
git brnach -f bugFix HEAD~1
~~~



#### git 지울때

rm -rf .git



#### git reset



#### git revert



#### git cherry-pick <Commit1> <Commit2> <...>



#### git tag









---

라이센스 MIT로 

MIT라이센스는 OPEN

Apache 라이센스는 소유권 주장 가능

GNU General Public License 잘못 하면 오염된다???

---



#### git ignore

vi gitignore 안에 들어가서 무시할 파일 쓰기





#### rebase

~~~
-master
-hotFix


$ git checkout hotFix 
$ git rebase master
~~~

두 브랜치가 나뉘기 전인 공통 커밋으로 이동하고 나서 그 커밋부터 지금 Checkout 한 브랜치가 가리키는 커밋까지 diff를 차례로 만들어 어딘가에 임시로 저장해 놓는다. Rebase 할 브랜치(역주 - hotFix)가 합칠 브랜치(역주 - master)가 가리키는 커밋을 가리키게 하고 아까 저장해 놓았던 변경사항을 차례대로 적용한다.

<img width="692" alt="스크린샷 2020-07-07 오후 2 41 38" src="https://user-images.githubusercontent.com/47776915/86720478-061a4600-c060-11ea-9ac1-a3f1f4b1ea3e.png">



`C4`의 변경사항을 `C3`에 적용하는 Rebase 과정. 그리고 나서 `master` 브랜치를 Fast-forward 시킨다.



~~~
$ git checkout master
$ git merge experiment
~~~

<img width="670" alt="스크린샷 2020-07-07 오후 2 42 54" src="https://user-images.githubusercontent.com/47776915/86720605-26e29b80-c060-11ea-9634-752d5a7494de.png">

 Merge 이든 Rebase 든 둘 다 합치는 관점에서는 서로 다를 게 없다. 하지만, Rebase가 좀 더 깨끗한 히스토리를 만든다. Rebase 한 브랜치의 Log를 살펴보면 히스토리가 선형이다. 일을 병렬로 동시에 진행해도 Rebase 하고 나면 모든 작업이 차례대로 수행된 것처럼 보인다.

Rebase는 보통 리모트 브랜치에 커밋을 깔끔하게 적용하고 싶을 때 사용한다. 아마 이렇게 Rebase 하는 리모트 브랜치는 직접 관리하는 것이 아니라 그냥 참여하는 브랜치일 것이다. 메인 프로젝트에 Patch를 보낼 준비가 되면 하는 것이 Rebase 니까 브랜치에서 하던 일을 완전히 마치고 `origin/master` 로 Rebase 한다. 이렇게 Rebase 하고 나면 프로젝트 관리자는 어떠한 통합작업도 필요 없다. 그냥 master 브랜치를 Fast-forward 시키면 된다.



#### Rebase 의 위험성

Rebase가 장점이 많은 기능이지만 단점이 없는 것은 아니니 조심해야 한다. 그 주의사항은 아래 한 문장으로 표현할 수 있다.

##### 이미 공개 저장소에 Push 한 커밋을 Rebase 하지 마라

[참고](https://git-scm.com/book/ko/v2/Git-브랜치-Rebase-하기)

