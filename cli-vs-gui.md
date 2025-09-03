# CLI vs GUI 핵심 정리 (개발자용)

## 🎯 핵심 차이점

| 특성 | CLI | GUI |
|------|-----|-----|
| **속도** | 압도적으로 빠름 | 느림 |
| **자동화** | 쉬움 (스크립트) | 어려움 |
| **정확성** | 명확한 제어 | 제한적 |
| **학습** | 어려움 (명령어 암기) | 쉬움 |

<br>

## ⚡ 개발자가 CLI를 쓰는 이유

### 1. **속도**
```bash
# 한 줄로 끝
git add . && git commit -m "fix" && git push
```

### 2. **자동화**
```bash
# 스크립트로 반복 작업 처리
npm run build && npm test && deploy.sh
```

### 3. **원격 작업**
```bash
# SSH로 서버 접속해서 작업
ssh user@server "git pull && systemctl restart app"
```

### 4. **정확한 제어**
```bash
# GUI에서 불가능한 세밀한 옵션
git log --oneline --since="2 days ago" --author="john"
```

<br>

## 🔥 개발자 필수 CLI 명령어

### Git
```bash
gs    # git status
ga    # git add
gcm   # git commit -m
gp    # git push
gl    # git pull
```

### 파일 작업
```bash
grep -r "TODO" .          # 파일 내용 검색
find . -name "*.js"       # 파일 찾기
ls -la                    # 상세 목록
```

### 시스템
```bash
ps aux | grep node        # 프로세스 확인
kill -9 1234             # 프로세스 종료
df -h                    # 디스크 사용량
```

<br>

## 🎨 GUI가 필요한 때

- **디자인 작업** (Figma, Photoshop)
- **복잡한 시각화** (차트, 그래프)
- **DB 관리** (데이터 브라우징)
- **코드 리뷰** (GitHub 웹)

<br>

## 🚀 실무 권장 비율

**80% CLI + 20% GUI**

- **CLI**: Git, 서버 관리, 빌드/배포, 파일 작업
- **GUI**: 코드 에디터, 디자인, 브라우저, DB 도구

<br>

## 💡 핵심 포인트

1. **CLI는 도구, GUI는 인터페이스**
2. **반복 작업 = CLI 필수**
3. **시각적 작업 = GUI 필요**
4. **개발 효율성 = CLI 마스터**
