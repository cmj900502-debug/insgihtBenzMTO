# 차민재 | Mercedes-Benz 모터원 고양 — 개인 영업 사이트 v2 (정적 HTML · "showroom editorial")

> v1(`/workspace/benz-site/`)은 백업으로 그대로 두었고, 이 폴더가 새 디자인·새 정보구조의 v2입니다. 데이터(모델·2026년 7월 가격표·프로모션·재고·카드·MOU·리포트·비교북·담당자 정보)는 v1과 같은 원본을 그대로 씁니다.

## 디자인
- 딥 차콜 `#0e0e10` 밴드와 웜 오프화이트 `#f4f2ee` 밴드를 번갈아 배치(`.band` / `.band.light`, 기존 `.section.alt` 도 라이트 밴드).
- 포인트 컬러: 샴페인 `#c9b48a`(어두운 배경) / `#7a6431`(밝은 배경 글자용) — 번호·키커·강조어·현재 메뉴 밑줄에만 사용. 초록은 '즉시출고' 상태 점(6–7px)에만.
- 제목: 세리프(Noto Serif CJK KR Bold를 제목에 쓰인 글자만 잘라 낸 `assets/fonts/serif-kr-sub.woff2`, 약 100KB · 없으면 Noto Serif KR → 나눔명조 → 시스템 serif). 본문: Noto Sans KR.
- 얇은 헤어라인, 작은 모서리(3px), 큰 차량 이미지, 가로 스크롤 캐러셀(`.rail`, scroll-snap), 넓은 여백, 번호 붙은 섹션 머리(01 · 02 …).
- 헤더: 단색 다크 고정 헤더 한 줄 — 로고(좌) · 전체 메뉴 · 상담 신청 버튼(우). 모바일: 로고+상담 신청 아래 가로 스크롤 메뉴 줄 + 전화·카톡 플로팅 버튼.
- 대비: WCAG AA 이상(본문 16.2:1 / 라이트 15.2:1, 보조 글자 7.3:1 / 5.8:1, 라이트 샴페인 5.1:1). `python3 qa/contrast.py` 로 확인.

