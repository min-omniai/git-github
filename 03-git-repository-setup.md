# 초기설정 & Git 저장소 생성하기

## 🛠️ Git 초기 설정

### 사용자 정보 설정 (필수)
```bash
# 사용자 이름 설정 (GitHub 사용자명 권장)
git config --global user.name "Your Name"

# 이메일 설정 (GitHub에서 사용하는 이메일)
git config --global user.email "your.email@example.com"
```

### 기본 설정 (권장)
```bash
# 기본 브랜치명을 main으로 설정
git config --global init.defaultBranch main

# 에디터 설정 (VS Code)
git config --global core.editor "code --wait"

# 색상 출력 활성화
git config --global color.ui auto
```

### 설정 확인
```bash
# 전체 설정 보기
git config --list

# 특정 설정 확인
git config user.name
git config user.email
```

<br>

## 📂 Git 저장소 생성하기

### 방법 1: 로컬에서 시작 → GitHub 업로드

#### 1단계: 프로젝트 폴더에서 Git 저장소 초기화
```bash
# 프로젝트 폴더로 이동
cd my-project

# Git 저장소 초기화
git init
```

#### 2단계: .gitignore 파일 생성 (선택사항)
**gitignore 생성** io: https://www.toptal.com/developers/gitignore

```bash
# .gitignore 파일 생성
touch .gitignore

# 내용 예시 (Node.js 프로젝트)
echo "node_modules/" >> .gitignore
echo ".env" >> .gitignore
echo "*.log" >> .gitignore
```

#### 3단계: 첫 번째 커밋
```bash
# 모든 파일 스테이징
git add .

# 첫 번째 커밋
git commit -m "Initial commit"
```

#### 4단계: GitHub에 저장소 생성 후 연결
```bash
# GitHub에서 저장소 생성 후
git remote add origin git@github.com:username/repository-name.git

# 원격 저장소에 푸시
git push -u origin main
```

### 방법 2: GitHub에서 시작 → 로컬로 클론

#### 1단계: GitHub에서 저장소 생성
1. GitHub 로그인 → "New repository" 클릭
2. Repository name 입력
3. "Add a README file" 체크 (권장)
4. "Create repository" 클릭

#### 2단계: 로컬로 클론
```bash
# 원하는 폴더로 이동
cd ~/Documents/projects

# 저장소 클론
git clone git@github.com:username/repository-name.git

# 클론된 폴더로 이동
cd repository-name
```

<br>

## 🔧 저장소 초기화 후 설정

### README.md 생성
```bash
# README.md 파일 생성
echo "# Project Name" > README.md
echo "" >> README.md
echo "프로젝트 설명을 여기에 작성하세요." >> README.md
```

### 브랜치 확인 및 설정
```bash
# 현재 브랜치 확인
git branch

# main 브랜치로 변경 (master인 경우)
git branch -M main
```

### 원격 저장소 연결 확인
```bash
# 원격 저장소 목록 확인
git remote -v

# 연결 테스트
git remote show origin
```

<br>

## 📋 .gitignore 템플릿

### Node.js 프로젝트
```gitignore
# Dependencies
node_modules/
npm-debug.log*
yarn-debug.log*
yarn-error.log*

# Environment variables
.env
.env.local
.env.production

# Build outputs
dist/
build/

# IDE
.vscode/
.idea/
```

### Python 프로젝트
```gitignore
# Byte-compiled / optimized
__pycache__/
*.pyc
*.pyo
*.pyd

# Virtual environment
venv/
env/
.env

# IDE
.vscode/
.idea/
*.swp
*.swo
```

### Java 프로젝트
```gitignore
# Compiled class file
*.class

# Package Files
*.jar
*.war
*.nar
*.ear
*.zip
*.tar.gz
*.rar

# IDE
.idea/
.vscode/
*.iml

# Build
target/
build/
```

<br>

## 🚀 실무 팁

### 1. SSH 키 사용하기
```bash
# HTTPS 대신 SSH 사용 (추천)
git remote set-url origin git@github.com:username/repo.git
```

### 2. 유용한 Git 별칭 설정
```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.cm commit
```

### 3. 초기 커밋 템플릿
```bash
# 의미있는 첫 커밋 메시지
git commit -m "feat: initial project setup with basic structure"
```

<br>

## ✅ 체크리스트

### 설정 완료 확인
- [ ] Git 사용자 정보 설정 완료
- [ ] 기본 브랜치명 main으로 설정
- [ ] SSH 키 GitHub 등록 완료
- [ ] 에디터 설정 완료

### 저장소 생성 확인
- [ ] `git init` 또는 `git clone` 완료
- [ ] README.md 파일 존재
- [ ] .gitignore 파일 생성 (필요한 경우)
- [ ] 첫 번째 커밋 완료
- [ ] 원격 저장소 연결 완료

### 테스트
- [ ] `git status` 정상 작동
- [ ] `git remote -v` 원격 저장소 확인
- [ ] `git push` 정상 작동
- [ ] GitHub에서 저장소 확인 가능

## 🔄 일반적인 워크플로우

```bash
# 1. 저장소 초기화 또는 클론
git init  # 또는 git clone <url>

# 2. 작업 수행
# 파일 생성, 수정, 삭제 등

# 3. 변경사항 확인
git status

# 4. 스테이징
git add .  # 또는 git add <specific-file>

# 5. 커밋
git commit -m "커밋 메시지"

# 6. 원격 저장소에 푸시
git push origin main
```

<br>

## 🚨 주의사항

### 민감한 정보 보호
- **.env 파일**: 환경변수, API 키 등
- **config 파일**: 데이터베이스 연결 정보
- **인증서 파일**: SSL 인증서, 개인키 등

### 대용량 파일 주의
- **이미지, 비디오**: Git LFS 사용 고려
- **빌드 결과물**: .gitignore에 추가
- **의존성 폴더**: node_modules, vendor 등

## 💡 추가 학습 포인트

1. **브랜치 전략** 이해하기
2. **커밋 메시지 컨벤션** 학습
3. **Git 훅(Hook)** 활용하기
4. **GitHub Actions** 자동화 설정

---

이제 Git 저장소를 생성하고 관리할 준비가 완료되었습니다! 🎉
