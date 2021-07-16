# GUI VS CLI

>CLI를 배워야하는 이유는 언어의 능력이 엄청 크기 때문이다. 
>
>시간의 순서에 따라 명령을 내릴수 있어 GuI비에 엄청난 장점이다. 또한 GUI 는 컴퓨터의 자원을
>
>너무 많이 사용한다. 매우작은 컴퓨터 자원으로도  사용가능하다.햣 



# git

버전을 통해 코드 관리도구

* .git파일은 .git 파일 위에 또잇어서는 안된다. 



## SCM & VCS

* SCM: Source Code Management(소스 코드 관리)
* VCS: Version control System(버전 관리 시스템)



## Git?

* 버전 관리도구
  * 변경 이력 트래킹
  * 언제든 특정 시점으로 이동 가능

* 백업도구
* 협업도구

## Git 버전관리

>중요 : git은 **폴더 단위**로 코드를 관리

* 커밋 == 버전 생성 == 스냅샷 촬영 == 현재 상태 저장



## git init : initialize repository

특정 폴더를 git으로 관리 시작

* (master)표시를 프롬포트에 표시
* `.git`폴더 생성
  * `.git`폴더 삭제시 git 관리 중지



## .git

git repository로 지우면 git으로써 역할을 하지 못한다. 

cd .git 

```
(GIT_DIR!) : .git 폴더안이야 조심해야돼
```



## git status

git에게 상태 확인

* git init 직후

``` 
On branch master: master라고 하는 branch에 있어
No commits yet: 아직 commit 없어
nothing to commit (create/copy files and use "git add" to track)
: commit 할 게 없어 (트래킹 하고 싶으면 `git add` 명령어를 사용해)
```

* `a.txt` 파일 생성 직후

``` 
Untracked files: 추적되지 않은 파일이 있어
(use "git add <file>..." to include in what will be committed)
a.txt (빨강)
commit 될 수 있게 포함하고 싶으면 `git add <파일명>`을 사용해
nothing added to commit but untracked files present (use "git add" to track)
```

* `git add a.txt` 직후

``` 
Changes to be committed: commit될 변경 사항이 있어
(use "git rm --cached <file>..." to unstage)
new file: a.txt (초록)
```



## git add [파일명] : add to staging area

Staging Area(스냅샷 무대)에 파일 추가

working tree에 있는것을 -> Staging Area에 올리는 것

git은 저절로 파일을 관리하지 않는다.( 저절로 tree 에서 area로 옮기지 않는다.)



## git commit -m "커밋 메시지" : create version

버전을 생성

* 커밋(버전)구성 요소
  * 해시(Hask) 
  * 작성자
  * 날짜
  * 커밋메시지: 버전에 대한 설명
* git commit -am "커밋 메시지"  : add와 commit을 한번에 할 수 있다(최초한번은 add로 트랙해야지 commit과 같이 쓸 수 있다.)

Staging Area에 있던것이 -> Repostiroty 로 옮겨진다.

`git commit --amend` : **마지막 커밋 메세지를 바꿀 수 있습니다.**

## git log : show version

버전(커밋)들의 히스토리(로그)

git log --stat :  각각의 버전별로 어떤 파일이 연류되어있는지 알수 있다.

git log -p

git log --oneline : commit id, title 메시지만 조회



## git config

설정

* git config[설정할 내용] [설정할 값]
  * git config user.name 'shin chanwoo'
  * git config user.email 'sskymc@gmail.com'
  * git config ~global : 전역설정



``` 
Author identity unknown: 작자 미상
*** Please tell me who you are.: 니가 누군지 말해주세요.
Run 다음을 실행하세요
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
to set your account's default identity.
Omit --global to set the identity only in this repository
```



## git 버전관리



| working tree                     | staging Area               | Repository    |
| -------------------------------- | -------------------------- | ------------- |
| 아직 버전으로 만들어지기 전 단계 | 버전을 만드려고하는 파일들 | 만들어진 버전 |



## git 명령어

* nano [파일명] : 파일을 생성하고 그안에 내용을 입력하는 창으로 들엉감
* cat [파일명] : 파일 내용을 보여주는 명령어



## git diff : show changes

초록 부분은  새버전으로 바뀐 모습을 보여주고 

빨간 부분에서는 변해서 없어진 모습을 보여준다.



git diff을 통해서 작업하는 마지막 버전과 워킹트리사이에서의 차이점을 파악하는 것을 가지고

내가 무엇을 했는지 반성을 하고 최종적으로 검토를 할 수 있는 것이 버전관리를 사용하는 가장

큰 호용입니다. 



## git checkout : 시간여행을 할 수 있다.

내가 사용할 브랜치를 지정하는 것이다.

시간을 탐색할 수 있다.

