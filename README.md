# 모여 (MOYEO) — 모임 중간지점 추천 프로토타입

친구들의 출발지·이동수단을 반영해 가장 공평한 중간지점과 모임 장소를 추천하는
모바일 웹 프로토타입입니다. (순수 HTML / CSS / JavaScript, 빌드 도구 불필요)

## 파일 구조

```
moyeo/
├── index.html         # 메인 홈
├── create.html        # 모임 만들기 (참여자 입력)
├── location.html      # 출발지 입력 방식
├── transport.html     # 이동수단 선택
├── result.html        # 중간지점 순위 (1단계 / ?stage=2 재사용)
├── category.html      # 카테고리 선택 (대·중분류 단일, 소분류 다중)
├── place.html         # 장소 추천 결과 (후보 카드)
├── directions.html    # 길찾기 결과 (최종)
├── css/
│   └── style.css      # 전체 공통 스타일
├── js/
│   └── script.js      # 전체 공통 스크립트 (페이지 이동·선택 로직)
└── README.md
```

## 화면 흐름

```
index → create → location → transport
  → result (1단계, "오늘 뭐하지?")
  → category
  → place (장소 추천 결과, "다음")
  → result?stage=2 ("길찾기 보기")
  → directions (길찾기 결과 · 모임 확정)
```

## VS Code에서 실행하기

빌드나 서버 설정 없이 바로 실행됩니다. 두 가지 방법 중 하나를 사용하세요.

### 방법 1 — Live Server 확장 (권장)
1. VS Code 확장 탭에서 **Live Server** (Ritwick Dey) 설치
2. `moyeo` 폴더를 VS Code로 열기 (`File → Open Folder`)
3. `index.html`을 우클릭 → **Open with Live Server**
4. 브라우저에서 모바일 크기로 보려면 개발자도구(F12) → 기기 툴바(Ctrl/Cmd+Shift+M)

### 방법 2 — 파일 직접 열기
`index.html`을 더블클릭해 브라우저로 열어도 동작합니다.
(`localStorage` 기반 선택값 저장이 일부 브라우저에서 `file://` 보안정책으로 제한될 수 있어
Live Server 사용을 권장합니다.)

## 기술 메모
- 외부 의존성 없음. 폰트(Pretendard)만 CDN에서 로드합니다.
- 페이지 간 데이터 전달은 `localStorage`(선택한 중간지점·장소)로 처리합니다.
- 모든 스타일은 `css/style.css`, 모든 동작은 `js/script.js`에 집중되어 있습니다.
  (HTML 인라인 style/script 미사용)
- 데스크톱에서는 아이폰 프레임으로, 480px 이하에서는 전체 화면 모바일 웹으로 표시됩니다.
