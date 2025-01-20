- [CLI - Command Line Interface](#cli---command-line-interface)
  * [기초 문법](#-----)
  * [경로](#--)
- [Git](#git)
  * [분산 버전 관리 시스템](#------------)
  * [Git의 3가지 영역](#git--3-----)
    + [1. Working Directory](#1-working-directory)
    + [2. Staging Area](#2-staging-area)
    + [3. Repository](#3-repository)
  * [Git의 동작](#git----)
  * [Vim 에디터 사용](#vim-------)
- [Remote Repository](#remote-repository)
  * [원격 저장소](#------)
  * [README.md 파일](#-readmemd--http---readmemd----)
 - [Revert & Reset](#revert---reset)
  * [Revert](#revert)
  * [Reset](#reset)
- [API](#api)
  * [Interface](#interface)
  * [API(Application Programming Interface)](#api-application-programming-interface-)
  * [Chat GPT API 활용](#chat-gpt-api---)

# CLI - Command Line Interface

- GUI - Graphic Use Interface 와 대비되는 개념
- 왜 CLI를 사용해야 할까?
    - **효율성: 메모리와 CPU 사용량이 적어 효율적으로 동작**
    - 정밀한 제어: 특정 프로그램이나 시스템의 세부 설정 정밀 제어
    - 표준성: 대부분의 Unix 운영체제 기반 시스템에서 동일하게 작동

- VS코드는 단순한 텍스트 에디터
    - 강력한 커뮤니티와 익스텐션을 사용할 수 있도록 통합했을 뿐

## 기초 문법

- **.** 현재 디렉토리 / **..** 상위 디렉토리(부모 폴더)
- `touch` 파일 생성
- `mkdir` 새 디렉토리 생성
- `ls` 현재 작업 중인 디렉토리 내부의 폴더/파일 목록 출력
- `cd` 현재 작업 중인 디렉토리를 변경 (위치 이동)
- `start` 폴더/파일을 열기 (Mac은 `open` )
- `rm` 파일 삭제 (디렉토리 삭제는 `rm -r`)

## 경로

- CLI에서 가장 중요한 것 - 내가 어디 있는지(경로) 알아야 한다
    - GUI와 같이 직관적으로 경로와 폴더/파일 목록 확인을 할 수 없음
    - **ls** 명령어를 습관적으로 사용
- 절대 경로
    - Root 디렉토리부터 목적 지점까지 거치는 모든 경로
    - C:/Users/ssafy/Desktop
- 상대 경로
    - 현재 작업하고 있는 디렉토리 기준 상대적 위치
    - 현재 위치가 C:/Users라면, 바탕 화면 상대 경로는 ssafy/Desktop

# Git

## 분산 버전 관리 시스템

- 버전 관리
    - 변화를 기록하고 추적하는 시스템
    - 마지막 파일과, 이전 변경사항만 남기기
- 분산식
    - 버전을 여러 개의 복제된 저장소에 저장 및 관리
    - 분산 구조에서의 장점
        - 중앙 서버의 장애나 손실에 대비하여 백업과 복구가 용이
        - 중앙 서버에 의존하지 않고 동시에 다양한 작업을 수행
            - 개발자들 간 작업 충돌을 줄이고 생산성 향상
        - 오프라인 환경에서도 작업 가능
            - 로컬 저장소에 기록하고 나중에 중앙 서버와 동기화
- 역할
    - 코드의 버전(히스토리) 관리
    - 개발되어 온 과정 파악
    - 이전 버전과의 변경 사항 비교

## Git의 3가지 영역

### 1. Working Directory

- 실제 작업 중인 파일들이 위치하는 영역

### 2. Staging Area

- WD에서 변경된 파일 중, 다음 버전에 포함시킬 파일들을 선택적으로 추가하거나 제외할 수 있는 중간 준비 영역
- 파일의 commit 여부를 명확히 구분
- 변경 사항을 검토하고 선택적으로 관리 가능하며, commit 메세지와 변경 사항을 그룹화하고 단계적으로 commit 할 수 있음

### 3. Repository

- 버전 이력과 파일들이 영구적으로 저장. 모든 버전과 변경 이력 기록
- **Commit** -  변경된 파일들을 저장하는 행위. ‘Snapshot’.

## Git의 동작

- `git init`
    - 로컬 저장소 설정(초기화)
    - git 버전 관리 시작할 디렉토리에서 진행
    - 해당 디렉토리 뒤에 `(master)` 표시가 뜨고, `ls -a` 로 **.git** 디렉토리가 생성됐음을 확인 가능
- `git add`
    - 변경 사항이 있는 파일을 staging area에 추가
- `git commit`
    - Staging area에 있는 파일들을 저장소에 기록
    - 해당 시점의 버전을 생성하고 변경 이력을 남기는 것 (commit)
    - Commit 생성을 위해서는 작성자 정보가 필요
        
        `git config --global [user.email](http://user.email) '--@--'` 
        
        `git config --global [user.name](http://user.name) '---'` 
        
        git global 설정 정보는 `git config --global -l` 로 확인
        
    - Commit의 이름이 필요
        
        `git commit -m '---'` 
        
        입력하지 않을 경우 Vim 에디터로 진입하여 정보를 입력해야 함
        
- `git log`
    - Commit 목록 확인
    - 간략히 보고 싶으면 `git log --oneline`
- `git status`
    - 로컬 저장소의 파일 상태 확인
    - 변경된 사항, staging area 추가 여부, commit 여부 등
- Git은 로컬 저장소 내 모든 파일의 변경사항을 감시하고 있음
- **Git 로컬 저장소 내 또다른 git 로컬 저장소를 만들지 말 것**
    - 이 경우 바깥의 git이 안쪽의 git 변경 사항을 추적 불가능
    - **.git/** 삭제를 통해 취소할 수 있음(`rm -r .git` )

- `git commit --amend`
    - 바로 직전 생성한 commit 수정
    - Vim 에디터가 열리면서 직전 commit 메시지 수정
    - Commit 메시지 수정할 경우 commit 해시 값도 변경
    - Staging area에 새로운 변경을 추가했을 경우, Vim 에디터에서 새로운 commit 정보 확인 및 수정 가능
    - **불필요한 commit 생성하지 않고 직전 commit 수정**

## Vim 에디터 사용

- **insert** 키 눌러서 텍스트 편집
- **Esc** 키로 편집 모드 종료
- **Shift+;** 키 입력 후,
    - q - 종료
    - q! - 강제 종료
    - **wq - 저장 후 종료**
    - wq! - 강제 저장 후 종료

# Remote Repository

## 원격 저장소

- 코드와 버전 관리 이력을 온라인 상의 특정 위치에 저장하여 여러 개발자가 협업하고 코드 공유 가능
- GitLab, GitHub, Bitbucket, etc.
- `git remote add origin remote_repo_url`
    - ‘origin’은 추가하는 원격 저장소 별칭. 로컬 저장소 하나에 여러 원격 저장소 추가 가능.
- `git remote -v`
    - 등록된 원격 저장소 목록 확인
- `git push origin master`
    - origin이라는 원격 저장소에 commit 목록 업로드(master라는 이름의 브랜치를 push)
    - commit이 올라가는 것. commit 이력이 있어야 push 가능
- `git pull origin master`
    - 원격 저장소의 변경 사항만을 받아옴 (업데이트)
- `git clone remote_repo_url`
    - 원격 저장소 전체를 복제 (다운로드)
    - 이렇게 받은 경우 이미 `git init` 이 되어 있음
- **gitignore**
    - Git에서 특정 파일이나 디렉토리를 추적하지 않도록 설정하는 데 사용하는 텍스트 파일
    - **.gitignore** 파일 생성(확장자 없음)
    - 파일 생성 후 **.gitignore** 에 해당 파일 이름 작성하면 추적되지 않음
    - **단, 이미 git 관리 이력이 있는 파일이나 디렉토리는 나중에 작성해도 적용되지 않음**
        - `git rm --cached` 로 git 캐시에서 삭제 필요
    - https://www.toptal.com/developers/gitignore/ 에서 gitignore 목록 작성 가능
- `git remote rm`
    - 현재 로컬 저장소에 등록된 원격 저장소 삭제

## README.md 파일

- 저장소 최상단에 위치해야 원격 저장소에서 올바르게 출력
- 하나만 존재할 필요는 없음. 각 디렉토리 내 여러 개 존재 가능.

# Revert & Reset

## Revert

- `git revert <commit id>`
    - 공백을 사용해 여러 commit 동시 처리 가능
    - `..` 사용해 범위 지정하여 여러 개 동시 처리 가능
    - `--no-edit`  commit 메시지 작성 위한 편집기 열지 않고 자동으로 진행
    - `--no-commit`  자동으로 commit 하지 않고 Staging Area에만 올림(이후 직접 commit). 이를 통해 여러 commit을 하나의 commit으로 묶어서 revert 할 수 있
- “재설정”
- 단일 commit을 실행 취소 하는 것
- 프로젝트 기록에서 commit을 없었던 일로 처리 후 그 결과를 새로운 commit으로 추가
- 즉 기록에서 commit이 사라지지는 않음
- 변경 사항을 안전하게 실행 취소할 수 있도록 도와주는 **순방향 실행 취소 작업**
- 기록이 손실되는 것을 방지하며 기록의 무결성과 협업의 신뢰성을 높임

## Reset

- `git reset [옵션] <commit id>`
- “되돌리기”
- 특정 commit으로 되돌아 간 뒤, 그 이후의 commit은 모두 삭제
- 삭제되는 commit들의 기록을 남겨둘 것인지 옵션을 통해 조정
    - `--soft` - staging area에 남김
    - `--mixed` - working directory에 남김(기본 옵션 값)
    - `--hard` - 기록을 남기지 않음

# API

## Interface

- 서로 다른 두 개의 시스템(기기, 소프트웨어)이 정보 교환 시 그 사이 존재하는 접점
- 기계와 기계, 시스템과 시스템 사이에서도 수많은 Interface를 통해 약속된 방식으로 데이터를 주고 받음
- Client - 서비스를 요청하는 쪽
- Server - 요청을 받아서 처리하고, 결과를 응답해주는 쪽

## API(Application Programming Interface)

- 두 소프트웨어(도는 시스템)가 서로 통신할 수 있게 하는 메커니즘
- 약속된 방식의 인터페이스. 특정 규칙에 따라 데이터를 요청하고 응답하는 규칙 제공
- Application - 특정 기능을 수행하는 모든 소프트웨어
- 소셜 로그인, 날씨 앱 등
- API Key
    - API에게 요청을 보내는 앱을 구별하기 위한 고유한 식별 문자열
    - 보안 강화, 데이터 관리

## Chat GPT API 활용

- 챗봇 프로그램을 만들 수 있음
    1. OpenAI 클라이언트를 초기화하고 API 키로 인증
    2. 대화의 기본 지침(system)과 사용자 질문(user)을 conversation_history에 추가
    3. OpenAI API에 conversation_history를 전달하여 응답 생성
    4. 생성된 응답 출
- 프롬프트 엔지니어링과 다양한 파라미터 조정을 통해 목적에 맞게 활용할 수 있음
