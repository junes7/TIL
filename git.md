## Git

> Git은 분산형버전관리시스템(DVCS)이다.
>
> 소스코드 형상 관리 도구로써, 작성되는 코드의 이력을 관리한다.

## 0. 기본설정

아래의 설정은 이력 작성자(author)를 설정하는 것으로, 컴퓨터에서 최초에 한 번만 설정하면 된다.

```bash
$ git config --global user.name junes7
$ git config --gloabl user.email 2junes@naver.com
```

## 1. 로컬 저장소(repository) 활용

### 1.저장소 초기화

```bash
$git init
Reinitialized existing Git repository in C:/Users/student/Desktop/TIL/.git/(master) $
```

* `(master)` 는 현재 있는 브랜치 위치를 뜻하며 `.git` 폴더가 생성된다.
* 해당 폴더를 삭제하게 되면 모든 `git` 과 관련된 이력이 삭제된다.

### 2. add

이력을 확정하기 위해서는 `add` 명령어를 통하여 `staging area` 에 `stage` 시킨다.

```bash
$ git add .			# 현재 디렉토리를 stage
$ git add README.md # 특정 파일을 stage
$ git add images /  # 특정 폴더를 stage
```
`add`를 한 이후에는 항상 `status`명령어를 통해 원하는 대로 되었는지 확인한다.

```bash
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   git.md

```

### 3. commit

`git`은 `commit`을 통해  이력을 남긴다.

커밋 시에는 항상 메시지를 통해 해당 이력의 정보를 나타내야 한다.

```bash
$ git commit -m 'Init'
[master (root-commit) 4a1d84a] Init
 1 file changed, 15 insertions(+)
 create mode 100644 git.md
```

```bash
$ git log
commit 4a1d84aa7323f2f3edc6da109f8e5d9b6bd7e0d2 (HEAD -> master)
Author: junes7 <2junes@naver.com>
Date:   Thu Dec 5 17:03:49 2019 +0900

    Init
```

## 2. 원격 저장소(remot repository) 활용

> 원격 저장소는 다양한 서비스를 통해 제공 받을 수 있다.
>
> github, gitlab, gitbucket

### 1. 원격 저장소 등록

```bash
$ git remote add origin https~
```

원격 저장소를 `origin`이라는 이름으로 해당 url로 설정한다.

등록된 원격 저장소는 아래의 명령어로 확인할 수 있다.

등록은 한 번만 실행하면 된다.

```bash
$ git remote -v
```

### 2. 원격 저장소 push

```bash
$ git push origin master
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 4 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (6/6), 1.42 KiB | 729.00 KiB/s, done.
Total 6 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), done.
To https://github.com/junes7/TIL.git
 + d696474...f2b4259 master -> master (forced update)
Branch 'master' set up to track remote branch 'master' from 'origin'.
```

`origin`원격 저장소에 `push` 하게 되며, github에서 확인할 수 있다.

이후 작업 과정에서는`add`->`commit`으로 이력을 남기고 `push`로 업로드 하면 된다.
