# Learn Git
## 주요 단어

- Working directory : 작업 디렉토리
- Staging area : Local repository로 올리기 전에 이번 커밋과 관련된 파일들을 관리하는 것
- Local repository : Remote repository로 Push하기 전에 관리하는 곳

## 명령어

- git init : 해당 Working directory을 깃에 등록함
- git add : Working directory의 변경사항을 Staging area에 등록
- git commit : Staging area의 사항들을 Local repository에 등록
- git push : Local repository의 사항들을 Remote repository에 등록
- git clone : Remote repository를 Working directory로 복사하면서 remote로 등록
- git pull : git fetch + git merge, Push한 이후의 변경내용을 가져옴
- git fetch : Remote repository를 Local repository로 가져옴
- git merge : Local repository를 Working directory로 가져옴

자동으로 병합되지 않는 conflict시에는 merge 또는 rebase를 사용할 것


git config --global --edit

서버의 중요한 특징
- 가용성 : 연중무휴로 사용가능
- 내구성 : 저장된 데이터가 사라지면 안 된다

내구성이 더 중요하며, 가용성은 서비스의 특징에 따라 다르다

프로젝트별로 git 세팅을 바꿀 수도 있음
git config --edit
git config user.name / git config user.email

커밋 메시지 첫 글자는 대문자, 첫 단어는 동사 현재형으로 할 것

git status
working directory와 staging area간 차이와 staging area에 올려놓은 파일들을 보여준다

git clean
local 저장소와 작업 디렉토리를 일치시킴

로컬 저장소는 커밋의 집합

git remote add origin https://Eclatant@github.com/Eclatant/TestRepository.git
잘못 설정했다면 git config --edit
cat .git/config 로도 확인가능

git push --set-upstream origin master

git reset --hard HEAD

git clone
임의의 디렉토리 만들고 로컬 저장소로 가져오고, 워킹 디렉토리에 최신내용 반영
git clone 명령 맨 뒤에 폴더명을 입력하면 원하는 폴더명으로 가져올 수 있음
git clone abc abcd 라고 하면 로컬 저장소 abc와 작업 디렉토리를 복사해옴

git checkout commit-id file : 해당 file만 커밋시점으로 되돌아감, file이 없으면 전체가 되돌아감

Already up-to-date : 원격 저장소와 로컬 저장소와 작업 디렉토리 모두가 일치함

git commit -am : git add 와 git commit을 합침

Tree와 Graph의 차이는 합쳐지냐 안 합쳐지냐이다

origin/HEAD : 최신
HEAD는 현재 작업 디렉토리

git branch -r : 원격 브랜치 목록
git remote -v : 원격 저장소 이름이 어떤 원격 저장소를 가리키고 있는지 확인가능
git push 원격저장소 브랜치이름 이 기본(생략하면 git push origin master)
git push --set-upstream origin master :  origin/master를 지금 브랜치의 원격저장소로 연결시키겠다

upstream : local에 연결된 원격 저장소

git branch feature : 현재 브랜치를 따와서 feature 브랜치를 생성
Master는 배포용으로 가장 완벽한 브랜치로 유지되어야 한다
서비스 개발시에는 develop브랜치를 따와서 그것에서 다른 기능에 해당하는 branch를 따와서 작업하다가 develop으로 merge해주고 검증 후에 master에 merge해서 배포해준다

checkout을 commit으로 할 수도 있다
checkout : 현재 작업 디렉토리를 바꿔주는 명령
HEAD도 origin/master는 해당 커밋시점을 가리키는 것

git log는 시간 순서대로 표시된다
merge는 head와 합치는 것

git reset 시에 staging area에 올려놓은 것은 날아간다

collaborator 가 없으면 origin/head 가 안 나오는 이유

우리는 과학자가 아닌 엔지니어이다
알려고 고민하는 시간을 1시간 이상 들이지 마세요

git checkout 2e4a153 -b event : 해당 커밋에서 브랜치를 생성하고 체크아웃

새로 클론해오면 마스터와 HEAD만 존재

origin/master 와 origin/head는 항상 기본적으로 같지만 설정에서 변경할 수 있음

git checkout origin/feature-1 -b feature-1 : origin/feature-1 을 feature-1으로 만들어줘

git checkout develop : remote에 develop이 있으면 가져와줘

head 브랜치는 삭제할 수 없어요
삭제하려는 브랜치에만 속해있는 커밋이 있다면 에러가 발생 (다른 곳으로 이전해줘!)
branch -d 옵션일 때만 가능

echo "zzz" >> copy.js
>> 쓰면 파일 밑에 덧붙이는 효과

git branch -D branchname 강제로 브랜치를 삭제

콜 바이 레퍼런스를 말하시려고 했던 이유?

브랜치는 한 커밋을 가리키고 있는 것이고, 그것은 과거 이력을 모두 가지고 있다 (포인터)
깃은 커밋 외에는 모두 허상에 가까움

alias glogs='git log --oneline --graph --decorate --all'
alias glogs='git log --oneline --graph --decorate' 를 일반적으로 더 많이 사용 (내 작업을 보기 위해서)