최신버전이 master이다. 즉 브랜치다. 해더가 마스터를 가르키고있다는 것은 실제 마지막버전을 가르키는 것이다. 

## git reset --hard [commit ID] : 버전리셋

`git reset`은 삭제 시키는게 아닌 지정한 버전으로 가는 것이다. (버전을 리셋하는게 아닌 버전으로 리셋하는 것이다.)  

* `--soft`, `--mixed`는 수정하고 있는 것은 살리면서 리셋 하는 것이다.
* `--hard`는 수정하고 있는 것 까지 지우는 가장 강력한 것이다.
* 협업을할 때는 공유되기 전 단계에서만 리셋을 시켜야한다. 공유된 이후에 리셋을 하면  엉키게된다.

## git revert : 리셋과 용도가 많이 비슷하다.

삭제의 목적과 보전의 목적을 동시에 달성할 수 있다.

![image-20210715232504015](C:\Users\sskym\AppData\Roaming\Typora\typora-user-images\image-20210715232504015.png)

`revert` 는 R3를 지정하고 싶으면 R4의 commit ID가 필요하다.

`revert`는 R4의 변화를 취소한 것이다. 즉 취소했으므로 R3 지정되는 것이며 R4도남는다.

`revert`는 역순으로 순서대로 내려가면서 revert를 해야한다. 즉 Messege 1 로 되돌리기 위해서는 R4, R3, messge2순으로 revert를 시켜야 한다.

git revert는 모든것을 되돌리는게 아닌 지정한 commit을 할때에 변화만을 되돌리는것이다.

## git 마무리

>버전관리의 핵심은 비교이다. 현재와 과거의 버전의 비교를 통해 과거를 되돌아 될 돌아 보는 것이 엄청난 이점을 가지고 있다. 또한 백업에 용이한다. 지속적으로 인터넷에 업로드함으로써 협업까지 같이 나갈 수 있는 장점또한 있다.
>
>### 이후 공부법
>
>1. 검색엔진에 `diff tool`을 검색하여 여러 tool들을 확인해보자
>
>2. `.gitignore` : 버전관리를 해선 안되는 것을 따로 등록시키는 명령어
>
>3. git의 가장 중요한 특징이자 혁신은 branch이다. branch는여러가지 상태가 같이 공존할 수 
>
>  있게 해준다. 
>
>4. `tag`: commit id가 어려워 id를 바꿀있게 도와주는 tag를 이용하면 좋다.
>
>   





# Git Backup

백업의 방법 두가지

* 자유롭지만 어려운방법 : 직접 백업서버를 구축하는 것이다. 
* 제한적이지만 쉬운방법 :  hosting  원격 저장소를 운영하는 곳(github)에 백업하는 방법



Local Repository(1) ---------------------> Remot Repositroty ---------------------->Local Repository (2)

​                                           push                                                      Clone

Local Repository <--------------------- Remot Repositroty

​                                          pull

Push하고 Pull를 계속 반복함으로써 백업을 하고 자동 이동성을 극대화할 수 있다.



## 백업

1. 원격 저장소 생성
2. remote  정보입력
3. git push



## Remote Repository

### git Hosting

* github
* gitlab.com



## Local -> Remote (http 방식)

push an existing repository from the command line : 노컬에서 저장소로 옮기는 법

```
git remote add origin https://github.com/doungge/my-repo.git
git branch -M main
git push -u origin main
```



## Remote -> Local(http)

gi t pull



### `git remote`

---

* `git remote add origin [백업주소]`

* 위에를 입력시  `git remote`  `origin`이 출력된다.
* `git remote -v`: 원격저장소의 주소를 나타내준다.



## git push

로컬 저장소의 파일들을 원격 저장소에 백업

* `git remote`로 원격저장소와 연걸이 되었을 시에 실행이 된다.

* `git push`

  ```
  $ git push : 입력시 다음 코드창에 git push --set-upstream origin master 입력후 로그인한다.
  fatal: The current branch master has no upstream branch.
  To push the current branch and set the remote as upstream, use
  
      git push --set-upstream origin master
  ```

  한번 등록을 한후에 `git push`를 입력하면 Remote repository에 들어가게 된다.

* `git push -u origin master`



## CLONE (Remot Repository --> Local Repository(2))

백업 받은 것을 다시 복원하는 방법

* `git clone [저장소 주소]`새로운 폴더에 복제 하는 방법이다.
* `git clone [저장소 주소] mkdir [폴더명]` 을 사용하면 새로 만든 폴더안에 복제 하는 방법이다.



## Git Pull

git pull 을 사용하면 원격저장소에 있는 파일들을 다른 Local Repositroy로 불러 오는것이다.





## 이후 공부

* ssh 알아보기

* issue tracker 기록 문제 기록 (협업기능과 시너지 좋다.)

