# Git add와 commit 완벽 가이드

## 🎯 Git의 3단계 영역

Git은 **3개의 영역**으로 나뉘어져 있습니다:

```
Working Directory → Staging Area → Repository
   (작업 디렉토리)     (스테이징 영역)    (저장소)
        |                 |              |
    파일 수정           git add         git commit
```

### 1. Working Directory (작업 디렉토리)
- 실제 파일들이 있는 폴더
- 파일을 생성, 수정, 삭제하는 공간

### 2. Staging Area (스테이징 영역)  
- 커밋할 준비가 된 파일들이 대기하는 공간
- **"무대 위에 올라간"** 상태

### 3. Repository (저장소)
- 실제로 저장된 커밋들이 있는 공간
- Git 히스토리가 기록되는 곳

---

## 📤 git add - 스테이징하기

### 기본 개념
**git add는 "커밋할 파일을 무대 위에 올리는" 작업**

```bash
# 파일 상태 확인
git status

# 파일을 스테이징 영역에 추가
git add filename.txt
```

### git add의 다양한 사용법

#### 1. 특정 파일 추가
```bash
git add index.html
git add src/app.js
git add README.md
```

#### 2. 여러 파일 동시 추가
```bash
git add index.html style.css script.js
```

#### 3. 모든 파일 추가 (가장 많이 사용)
```bash
git add .
# 현재 디렉토리의 모든 변경사항을 스테이징
```

#### 4. 특정 확장자만 추가
```bash
git add *.js      # 모든 JavaScript 파일
git add *.md      # 모든 마크다운 파일
```

#### 5. 폴더별 추가
```bash
git add src/      # src 폴더의 모든 파일
git add docs/     # docs 폴더의 모든 파일
```

#### 6. 대화형 추가 (고급)
```bash
git add -p        # 각 변경사항을 하나씩 확인하며 추가
git add -i        # 대화형 모드로 추가
```

### 스테이징 상태 확인
```bash
# 현재 상태 확인
git status

# 스테이징된 변경사항 미리보기
git diff --staged
```

---

## 💾 git commit - 저장하기

### 기본 개념
**git commit은 "스테이징된 변경사항을 저장소에 영구 기록하는" 작업**

```bash
# 기본 커밋 (에디터가 열림)
git commit

# 메시지와 함께 커밋 (가장 일반적)
git commit -m "커밋 메시지"
```

### git commit의 다양한 사용법

#### 1. 기본 커밋
```bash
git commit -m "Add login feature"
```

#### 2. 상세한 커밋 메시지
```bash
git commit -m "Add user authentication

- Implement login/logout functionality
- Add password validation
- Update user interface for auth forms"
```

#### 3. add + commit 동시에 (추적 중인 파일만)
```bash
git commit -am "Fix bug in navigation"
# git add . && git commit -m "..." 와 동일 (새 파일 제외)
```

#### 4. 마지막 커밋 수정
```bash
git commit --amend -m "새로운 메시지로 변경"
```

#### 5. 빈 커밋 (테스트용)
```bash
git commit --allow-empty -m "Trigger CI build"
```

### 💬 커밋 타이밍
- Git의 커밋은 단순 저장이 아니라 **작업 단위 스냅샷**
- 현업에서는 보통 이런 단위로 커밋함:
  - **기능 하나 구현 완료**
  - **버그 하나 수정**
  - **리팩터링 단위**
- 따라서 “**작업이 끝난 시점**”에 커밋하는 게 일반적

👉 만약 단순 저장용으로 자주 커밋한다면, reset/revert의 의미가 체감되기 어려움


---

## 🔄 실제 워크플로우

### 일반적인 작업 과정
```bash
# 1. 현재 상태 확인
git status

# 2. 파일 수정 작업
# (VS Code 등에서 파일 편집)

# 3. 변경사항 확인
git status
git diff

# 4. 스테이징
git add .

# 5. 스테이징된 내용 확인
git status

# 6. 커밋
git commit -m "Add new feature"

# 7. 결과 확인
git log --oneline
```

### 상태별 파일 표시

