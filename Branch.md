# Branch



## Branch를 쉽게 보기위한 사전작업

* `git log -all` : 만들어진 모든 브랜치를 볼수 잇는 명령어
* `git log --graph` : 브랜치들을 시각화해줄수있는 명령어

![image-20210716174044383](C:\Users\sskym\AppData\Roaming\Typora\typora-user-images\image-20210716174044383.png)

​																<빨간색 줄로 그래프형식을 보여준다>

* `git log --oneline` : log를 한줄만 보여주는 명령어
* `git log --all --graph --oneline` 한줄로 사용가능하다. 



## Branch를 위한 명령어

* `git branch` : branch의 목록을 보여주는 명령어
* `git branch [브렌치 명]` : 새로운 branch를 생성한다.

> HEAD -> master , *master는 현재 마스터에 속해있다는 의미이다.
>
> `git chechout [브렌치명]`: 가고싶은 branch로 시점이 이동하며 HEAD는 가고싶은 branch로 향한다.

* HEAD -> [브렌치명]   :  git check out apple

  ![image-20210716173301107](C:\Users\sskym\AppData\Roaming\Typora\typora-user-images\image-20210716173301107.png)

* `git branch master`

  ![image-20210716173627385](C:\Users\sskym\AppData\Roaming\Typora\typora-user-images\image-20210716173627385.png)



# merge

`git merge`는 다른 브렌치를 현재 checkout 된 브렌치에 merge하는 명령이다.  merge 하고 나서 현재 브렌치가 merge된 결과를 가리키도록 옮긴다.

### 병합하는 브렌치명이 다를때 Merge

`git merge [브랜치명]` : 해당 브랜치가 master와 merge된다.

![image-20210716194407288](C:\Users\sskym\AppData\Roaming\Typora\typora-user-images\image-20210716194407288.png)

​                                                            <merge의 시작부터 과정 >

### 병합하는 파일 명이 같을 때 Merge

파일의 이름이 같을때도 서로 다른 부분을 찾아서 병합을 해준다. 하는 방법은 똑같다.



## merge CONFLICT

``` 
not something we can merge
```

 Merge CONFLICT가 된다는 에러문인다.

```shell
sskym@DESKTOP-V1R6F0J MINGW64 ~/gitpratice/merge (master)
$ git merge 02
Auto-merging work.txt
CONFLICT (content): Merge conflict in work.txt
Automatic merge failed; fix conflicts and then commit the result.

```

git status

```shell
$ git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   work.txt

no changes added to commit (use "git add" and/or "git commit -a")

```

txt 파일 안 모습

```
# title
content
<<<<<<< HEAD 현재 branch(master)의 내용
masterw
=======  :구분자
02
>>>>>>> 02 branch(02)의 내용
#title
content

```

충돌이 있어 났을때 branch(master)와 branch(02)중 선택 하면된다.(둘다안하고 둘다해도된다.)

직접 수정할 수 있다.

```
# title
content

masterw, 02


#title
content

```

수정한후 `git add`  +`git status`

```
$ git status
On branch master
All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)

Changes to be committed:
        modified:   work.txt
```

commit 후 브랜치를 보면 병합이 된 것을 알 수있다.

```
$ git log --all --graph --oneline
*   2ebf315 (HEAD -> master) Merge branch '02'
|\
| * 9b2035c (02) o2 work2
* | 38f36b6 master work2
|/
* a170707 work1
```

충돌이 있을때 git은 정말 효율적으로 작용한다.

 ## git은 어떻게 충돌을 발견하는가?

### CONFLICT 3WAY MERGE

| hear  | base | there | 2way merge | 3way merge      |
| ----- | ---- | ----- | ---------- | --------------- |
| A     | A    | A     | A          | A               |
| B ->H | B    | B     | Confict    | 자동 병합O -> H |
| C     | C    | C->T  | Confict    | 자동 병합O -> T |
| D ->H | D    | D->T  | Confict    | 자동 병합 X     |

hear와 there을 합칠때 같은 것은 그대로 가고 hear와 there가 다를때 충돌이 일어난다.

2way merge에 비해 3way merge가 자동병합이 가능하다.

### git merge tool

* p4merge을 git bash에서 실행시키기 위해서는 아래 코드를 실행시켜준다.

  ```
  $git config --global merge.tool p4merge :merge.tool을 p4를 사용한다.
  $git config --global mergetool.p4merge.path 'C:\Program Files\Perforce\p4merge.exe': p4merge의경로
  ```

* 위 코드 실행 후 `git mergetool`을 입력하면 p4merge프로그램이 실행된다.

* ![image-20210717112515283](C:\Users\sskym\AppData\Roaming\Typora\typora-user-images\image-20210717112515283.png)

  수정하고 저장하면 add까지 자동으로 완료 된다. 그리고 `git status`를 하면

  ```
  $ git status
  On branch o2
  All conflicts fixed but you are still merging.
    (use "git commit" to conclude merge)
  
  Changes to be committed:
          modified:   work.txt
  
  Untracked files:
    (use "git add <file>..." to include in what will be committed)
          work.txt.orig : 
  ```

   수정한것이 맞는지 확인하는 절차가 남아있다. 맞으면 `work .txt.orig`.를 지우면된다.

* 위에 내용이 잘 처리되었으면 CONFLICT가 해결된다.

  ```
  $ git log --all --graph --oneline
  *   ac6dcd9 (HEAD -> o2) Merge branch 'o3' into o2
  |\
  | * 1f67fc0 (o3) o3 work
  * | c8ba02f o2 work
  |/
  * 7ce99ee (master) work1
  
  ```

  
