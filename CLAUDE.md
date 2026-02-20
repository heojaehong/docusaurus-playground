# CLAUDE.md

이 파일은 Claude Code(claude.ai/code)가 이 저장소에서 작업할 때 참고하는 가이드입니다.

## 명령어

```bash
# 개발
yarn start          # 핫 리로드 로컬 개발 서버 실행 (http://localhost:3000)
yarn build          # 정적 사이트를 ./build 디렉터리에 생성
yarn serve          # 빌드된 사이트를 로컬에서 서빙

# 유지보수
yarn clear          # 생성된 파일 및 캐시 삭제 (.docusaurus, build)
yarn swizzle        # 테마 컴포넌트를 꺼내거나 래핑하여 커스터마이징

# 배포
USE_SSH=true yarn deploy         # SSH를 통해 GitHub Pages에 배포
GIT_USER=<username> yarn deploy  # HTTPS를 통해 GitHub Pages에 배포
```

린트 및 테스트 스크립트는 설정되어 있지 않습니다.

## 아키텍처

`preset-classic`(docs + blog + theme 통합 프리셋)을 사용하는 표준 **Docusaurus v3.9.2** 사이트입니다.

**주요 설정 파일:**
- `docusaurus.config.js` — 사이트 메타데이터, 프리셋 설정, 네비게이션/푸터, 코드 하이라이팅
- `sidebars.js` — 사이드바는 `docs/` 디렉터리 구조에서 자동 생성됨

**콘텐츠 디렉터리:**
- `docs/` — MDX 문서 페이지; 사이드바 순서/레이블은 프런트매터 또는 `_category_.json`으로 제어
- `blog/` — 블로그 게시물, `authors.yml`과 `tags.yml`로 메타데이터 관리
- `static/` — 빌드 출력 루트에 그대로 복사되는 정적 파일

**커스텀 React 코드**는 `src/`에 위치:
- `src/pages/` — 커스텀 전체 페이지 (예: 홈페이지 `index.js`)
- `src/components/` — 공유 React 컴포넌트 (CSS Modules로 스코프 스타일링)
- `src/css/custom.css` — Infima 디자인 시스템의 전역 CSS 변수 오버라이드 (주 색상, 다크 모드)

**주목할 설정 플래그:**
- `future.v4: true` — Docusaurus v4 호환 모드 활성화
- `onBrokenLinks: 'throw'` — 끊어진 내부 링크는 빌드를 실패시킴
- `onBrokenAnchors: 'warn'` — 끊어진 앵커는 경고만 출력

## 콘텐츠 추가

- **새 문서 페이지:** `docs/` 아래에 `.md` 또는 `.mdx` 파일 추가. 사이드바는 파일시스템에서 자동 생성됨.
- **사이드바 순서 지정:** 프런트매터의 `sidebar_position` 또는 폴더 내 `_category_.json` 사용.
- **새 블로그 게시물:** `blog/` 아래에 `YYYY-MM-DD-제목.md` 형식으로 파일 추가.
- **커스텀 React 페이지:** `src/pages/` 아래에 `.js`/`.tsx` 또는 `.md` 파일 추가.