```bash
git status
```
출력 예시:
```
On branch main
Changes to be committed:          # 스테이징된 파일들 (녹색)
  new file:   index.html
  modified:   style.css

Changes not staged for commit:    # 수정했지만 스테이징 안된 파일들 (빨간색)
  modified:   script.js

Untracked files:                  # 새 파일 (빨간색)
  config.json
```

---

## 🎨 커밋 메시지 작성법

### 좋은 커밋 메시지 구조
```
타입: 간단한 설명 (50자 이내)

상세한 설명 (선택사항)
- 왜 이 변경이 필요한지
- 무엇을 변경했는지
- 어떤 영향이 있는지
```

### 커밋 타입 예시
```bash
git commit -m "feat: add user login functionality"
git commit -m "fix: resolve navigation bug on mobile"  
git commit -m "docs: update README with installation guide"
git commit -m "style: fix code formatting"
git commit -m "refactor: reorganize user service functions"
```

### 좋은 커밋 메시지 예시
```bash
# ✅ 좋은 예시
git commit -m "fix: resolve login button not responding on mobile"
git commit -m "feat: add dark mode toggle to header"
git commit -m "docs: add API documentation for user endpoints"

# ❌ 나쁜 예시  
git commit -m "수정"
git commit -m "bug fix"
git commit -m "asdfasdf"
git commit -m "work in progress"
```

---

## ⚡ 자주 사용하는 패턴

### 패턴 1: 빠른 커밋
```bash
git add . && git commit -m "Quick fix for navbar issue"
```

### 패턴 2: 선별적 커밋
```bash
# 특정 파일만 커밋하고 싶을 때
git add src/components/Header.js
git add src/styles/header.css
git commit -m "Update header component styling"
```

### 패턴 3: 부분 커밋 (고급)
```bash
# 한 파일 내의 일부 변경사항만 커밋
git add -p filename.js
git commit -m "Implement error handling in user service"
```

---

## 🔧 유용한 명령어

### 스테이징 취소
```bash
# 모든 파일 스테이징 취소
git reset HEAD

# 특정 파일 스테이징 취소
git reset HEAD filename.txt
```

### 변경사항 확인
```bash
# 작업 디렉토리의 변경사항
git diff

# 스테이징된 변경사항
git diff --staged

# 마지막 커밋과 비교
git diff HEAD
```

### 커밋 히스토리 확인
```bash
# 간단한 로그
git log --oneline

# 그래프로 보기
git log --oneline --graph

# 최근 5개 커밋
git log --oneline -5
```

---

## 🚨 주의사항

### 1. 커밋하면 안 되는 파일들
```bash
# .gitignore에 추가해야 할 파일들
node_modules/     # 의존성 폴더
.env             # 환경변수 파일  
*.log            # 로그 파일
dist/            # 빌드 결과
.DS_Store        # Mac 시스템 파일
```

### 2. 커밋 크기
- **작은 단위로 자주 커밋**하는 것이 좋음
- 한 번에 너무 많은 변경사항을 커밋하지 말 것
- 기능별, 수정별로 나누어 커밋

### 3. 커밋 메시지
- **명확하고 간결하게** 작성
- **영어 또는 한국어 일관성** 유지
- **현재형**으로 작성 ("Add" not "Added")

---

## 💡 실무 팁

### 1. 별칭 설정으로 빠른 작업
```bash
# ~/.zshrc에 추가
alias ga='git add'
alias gaa='git add .'
alias gc='git commit'
alias gcm='git commit -m'
alias gs='git status'
```

### 2. 작업 전 항상 상태 확인
```bash
gs    # git status 확인 습관화
```

### 3. 커밋 전 검토 습관
```bash
git diff --staged    # 커밋될 내용 미리 확인
```

---

## 🎯 핵심 정리

1. **git add**: 변경사항을 스테이징 영역으로 이동
2. **git commit**: 스테이징된 변경사항을 저장소에 기록  
3. **작은 단위로 자주 커밋**하는 것이 좋음
4. **의미있는 커밋 메시지** 작성하기
5. **커밋 전에는 항상 git status로 확인**하기

이제 `git add`와 `git commit`을 자신있게 사용할 수 있습니다! 🚀
