# 영주과외 (yeongju-tutoring) — 작업 규칙

경상북도 영주시 지역 타겟 과외 사이트. GitHub Pages 정적 사이트, 빌드 없음.
홈 `~/CLAUDE.md` 규칙을 그대로 따른다 (세션 하나 = 저장소 하나, 시작 때 pull, 끝날 때 commit+push, 작업로그 기록).

## 도메인 / 배포
- 도메인: **아직 없음**. 현재 주소 `https://x26589334-cpu.github.io/yeongju-tutoring/`
- 도메인을 붙일 때: ① `CNAME` 파일 생성 ② 이 파일과 `sitemap.xml`·`robots.txt`·각 페이지 `canonical`/`og:url` 의 주소를 한 번에 교체
  → 교체는 생성기로 한다: `사이트관리/도구/지역과외/regions.js` 의 `siteUrl` 수정 후 재생성
- GA4 측정 ID 미발급. `analytics.js` 의 `GA_ID` 가 비어 있어 지금은 아무것도 보내지 않는다. 발급하면 그 한 줄만 채우고 `사이트관리/사이트대장.md` 10절에 적는다.

## 이 사이트만의 구조
| 파일 | 내용 |
|---|---|
| `index.html` | 홈 (히어로 SVG = temple-roof 모티프) |
| `schools.html` | 영주 초·중·고 39곳 목록 + 검색 |
| `school/*.html` | **학교별 정적 페이지 39개** — SEO 의 핵심. 학교당 국어·영어·수학·사회·과학·코딩 키워드 |
| `teachers.html` | 선생님 (화상 673명 — 영주 방문 선생님이 0명이라 방문 관련 내용은 감춰져 있다) |
| `online.html` | 화상과외 안내 |
| `blog.html` · `blog/*.html` | 데일리 글 |
| `teachers-data.js` | 선생님 데이터 (자동 생성 — 직접 고치지 말 것) |
| `데일리-키워드.md` | 데일리 글 주제 목록 (읍·면·동 × 과목, 학교 × 과목) |

## 절대 손으로 고치지 말 것
이 사이트 전체는 **생성기 출력**이다: `C:\Users\DOJIVERSE\사이트관리\도구\지역과외\`
- 디자인·문구·페이지 구조를 바꾸려면 → 생성기(`regions.js`/`css.js`/`build.js`)를 고치고 다시 생성
- 손으로 고친 뒤 재생성하면 **덮어써진다**
- 예외: `blog/` 안의 글과 `blog.html` 목록, `rss.xml`, `sitemap.xml` 은 재생성 시 **보존**한다 (생성기가 blog 폴더를 건드리지 않음)

## 글 올릴 때
1. `git pull`
2. `blog/<슬러그>.html` 작성 (기존 글 형식 그대로 복사해서 본문만 교체)
3. `tools/새글.js` 실행 → `blog.html`·`rss.xml`·`sitemap.xml` 갱신
4. `git add -A && git commit && git push`
5. `& "$env:USERPROFILE\사이트관리\로그기록.ps1" -Repo yeongju-tutoring -Status 완료 -What "글 N편"`

## 함정
- CSS/JS 를 고쳤으면 HTML 의 `?v=` 를 올린다 (전 사이트 공통 규칙 6). 생성기가 `style.css?v=1`·`app.js?v=1`·`teachers-data.js?v=1` 로 박아 둔다.
- 상담 폼은 **허브 Apps Script 공유**다. `form.js` 의 `SHEET_TAB = "지역과외"` — 오타가 나면 시트에 새 탭이 조용히 생긴다. 탭 이름을 바꾸려면 11개 사이트 전부 같이 바꿔야 한다.
- 학교 이름은 정식 명칭으로 쓴다 (홈 CLAUDE.md 규칙 10). 기존 페이지 주소는 고치지 않는다.
