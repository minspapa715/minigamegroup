# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

순수 HTML/CSS/JS로 구현된 정적 5가지 미니 게임 모음 웹앱. 빌드 도구, 패키지 매니저, 프레임워크 없음.

- **홈페이지**: `index.html` — 게임 선택 카드 UI
- **게임 파일**: `minesweeper.html`, `snake.html`, `2048.html`, `breakout.html`, `memory.html`
- **배포**: GitHub Pages → `https://minspapa715.github.io/minigamegroup/`

## 실행 방법

별도 서버 불필요. 파일을 브라우저에서 직접 열면 됨:

```
start index.html          # Windows
```

또는 VS Code Live Server 확장으로 실행.

## Git / 배포

파일 수정 시 `.claude/settings.json`의 PostToolUse 훅이 자동으로 `git add → commit → push`를 실행함. GitHub Pages가 push 감지 후 자동 재배포.

수동 커밋이 필요한 경우:
```
git add <file>
git commit -m "메시지"
git push
```

## 코드 구조 규칙

각 게임은 단일 HTML 파일로 완결됨 (CSS·JS 인라인 포함). 공통 패턴:

- **다크 테임**: `#1a1a2e` 배경, 게임별 accent 색상 (지뢰찾기 `#e94560`, 뱀 `#55efc4`, 2048 `#fdcb6e`, 벽돌깨기 `#74b9ff`, 카드 `#a29bfe`)
- **홈 버튼**: 모든 게임 페이지 좌상단 `← 홈` 링크 (`index.html`로 연결)
- **캔버스 게임** (뱀, 벽돌깨기): `requestAnimationFrame` 기반 게임 루프
- **DOM 게임** (2048, 기억력, 지뢰찾기): 상태 변경 시 전체 또는 부분 리렌더링

새 게임 추가 시: 단일 HTML 파일 생성 → `index.html` 카드 목록에 추가.
