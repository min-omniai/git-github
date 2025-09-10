# 📌 여러 브랜치 (Git Branch)

## 1. 브랜치 만드는 법
```bash
git branch feature/login
```

- 현재 위치한 커밋에서 `feature/login`이라는 새 브랜치를 생성
- 단, HEAD는 여전히 이전 브랜치(main 등)에 머무름

---

## 2. 브랜치를 만들면서 바로 이동하는 법
```bash
git checkout -b feature/login

또는 (Git 2.23 이후 권장)

git switch -c feature/login
```

- 브랜치를 생성하면서 동시에 이동
- `-b` 또는 `-c` 옵션이 "create"를 의미

---

## 3. 브랜치 히스토리 확인
- **SourceTree**  
  - 좌측 브랜치 목록에서 원하는 브랜치 더블클릭 → 체크아웃
  - 중앙 그래프 뷰에서 브랜치가 분기된 모습 시각적으로 확인 가능

- **Cursor (VSCode 기반 Git 그래프)**  
  - Source Control 패널 또는 Git Graph 확장 사용
  - main, feature 등 여러 브랜치가 어디서 갈라졌는지 한눈에 볼 수 있음

---

## 4. 터미널에서 로그 내역 깔끔하게 보기
```bash
git log --all --decorate --oneline --graph
```

- 옵션 설명
  - `--all`: 모든 브랜치 로그 보기
  - `--decorate`: 브랜치/태그 이름 표시
  - `--oneline`: 한 줄 요약 출력
  - `--graph`: 텍스트 기반 브랜치 구조 시각화

---

## ✅ 요약
- `git branch <name>` : 브랜치 생성  
- `git checkout -b <name>` 또는 `git switch -c <name>` : 생성 + 이동  
- SourceTree / Cursor: 그래프 뷰로 분기된 브랜치 확인  
- `git log --all --decorate --oneline --graph` : 터미널에서 브랜치 흐름 확인  