## 정보 구조 (메뉴)
상단 메뉴 한 줄: **로고(좌) · 홈 · 이달의 포커스 할인 · 차량 찾기 · 전국 재고 · 가격·혜택 · 구매 가이드 · 차민재 팀장 · [상담 신청] 버튼(우)**.
- 헤더는 단색 다크(#0e0e10) · 상단 고정(sticky). 데스크톱(≥1180px) 메뉴 16.5–17px/600, 현재 페이지는 흰색 굵게 + 샴페인 밑줄, 마우스 오버 시 회색 밑줄.
- 모바일/태블릿: 1행 로고 + 상담 신청, 2행 전체 메뉴 가로 스크롤 줄(15px, 햄버거 없음, 현재 메뉴 자동 노출). 하단 탭바는 없애고 오른쪽 아래 전화·카톡 플로팅 버튼(`.fab`)으로 대체.
- 메뉴 정의: `build/site.py` 의 `NAV`, `CTA`.

| 메뉴 | 파일 | 내용 |
|---|---|---|
| 홈 | `index.html` | 풀폭 S-Class 배경 히어로(어두운 그라데이션 + 작은 원형 프로필 88–104px) · '10년의 노하우, 끝까지 책임지는 사후관리' · 전화/카톡/견적 문의 · 이달의 포커스 할인 티저 · 이달의 추천 차량 · 지금 바로 출고 가능(재고에서 자동) · 혜택 · 고객 후기(준비 중 자리) · 상담 4단계 |
| 차량 찾기 | `cars/index.html` | 세단 / SUV / 쿠페·카브리올레 / 전기차 / AMG / Maybach 별 가로 캐러셀 + 모델 검색 + 신차·출시 예정(`#new`) |
| └ 모델 44개 | `cars/<slug>.html` | 트림·가격(2026-07-01 가격표)·제원·옵션·색상·비교 |
| 이달의 포커스 할인 | `focus.html` | 이달 할인 오른 차종 · 내 혜택 찾기(선택기) · 금융/장기렌트 추가 할인 · AMG·마이바흐 · 추가 혜택 · 모델별 할인표(검색·차종 필터) — `data/focus-YYYY-MM.json` 에서 생성 |
| 전국 재고 | `cars/stock.html` | 메일 첨부 재고 엑셀 → `build/update_stock.py` (현재 2026-10-16 기준 68개 모델 · 362개 조합 · 즉시출고 257조합) |
| 가격·혜택 | `offers.html` | 탭: 가격표 `#price` · 금융·구매 기준 `#conditions` · 추가 할인 `#extra` · 카드 혜택 `#cards` · MOU 확인 `#mou` |
| 구매 가이드 | `library/index.html` | 이달의 리포트 + 지난 리포트 목록(`library/report-YYYY-MM.html`) + 비교북 서가 39권(`library/*.html`) |
| 차민재 팀장 | `advisor.html` | 인사말 · 경력·자격 · 네 가지 사후관리 약속 |
| 상담 신청 | `consult.html` | 전화 · 카카오톡 · 견적 신청서 |
| 기타 | `policy.html`, `404.html` | |

## 빌드 구조
- **`python3 build/site.py`** 가 v2 빌드 진입점입니다. 내부적으로 `build/build.py`(v1과 같은 데이터 로더·가격표 오버레이 `build/official_price.py`·콘텐츠 블록)를 불러와 본문을 만든 뒤, 새 레이아웃·새 경로로 다시 배치하고 링크를 새 경로로 바꿉니다(옛 경로 `guide/`, `books/`, `reports/`, `price.html` 등은 생성하지 않음).
- 새 페이지 구성(홈·차량 찾기·가격·혜택·구매 가이드·차민재 팀장·상담 신청)과 문구는 `build/site.py`, 스타일은 `assets/css/style.css`.
- 빌드 끝에 `build/font_subset.py` 가 제목 글자에 맞춰 세리프 폰트를 다시 잘라 냅니다(fontTools + brotli 필요. 실패해도 시스템 세리프로 표시되고 빌드는 계속됩니다).

## 담당자 정보 — `assets/js/config.js` 가 단일 원본
`siteName, shortName, name, title, branch, dealer, address, phone, kakaoUrl, kakaoChannelUrl, youtubeUrl, blogUrl, formUrl, email, photo, siteUrl`

- 값을 바꾼 뒤 **`python3 build/site.py`** 를 실행하면 HTML·`<title>`·meta·OG 태그에 직접 반영됩니다(검색엔진·JS 미동작 환경 포함).
- 빈 값("")인 항목은 자동으로 숨겨집니다: 카카오톡 채널·유튜브·블로그·이메일·외부 폼 버튼은 표시되지 않고, 주소 줄은 생략됩니다.
  (빌드 없이 config.js만 고쳐도 `site.js`가 이름·연락처 텍스트와 링크를 채우고, 비어 있는 링크는 숨깁니다.)
- 현재 미입력: `address`(전시장 주소), `kakaoChannelUrl`, `youtubeUrl`, `blogUrl`, `email`, `formUrl`, `photo`, `siteUrl`.
- `siteUrl`(예: `https://example.com/`)을 넣으면 canonical·`og:url`·`og:image`(절대경로 `assets/img/og-image.jpg`)가 생성됩니다. 그 경우 1200×630 이미지를 `assets/img/og-image.jpg`로 넣어 주세요.

### 프로필 사진 교체 방법
1. 사진을 `assets/img/profile.jpg` 로 저장(세로 4:5 권장, 예: 800×1000, 300KB 이하).
2. `assets/js/config.js` 에서 `photo: "assets/img/profile.jpg"` 로 지정.
3. `python3 build/site.py` 실행 → 홈·차민재 팀장 페이지의 이니셜 ‘차’ 아바타가 사진으로 바뀝니다.
   (빌드하지 않아도 site.js가 런타임에 아바타를 사진으로 교체합니다.)

### 인사말·경력 문구
`build/build.py` 상단의 `INTRO_HEAD`, `INTRO_SHORT`(홈), `ABOUT_LEAD`, `ABOUT_PARAS`(소개), `CREDS`(경력·자격 배지)를 수정 후 `python3 build/site.py` 로 다시 빌드. (사후관리 약속 `PROMISES`, 상담 단계 `STEPS`, 홈 추천 차량 `picks` 는 `build/site.py`)
리포트 ‘이달의 코멘트’와 비교 자료 ‘담당자 코멘트’ 칸은 기본 숨김입니다. 직접 쓰려면 `SHOW_AUTHOR_NOTES = True`.

## 홈 히어로 이미지
- `assets/img/hero/s-class-hero-1600.webp`(1600×907, 76KB) · `s-class-hero-800.webp`(모바일 800×1000, 42KB) · `s-class-hero-1600.jpg`(폴백, 154KB), `<picture>` srcset.
- 출처: Mercedes-Benz AG 글로벌 미디어 — “Press Test Drive in Hamburg: Photo and video assets of the new Mercedes-Benz S-Class” (2026-05-13), https://media.mercedes-benz.com/en/article/8bde5eed-e31a-4643-a806-41d12fa8b0a4 (이미지 id b21c20bd-…). 유럽 사양. 기록: `build/hero_image.json`.
- ⚠️ 보도자료 이미지는 언론·편집 목적 자료입니다. 상업 게시 전 딜러사/MBK 마케팅 가이드로 사용 가능 여부를 확인하거나 공식 국내 이미지로 같은 파일명 교체하세요.

## 이달의 포커스 할인 — 매월 교체 방법
1. `data/focus-2026-10.json` 을 복사해 `data/focus-YYYY-MM.json` 으로 만들고 값만 바꿉니다(빌드는 가장 최신 파일명 1개를 사용). 이전 달 파일은 지우거나 보관해도 됩니다.
2. 주요 키: `period`(기간) · `disclaimer` · `highlights`(상단 카드) · `raised`(할인 오른 차종: `slug`=모델 페이지, `q`=재고 검색어) · `cases`/`case_note` · `finance`/`finance_notes` · `rent`/`rent_notes` · `amg`/`f1`/`maybach` · `extras` · `classes` · `table`(모델별 할인표: `my, cls, model, cash, fin, retention, tradein, conquest, raised, note, slug`).
3. 값 표기: 숫자가 없거나 '미기재'·'확인 필요' → 사이트에 **'상담 시 확인'** 으로 표시, 현금 할인 '-' → **'상담 문의'**, '—' = 해당 없음.
4. **고객용 혜택만** 입력하세요. 내부 영업 가이드의 직원 인센티브·직원/가족 프로그램·내부 처리 절차·마감/감사 규정·내부 메모·문서명·영업 화법·리드 이벤트 세부·수량 등은 넣지 않습니다(수량은 '한정 수량'만).
5. `python3 build/site.py` 로 빌드 → 아래 금지어 검사 → QA.
   `rg "SC 보너스|MB Race|STS|SCC|CMD|CONFIDENTIAL|대외 유출|MB Family|시상|환수" -g '*.html' -g '*.js' --glob '!ref/**' --glob '!qa/**'` → 0건이어야 합니다.

## 차량 사진 출처 (중요)
- 메르세데스-벤츠 코리아 공식 사이트(www.mercedes-benz.co.kr)와 이미지 CDN(assets.oneweb.mercedes-benz.com)은 제작 환경에서 봇 차단(Akamai, HTTP 403/연결 거부)으로 이미지를 내려받을 수 없었습니다.
- 대신 **Mercedes-Benz USA 공식 뉴스룸(https://media.mbusa.com/)의 보도자료 대표 이미지**(1024px)를 WebP로 변환해 `assets/img/models/` 에 넣었습니다(모델별 큰 이미지 + 560px 썸네일, 총 약 2.6MB).
- 이미지별 원본 URL·보도자료 제목은 `build/model_images.json` 에 기록되어 있습니다. 미국 사양이므로 번호판·휠·색상 등이 국내 사양과 다를 수 있습니다.
- 기본 모델 사진을 참고 이미지로 쓴 모델(대체 표시·alt에 명시): Mercedes-AMG E-Class(→E-Class), Mercedes-AMG S-Class(→S-Class), Mercedes-AMG CLE Coupé(→CLE Coupé), Mercedes-AMG CLE Cabriolet(→CLE Cabriolet).
- 사진 없음: **EQA** (미국 미판매로 공식 보도 이미지 없음) → 실루엣 자리표시 유지.
- ⚠️ 보도자료 이미지는 일반적으로 언론·편집 목적 제공 자료입니다. 상업적 영업 사이트에 게시하기 전 딜러사(모터원)·메르세데스-벤츠 코리아 마케팅 가이드에 따라 사용 가능 여부를 확인하거나, 딜러사가 제공하는 국내 공식 이미지로 교체하세요. 교체는 같은 파일명으로 `assets/img/models/<slug>.webp`, `<slug>-560.webp` 를 덮어쓰면 됩니다.

## 모델 소개 문구 출처
`build/official_kr.json` — mercedes-benz.co.kr 각 모델 overview 페이지의 ‘하이라이트’ 문구를 요약(2026-10-18, 검색 색인 기준). `synth: true` 항목은 검색 요약 기반이라 공식 페이지에서 재확인을 권장합니다.

## 상담 폼
백엔드가 없습니다. `email`을 넣으면 메일 앱으로, `formUrl`을 넣으면 외부 신청서 버튼이 나타납니다. 둘 다 없으면(현재) 작성 내용을 정리해 **문자(sms:010-4921-5059)로 보내기 / 복사 후 카카오톡 열기** 버튼을 보여 줍니다.

## 차량 가격 기준 — 2026년 7월 1일 26MY 가격표
- 원본: 영업 담당자가 제공한 메르세데스-벤츠 코리아 '26MY 차량가격표'(2026-07-01) 이미지 → `data/official-price-2026-07.json` (101행, 2회 확대 판독).
- 적용: `build/official_price.py` 가 빌드 시 MY26 트림과 S클래스 27MY F/L 트림의 권장 소비자가를 덮어쓰고, 할인·실구매가를 같은 % 조건으로 다시 계산합니다(만원 미만 절삭). 매핑은 파일 안에 명시적으로 적혀 있습니다.
- 변경 내역은 빌드할 때마다 `build/price_overlay_log.json` 에 기록됩니다(changed / anomaly / 가격표에 없는 트림 목록).
- 가격표 이상값: EQE 350+ 가 1,100,000,000원으로 표기됨 → 오기로 보고 게시하지 않으며 기존 110,000,000원을 유지(`ANOMALIES`). 가격이 공란인 트림은 '가격 문의'로 표시.

## 재고 — 매일 업데이트 방법 (v2)
재고 페이지(`cars/stock.html`)와 홈·차량 찾기의 '지금 바로 출고 가능' 영역은 `data/stock.json` 으로 만들어지고, 이 파일은 모터원 Sales Operations 의 '◆◆ YYYY-MM-DD 재고 현황◆◆' 메일 첨부 엑셀(`YYYY-MM-DD 차량 재고현황_메일용.xlsx`, 시트 `allocation`)에서 생성합니다.

1. Gmail 에서 최신 메일 찾기: `subject:재고현황 OR subject:"재고 현황"` (발신 @motorone.co.kr, 가장 최근 날짜).
2. 첨부 엑셀을 `data/inbox/` 에 내려받기 (파일명에 날짜가 들어 있어야 재고 기준일로 인식, 아니면 `--date` 지정).
3. 실행:
   ```bash
   cd /workspace/benz-site-v2
   python3 build/update_stock.py "data/inbox/2026-10-16 차량 재고현황_메일용.xlsx"     # 파싱 → 검증 → data/stock.json → build/site.py 로 v2 전체 재빌드
   # 옵션: --date 2026-10-16 (파일명에 날짜가 없을 때) · --force (재고가 70% 넘게 줄어든 게 맞을 때) · --no-build
   ```
4. QA (로컬 서버 8081): `python3 -m http.server 8081 --bind 127.0.0.1 &` 후 `python3 qa/linkcheck.py && python3 qa/browser_qa.py && python3 qa/interact.py`
5. 배포용 압축: `python3 build/mkzip.py` → `/workspace/benz-site-v2-lite.zip` (`data/inbox/`, 스크린샷, 엑셀 파일은 자동 제외).

- 안전장치: 필수 열 누락, 데이터가 너무 적음(모델 5개·조합 20개·50대 미만), 모델명/색상명 깨짐, 이전보다 조합이 70% 넘게 줄어듦, 결과에 차대번호·전화번호·리드/계약번호 형태가 섞임 → 덮어쓰지 않고 이전 `stock.json` 을 유지합니다. 빌드가 실패하면 이전 파일로 되돌립니다. 같은 파일을 다시 넣으면 'no change'(멱등). 실행 기록: `data/stock-update.log`, 직전 데이터: `data/stock.prev.json`.
- 공개하는 정보: 모델명, 모델 연도, 차종 분류, 외장 색상(투톤 포함), 내장 색상, 조합별 수량, 출고 가능 월. **공개하지 않는 정보**: 차대번호, 엔진번호, 커미션·재고·리드·거래 번호, 고객명·회사명, 배정 전시장·팀·영업사원, 공급가, 생산일, 물류·내부 상태 사유 등 나머지 모든 열.
- 집계 기준: `차량 상태 = 판매 가능` 인 차량만 포함(계약 확정·가계약·판매 완료 제외). **즉시출고** = 재고 유형 '입고 물량' + 출고 가능일(PDD)이 기준일 이전 + 가용 여부 '판매 가능'. 그 외는 PDD 월 기준 **출고예정**.
- `data/inbox/` 원본 엑셀에는 개인정보가 들어 있으니 웹 서버에 올리거나 공유하지 마세요.

## 데이터 갱신 / 다시 빌드
`ref/data/*.json` (가격·제원·옵션·MOU 데이터) → `python3 build/site.py`
가격·재고·프로모션은 매월 바뀌므로 공식 가격표(mercedes-benz.co.kr ‘차량 가격표’ PDF)와 딜러사 자료로 직접 갱신해야 합니다.

## 로컬 실행 / QA
`python3 -m http.server 8081 --bind 127.0.0.1` 후 http://127.0.0.1:8081/ (QA 스크립트는 8081 기준)
QA: `python3 qa/linkcheck.py`, `python3 qa/browser_qa.py`(375·1280), `python3 qa/interact.py`(새 IA 기준 52개 항목), `python3 qa/contrast.py`(WCAG AA)
스크린샷: `python3 qa/screens.py` — **첫 화면(above-the-fold)만** 찍습니다(1280×900, 375×812). 원본 PNG는 `screenshots/`, 공유용 JPEG(최대 1000px, 품질 80)는 `preview/`. 전체 페이지 캡처는 만들지 않습니다.

## 홈 히어로 시안 (mockups/) — index.html 미적용
- `mockups/hero-a.html` 좌우 분할형 · `hero-b.html` 차량 옆에 선 구도 · `hero-c.html` 명함 카드형. 실제 헤더·메뉴·CSS + 홈 나머지 섹션 포함, `noindex`, 사이트 메뉴에는 연결하지 않음. 스타일: `assets/css/mockups.css`, 생성: `build/site.py` 의 `build_mockups()`.
- 사진 교체: `assets/img/rep/rep.jpg`(상반신, 4:5 권장 — 시안 A·C) / `assets/img/rep/rep-standing.jpg`(전신, 배경 제거 PNG/JPG 권장 — 시안 B, 파일명을 바꾸면 `REP_STANDING` 수정)를 넣고 `python3 build/site.py` 하면 실루엣 자리표시(`rep-placeholder.svg`, `rep-standing-placeholder.svg`)와 '팀장님 사진 자리' 캡션이 자동으로 실제 사진으로 바뀝니다.

### 실제 프로필 사진 (2026-10-19)
- 원본(사용자 제공) → `assets/img/rep/rep.jpg`(800×1000 상반신 4:5, 홈 아바타·팀장 소개·시안 A·C) · `rep-cutout.png/.webp`(배경 제거 컷아웃, 시안 B 계열). `config.js` 의 `photo` 가 `assets/img/rep/rep.jpg` 로 설정됨.
- 배경 제거: `pip install rembg[cpu]` → birefnet-portrait 모델 + 1.2px 페더 + 흰 배경 번짐 제거. 얼굴·외모는 수정하지 않았습니다.
- 시안 B 계열(`mockups/hero-b.html` S-Class, `hero-b2` AMG GT, `hero-b3` 마이바흐, `hero-b4` 전기 G-Class, `hero-b5` 라이트 쇼룸): 컷아웃을 차량 앞(오른쪽)에 배치, 하단·좌우 페이드, 장면별 색보정·림라이트·그림자(`assets/css/mockups.css` 의 `.mhv-*` `--grade`). 배경 출처: `build/hero_image.json`.
