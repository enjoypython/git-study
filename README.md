# Git  Content
> Git 공부하면서 정리한 자료

<br>

# 목차
- [레퍼런스 링크](#1)
- [학습계획](#2)
- [Git GUI 프로그램 추천](#3)
- [깃 세팅 시 권장항목](#4)
- [기본적인 명령이](#5)

<br>

<a name="1"></a>
# 학습 레퍼런스 링크

- [Git 명령어 정리](https://velog.io/@taeha7b/git-command)
- [소스 코드 관리를 위한 Git 사용법 총 정리](https://www.lainyzine.com/ko/article/summary-of-how-to-use-git-for-source-code-management/)
- [Git Tutorial for Beginners: Learn Git in 1 Hour](https://youtu.be/8JJ101D3knE)
- [GitHub GitHub 정리하기](https://velog.io/@rssungjae/GitHub-GitHub-%EC%A0%95%EB%A6%AC%ED%95%98%EA%B8%B0)
- [git 깃허브 정리](https://velog.io/@dlawjdgk0715/git-%EA%B9%83%ED%97%88%EB%B8%8C-%EC%A0%95%EB%A6%AC)
- [Commit message 작성 규칙](https://velog.io/@djh20/Git-%EC%A0%9C%EB%8C%80%EB%A1%9C-%EC%82%AC%EC%9A%A9%ED%95%B4%EB%B3%B4%EC%9E%90)
- [Github, Git Commit Rule (깃허브 커밋 룰)](https://underflow101.tistory.com/31)
- [업데이트 | 가장 위험한 깃 실수 6가지와 빠른 수습 방법](https://www.itworld.co.kr/news/142318)
- [\[Git\] git stash 명령어 사용하기
](https://gmlwjd9405.github.io/2018/05/18/git-stash.html)
- [Git - fast-forward merge 란? fast-forward & 3-way Merge의 차이점](https://coding-start.tistory.com/333)
- [[GIT] 병합(merge) 종류 별 완벽 설명
](https://minemanemo.tistory.com/46)
- [브랜치 통합하기](https://backlog.com/git-tutorial/kr/stepup/stepup1_4.html)
- [Git 브랜치 - Rebase 하기](https://git-scm.com/book/ko/v2/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98-Rebase-%ED%95%98%EA%B8%B0)
- [깃(Git) 커밋 가이드](https://tech.10000lab.xyz/git/git-commit-discipline.html)

<br>
<a name="3"></a>

# Git GUI 프로그램 추천
- [Github Desktop](https://desktop.github.com/)
- [Source Tree](https://www.sourcetreeapp.com/)
- [GitKraken](https://www.gitkraken.com/)

<br>

<a name="4"></a>
# Git 설치후 세팅
## Git config 설정
- `git config` 명령어를 통해 계정정보를 설정합니다.
```bash
$ git config --global user.name "name"
$ git config --global user.email "name@domain.com"
```


<br>

## OS간 충돌방지
### [설명 링크](https://www.lesstif.com/gitbook/git-crlf-20776404.html)


### 윈도우
```bash
$ git config --global core.autocrlf true
```
### Mac & Linux
```bash
$ git config --global core.autocrlf input
```

### 가독성 좋은 GIt 터미널 세팅
```bash
Mac : Zsh with Git plugin
Windows: posh-git
Windows: windows terminal(beta)
```

### Git 에디터 설정 (VScode)
```bash
# code --wait 입력 시 git파일이 닫힐때 까지 git 터미널이 대기상태
$ git config --global core.editor "code --wait" 
```

<br>
<a name="5"></a>

# 명령어
## Staging Files
## Add 커맨드
```bash
$ git add file1.txt # 단일 추가
$ git add file1.txt file2.txt  # 복수 추가
$ git add *txt  # 패턴매치 추가
$ git .  # 현 경로에 있는 모든항목 추가 (재귀적 탐색포함)
$ git add . -f # ignore파일 및 삭제파일 이력 커밋한 경우
```
<br>

## Status 확인
```bash
$ git status # 현재 staging 된 항목과 현재 레포지터리에 있는 파일비교
```
<br>

## Commit 하기
```bash
$ git commit -m "메모" 
$ git commit # 메모없이 진행 할 경우 COMMIT_EDITMSG파일에 저장된 default 메시지 값으로 커밋 메시지 반영

# Skipping Staging Area and commit
$ git commit -a -m "메모" # commit all modified files    
```

<br>

## Renaming and moving Files
```bash
$ git mv filename.txt newfilename.txt
```

<br>

## View GIt log
```bash
$ git log
$ git log --oneline # 요약본
$ git log --stat # 파일 변동사항 확인
$ git --stat # 각 커밋의 자세한 내역확인
$ git --oneline --patch # 각 파일의 변경내역 확인
```
<br>

## View GIt log with filtering
```bash
$ git log --oneline -3 # 마지막 3개 커밋내역 확인

$ git log --oneline --author="이름" # 커밋 생성자 이름으로 확인
$ git log --oneline --before="2021-12-31" # 날짜 기준으로 조회
$ git log --oneline --after="2021-12-31" # 날짜 기준으로 조회
$ git log --oneline --after="yesterday" # 어제 이후 커밋조회
$ git log --oneline --after="one week ago"
$ git log --oneline --after="one month ago"

# 커밋 메시지 기준으로 조회
$ git log --oneline --grep="커밋 메시지"
$ git log --oneline --grep="커밋 메시지"

# 변경된 코드기준으로 조회
$ git log --oneline -S"코드"
# 변경된 코드기준으로 커밋된 파일내역 확인
$ git log --oneline -S"코드" --Patch 

# 범위기준으로 조회
$ git log --oneline [commit해쉬1]..[commit해쉬2]

# 파일변경기준으로 조회
$ git log --oneline -- "파일이름"
$ git log --oneline --patch -- "파일이름" # 패치내역까지 조회
```
<br>

## Git Diff
```bash
$ git diff # 현재 수정중인 파일과 commit된 파일비교
$ git diff --staged # add된 파일과 commit된 파일비교
$ git diff [commit해쉬1]..[commit해쉬2] # commit간의 비교
$ git diff HEAD HEAD^ # 가장 최근의 커밋과 그 전의 커밋을 비교

# Current branch, diff between commits 2 and 3 times back
$ git diff HEAD~3 HEAD~2
```
<br>

# Branch
```bash
# Create new branch
$ git branch [브랜치명]

# list branches
$ git branch

# 현재 활성화된 git branch 확인
$ git status
>>> on branch master

# branch 이동 (2가지 방법)
# Switch branches
$ git checkout [브랜치명] 

# Switch branches or restore working tree files
$ git switch [브랜치명]

# Restore working tree files
$ git restore [브랜치명] 

# Create new branch and move to the branch
$ git switch -C [브랜치명]
$ git checkout -b [브랜치명]

# rename branch
$ git branch -m [old name] [new name]

# delete branch
# merge가 된것들만 한하여 삭제
$ git branch -d [브랜치명]

# delete branch by Force
$ git branch -D [브랜치명]

# comparing branch
# show all the log commits in the branch that are not in master branch
$ git log master..[브랜치명]

# show all difference between two branch
$ git diff master..[브랜치명]
$ git diff [브랜치명] # master.. 생략해도 자동으로 마스터 브랜치랑 비교

# 변경된 파일만 확인 시
$ git diff --name-status [브랜치명]
```

<br>

## Stashing
Stroing in safe place but doens't record in history
```bash
$ git stash push -m "메시지"

# stash push all
$ git stash push -am "메시지"

# list satsh
$ git stash list

# show stash change
$ git stash show [인덱스 숫자]

# drop stash
$ git stash drop [인덱스 숫자]

# drop all stash
$ git stash clear
```
<br>

# Merging

#### merge 하기전에 그래프로 확인할떄 도움되는 명령어
```bash
$ git slog --oneline --all --graph
```

## Fast-forward merge
```bash
## --ff 는 기본설정이다
$ git merge [브랜치명]
```

## No Fast-forward merge
```bash
# fast-forward의 관계라도 merge commit 실행
$ git switch master
$ git merge --no--ff [브랜치명]
```
<br>


# Push

```bash
# 기본값 경로: origin/master
$ git push [브랜치명]
$ git push -f # 강제로 푸쉬하기 # 절대로 쓰지 말자
```

<br>


# Fetch

```bash
$ git fetch
```

<br>


# Pull

```bash
$ git pull
$ git merge origin/master
```
<br>