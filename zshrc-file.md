## 📌 .zshrc 파일

### 1단계: .zshrc 파일 열기

```bash
nano ~/.zshrc
```

### 2단계: .zshrc 아래 코드 추가하기
```bash
export PATH=/opt/homebrew/bin:$PATH

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  #$
export PATH=$PATH:/Applications/Wine.app/Contents/Resources/bin
export PATH=$PATH:/Applications/Wine.app/Contents/Resources/bin
export PATH=$PATH:/Applications/Wine.app/Contents/Resources/bin
export PATH=$PATH:/Applications/Wine.app/Contents/Resources/bin

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
alias gpom='git push origin main'
alias gpull='git pull origin main'
alias ginit='git init && git add . && git commit -m "Initial commit"'
alias gundo='git reset --soft HEAD~1'  # 마지막 커밋 취소
alias gclean='git clean -fd'  # 추적되지 않는 파일 삭제

# Git 브랜치 표시 함수
parse_git_branch() {
    git branch 2> /dev/null | sed -n -e 's/^\* \(.*\)/(\1)/p'
}

# 프롬프트 설정 (컬러 포함)
setopt PROMPT_SUBST
PROMPT='%F{cyan}%n@%m%f %F{blue}%~%f %F{green}$(parse_git_branch)%f %$
```
