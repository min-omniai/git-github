# Git 설치 및 설정 가이드 (Windows, Mac)

## 📥 Git 설치

### Windows 설치

#### 방법 1: 공식 웹사이트에서 설치
1. [Git 공식 웹사이트](https://git-scm.com/) 접속
2. "Download for Windows" 클릭
3. 다운로드된 설치 파일(.exe) 실행
4. 설치 옵션 선택:
   - **Adjusting your PATH environment**: "Git from the command line and also from 3rd-party software" 선택 (권장)
   - **Choosing the default editor**: Visual Studio Code 또는 원하는 에디터 선택
   - **Configuring the line ending conversions**: "Checkout Windows-style, commit Unix-style line endings" 선택 (권장)
   - **Configuring the terminal emulator**: "Use Windows' default console window" 선택
5. 설치 완료

#### 방법 2: Chocolatey로 설치
```bash
# PowerShell을 관리자 권한으로 실행
choco install git
```

#### 방법 3: winget로 설치 (Windows 10/11)
```bash
# PowerShell에서 실행
winget install --id Git.Git -e --source winget
```

### Mac 설치

#### 방법 1: Homebrew로 설치 (권장)
```bash
# Homebrew 설치 (없는 경우)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Git 설치
brew install git
```

#### 방법 2: 공식 웹사이트에서 설치
1. [Git 공식 웹사이트](https://git-scm.com/) 접속
2. "Download for macOS" 클릭
3. 다운로드된 .dmg 파일 실행
4. 설치 패키지 실행 후 안내에 따라 설치

#### 방법 3: Xcode Command Line Tools로 설치
```bash
# 터미널에서 실행
xcode-select --install
```

<br>

## ⚙️ Git 설정

### 필수 설정

#### 사용자 정보 설정
```bash
# 사용자 이름 설정 (GitHub 사용자명 권장)
git config --global user.name "Your Name"

# 이메일 설정 (GitHub에서 사용하는 이메일)
git config --global user.email "your.email@example.com"
```

#### 기본 브랜치명 설정
```bash
# 기본 브랜치명을 main으로 설정 (GitHub 표준)
git config --global init.defaultBranch main
```

### 추가 설정 (권장)

#### 기본 에디터 설정
```bash
# Visual Studio Code
git config --global core.editor "code --wait"

# Vim
git config --global core.editor "vim"

# Nano
git config --global core.editor "nano"
```

#### Windows에서 줄바꿈 문자 설정
```bash
# Windows
git config --global core.autocrlf true

# Mac/Linux
git config --global core.autocrlf input
```

#### 색상 출력 활성화
```bash
git config --global color.ui auto
```

#### 출력 페이징 설정
```bash
# 짧은 출력도 페이저 사용하지 않기
git config --global pager.branch false
git config --global pager.tag false
```

<br>

## 🔍 설치 확인

### 버전 확인
```bash
git --version
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

## 🔐 SSH 키 설정 (GitHub 연동)

### SSH 키 생성
```bash
# SSH 키 생성 (이메일은 GitHub 이메일로)
ssh-keygen -t ed25519 -C "your.email@example.com"

# Enter 키를 눌러 기본 위치에 저장
# 패스프레이즈는 선택사항 (보안상 권장)
```

### SSH Agent에 키 추가

#### Windows (Git Bash)
```bash
# SSH Agent 시작
eval "$(ssh-agent -s)"

# SSH 키 추가
ssh-add ~/.ssh/id_ed25519
```

#### Mac
```bash
# SSH Agent 시작
eval "$(ssh-agent -s)"

# SSH 키 추가
ssh-add --apple-use-keychain ~/.ssh/id_ed25519
```

### 공개 키를 GitHub에 등록

#### 1. 공개 키 복사
```bash
# Windows (Git Bash)
cat ~/.ssh/id_ed25519.pub | clip

# Mac
pbcopy < ~/.ssh/id_ed25519.pub
```

#### 2. GitHub에서 설정
1. GitHub 로그인 → Settings → SSH and GPG keys
2. "New SSH key" 클릭
3. Title: 컴퓨터 이름 등 식별 가능한 이름
4. Key: 복사한 공개 키 붙여넣기
5. "Add SSH key" 클릭

### SSH 연결 테스트
```bash
ssh -T git@github.com
```

<br>

## 🛠️ 개발 환경별 추가 설정

### Windows 추가 설정

#### Git Bash를 기본 터미널로 설정 (VS Code)
```json
// settings.json
{
    "terminal.integrated.defaultProfile.windows": "Git Bash"
}
```

#### Windows Terminal에서 Git Bash 사용
1. Windows Terminal 설치
2. 설정에서 Git Bash 프로필 추가

### Mac 추가 설정

#### .zshrc에 Git 별칭 추가
**📝 .zshrc 파일 편집**
```bash
### nano 에디터로 열기 (초보자 추천)
nano ~/.zshrc

### 또는 VS Code로 열기
code ~/.zshrc

### 또는 vim으로 열기
vim ~/.zshrc
```

```bash
# ~/.zshrc 파일에 추가

# Git 별칭 설정
alias gs='git status'
alias ga='git add'
alias gaa='git add .'
alias gc='git commit'
alias gcm='git commit -m'
alias gp='git push'
alias gl='git pull'
alias gco='git checkout'
alias gb='git branch'
alias gd='git diff'
alias glog='git log --oneline --graph --decorate --all'
alias gst='git stash'
alias gsp='git stash pop'

# 개인 맞춤 별칭 예시
alias gpom='git push origin main'
alias gpull='git pull origin main'  
alias ginit='git init && git add . && git commit -m "Initial commit"'
alias gundo='git reset --soft HEAD~1'  # 마지막 커밋 취소
alias gclean='git clean -fd'  # 추적되지 않는 파일 삭제
```
### ✅ 설정 확인
```bash
# 별칭이 제대로 설정되었는지 확인
alias | grep git

# 테스트
gs  # git status와 같은 결과가 나와야 함
```

🚀 완료!
이제 Git 명령어를 훨씬 빠르게 입력할 수 있습니다!
예시:
```bash
gs              # 상태 확인
gaa             # 모든 파일 추가
gcm "Update"    # 커밋
gpom            # 메인 브랜치에 푸시
```

<br>

## 🔧 유용한 Git 별칭 설정

```bash
# 상태 확인
git config --global alias.st status

# 짧은 로그
git config --global alias.lg "log --oneline --graph --decorate --all"

# 마지막 커밋 수정
git config --global alias.amend "commit --amend --no-edit"

# 브랜치 목록
git config --global alias.br branch

# 체크아웃
git config --global alias.co checkout

# 되돌리기
git config --global alias.unstage "reset HEAD --"
```

<br>

## ✅ 설치 완료 체크리스트

- [ ] Git 설치 완료
- [ ] `git --version` 명령어로 버전 확인
- [ ] `git config --global user.name` 설정
- [ ] `git config --global user.email` 설정
- [ ] 기본 브랜치명 설정 (`main`)
- [ ] SSH 키 생성 및 GitHub 등록
- [ ] SSH 연결 테스트 성공
- [ ] 에디터 설정 (선택사항)
- [ ] 유용한 별칭 설정 (선택사항)

<br>

## 🚀 다음 단계

설치와 설정이 완료되었다면:

1. **첫 번째 저장소 만들기**: `git init`
2. **GitHub에서 저장소 클론**: `git clone [repository-url]`
3. **기본 Git 워크플로우 학습**: add → commit → push

<br>

## 📚 참고 자료

- [Git 공식 문서](https://git-scm.com/doc)
- [GitHub Docs - Git 설정](https://docs.github.com/en/get-started/quickstart/set-up-git)
- [Pro Git Book](https://git-scm.com/book)

---

💡 **팁**: 설정이 제대로 되었는지 확인하려면 새로운 터미널 창을 열어 테스트해보세요!
