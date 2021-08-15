---
layout: post
title: "[git] 자주 사용하는 git command 정리"
---

```bash
git init # 현재 디렉토리를 git이 관리하는 프로젝트 디렉토리로 설정하고 그 안에 레포지토리(.git 디렉토리) 생성
git config user.name 'username' # 현재 사용자의 아이디를 'username'으로 설정 - 커밋 ㅅ ㅣ필요
git config user.email 'teacher@gmail.com' # 사용자의 이메일 주소 설정 - 커밋 시 필요
git add [파일이름] # 수정사항이 있는 파일을 staging area에 올리기
git add [디렉토리명] # directory 내 수정사항이 있는 모든 파일들을 staging area에 올림
git reset [파일이름] #stating aread에 올린 파일 다시 내리기
git commit -m "커밋 메세지" #현재 staging area에 있는 것들 커밋으로 남기기
git status # git이 현재 인식하고 있는 프로젝트 관련 내용들 출력
git push -u origin master # 로컬 레포지토리의 내용을 처음으로 리모트 레포지토리로 올릴 때
git push
git pull # 리모트 레포지토리의 내용을 로컬 레포지토리로 옮길 때
git fetch # merge하지 않고 pull만 해옴 - 리모트 레포지토리의 내용을 확인한 뒤 로컬 레포지토리로 옮기고 싶을 때.
git clone [프로젝트의 github주소] # github에 올라가있는 오픈 소스 프로젝트를 내 컴퓨터로 가져오기
```

#### 커밋 다루기

```bash
git log # 커밋 히스토리 출력
git log --pretty=oneline # 커밋 히스토리를 한 줄씩 보기좋게 출력
git show [커밋 아이디] # 특정 커밋에서 어떤 변경사항이 있었는지 확인
git commit --amend # 최신 커밋을 수정해서 새로운 커밋으로 만듦
git config alias.[별명] [커맨드] # 길이가 긴 커맨드에 별명 붙여서, 별명으로 해당 커맨드 실행가능하도록 함
git diff [커밋A 아이디] [커밋B 아이디] # 두 커밋 차이 비교
git reset [옵션] [커밋 아이디] # 옵션 생략하면 --mixed 옵션 적용됨
# --soft : HEAD가 특정 커밋을 가리키도록
# --mixed : staging area까지 특정 커밋처럼 리셋
# --hard : working directroy까지 특정 커밋처럼 리셋
# 커밋 아이디 대신 HEAD^, HEAD~3을 사용해도 된다
git tag [태그이름] [커밋 아이디] # 특정 커밋에 태그 붙임
```

HEAD: 어떤 커밋을 가리킴. HEAD가 가리키는 커밋의 내용대로 working directory 구성됨.

git의 세 가지 작업영역 : working directory, staging area, repository

#### 브랜치 사용하기

```bash
git branch [새 브랜치 이름] # 브랜치 생성
git checkout -b [새 브랜치 이름] # 브랜치 생성하면서 이동
git checkout [브랜치 이름] # 그 브랜치로 이동
git branch -d [브랜치 이름] # 브랜치 삭제
git merge --abort # 머지 시도 이전의 상태로 돌아가기
```

#### git reset과 git checkout

- git reset : HEAD가 가리키던 브랜치가 다른 커밋을 가리키도록 한다. HEAD도 결국 간접적으로 다른 커밋을 가리키게 되는 효과가 생긴다.
- git checkout : HEAD 자체가 다른 커밋이나 브랜치를 가리키도록 한다.
