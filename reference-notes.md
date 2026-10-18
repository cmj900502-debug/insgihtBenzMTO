# Reference site notes — https://mb-hansdream.co.kr/

Crawled 2026-10-18 (KST, UTC+9) with curl from `sitemap.xml` (97 URLs) + 2 extra URLs found in links (`BenzDream_MonthlyReport_latest.html` = copy of 202610, `MY26_CLA_C178.html` = meta-refresh redirect to `MY27_CLA_C174_electric.html`). Site is static HTML; model guide pages embed their data as JSON (`<script id="vehicle-data" type="application/json">`), which was parsed directly. No headless browser was needed for content.

**Not fetched (by choice):** `robots.txt` disallows `/BenzDream_Inventory.html`, `/BenzDream_Sales_Inventory.html` and `/quote_*` — these were respected and not crawled. External services (Kakao channel, Google Form `forms.gle/...`, YouTube, Naver blog) are the rep's personal channels and were not copied. Vehicle/colour photos (`assets/guides/*.webp`, `images/*.webp`) were NOT downloaded; they are manufacturer/rep images — placeholders are used instead.

**Content policy of the reference:** its `BenzDream_ContentPolicy.html` states that the rep's own text, buying-strategy write-ups, comparison layouts and self-made images/videos may not be copied wholesale or re-used with a swapped author/contact, while it claims no exclusive right over factual info (specs, prices). The new site therefore reuses factual data (prices, discounts, rates, specs, options, stock combos, MOU list, card terms) and the menu structure, but uses original layout/CSS/copy and leaves editorial commentary as placeholders.

## Global navigation (header, every page)
Brand "한호만 · 벤츠 고양 전시장" → `/`
- **홈** → `/`
- **신차·사전예약** → `/#launches (home section)`
- **차종별 가이드** → `BenzDream_Models.html`
- **가격·프로모션** → `BenzDream_PriceAndPromotion_2026.html`
- **전국 재고** → `BenzDream_Stock.html`
- **구매전략리포트** → `BenzDream_MonthlyReport_latest.html (→ 2026-10)`
- **카드혜택** → `BenzDream_ShinhanCards.html`
- **MOU 확인** → `BenzDream_MOU_List.html`
- **상담하기 ↗** → `Kakao channel chat (external)`
- Secondary strip on info pages: 01 가격·프로모션 · 02 전국 재고 · 03 구매전략리포트 · 04 카드혜택 · 05 MOU 확인; "Next step" block linking all of them + 차종별 가이드.
- Footer: rep name/showroom, address, phone, Kakao, YouTube, About (`BenzDream_About.html`), Naver blog, 콘텐츠 이용 안내 (`BenzDream_ContentPolicy.html`).

## Home (`/`)
1. Hero carousel: 01 rep intro · 02 The all-new electric CLA (트림·옵션) · 03 The all-new GLC Electric (사전계약).
2. Rep intro ("당신의 벤츠를 함께 고민할 사람") + buttons: 직접 상담하기 (Kakao), 유튜브, 소개·상담 안내, 신차·사전예약 소식.
3. **#launches – New & Upcoming (6 cards):** 140주년 에디션 II (GLE/Coupé/GLS) · all-new electric CLA · all-new GLC Electric · all-new GLB · new G-Class MY27 · new S-Class MY27 Facelift.
4. Before you buy: Mercedes-Benz × Shinhan Card; 01 가격·프로모션·금융 · 02 전국 재고 · 03 이달의 구매전략 리포트 · 04 매월 리포트 받아보기 (Kakao channel); past reports 2026-09/07/06/05/04.
5. Model finder (search + 44 models) grouped: 세단·해치백 / SUV / 전기차 / 쿠페·카브리올레·AMG GT / Mercedes-Maybach.
6. Meet your advisor (YouTube) · 상담 CTA (Kakao, Google Form 견적·재고 상담 신청서) · contact block.

## 차종별 가이드 (`BenzDream_Models.html`) — 44 model guides
Search + category tabs (전체 · 세단·해치백 · SUV · 전기차 · 쿠페·카브리올레 · AMG · Maybach).
- **세단·해치백** (6; A → CLA → C → E → S): A-Class [MY26, 4 trims], CLA [MY26, 3 trims], CLA (신형 하이브리드) [MY27, 2 trims], C-Class [MY26, 5 trims], E-Class [MY27, 18 trims], S-Class [MY27, 15 trims]
- **SUV** (8; GLA → GLB → GLC → GLE → GLS → G): GLA [MY27, 2 trims], GLB [MY26, 4 trims], GLC [MY27, 7 trims], GLC Coupé [MY27, 6 trims], GLE [MY26, 7 trims], GLE Coupé [MY26, 4 trims], GLS [MY26, 8 trims], G-Class [MY27, 8 trims]
- **전기차** (9; 전기 세단부터 SUV까지): CLA electric [MY27, 5 trims], EQE [MY27, 2 trims], EQS [MY25, 1 trims], EQA [MY27, 4 trims], EQB [MY26, 4 trims], GLC electric [MY27, 2 trims], EQE SUV [MY27, 4 trims], EQS SUV [MY27, 4 trims], G-Class electric [MY27, 3 trims]
- **쿠페·카브리올레** (2; 같은 클래스의 쿠페와 오픈톱을 함께): CLE Coupé [MY27, 6 trims], CLE Cabriolet [MY27, 6 trims]
- **AMG** (15; 세단 → SUV → 쿠페·로드스터): Mercedes-AMG A-Class [MY27, 3 trims], Mercedes-AMG CLA [MY26, 3 trims], Mercedes-AMG E-Class [MY27, 3 trims], Mercedes-AMG S-Class [MY26, 2 trims], Mercedes-AMG GT 4-Door [MY26, 2 trims], Mercedes-AMG GLB [MY26, 2 trims], Mercedes-AMG GLC [MY27, 2 trims], Mercedes-AMG GLC Coupé [MY27, 2 trims], Mercedes-AMG GLE [MY26, 2 trims], Mercedes-AMG GLE Coupé [MY26, 2 trims], Mercedes-AMG GLS [MY26, 1 trims], Mercedes-AMG CLE Coupé [MY27, 4 trims], Mercedes-AMG CLE Cabriolet [MY27, 4 trims], Mercedes-AMG GT Coupé [MY27, 6 trims], Mercedes-AMG SL [MY27, 4 trims]
- **Maybach** (4; S-Class → GLS → EQS SUV → SL): Mercedes-Maybach S-Class [MY27, 6 trims], Mercedes-Maybach GLS [MY26, 4 trims], Mercedes-Maybach EQS SUV [MY27, 2 trims], Mercedes-Maybach SL [MY27, 2 trims]

### Guide page (`BenzDream_Guide_<slug>.html`) contents
Sections: 트림 비교 (trim cards w/ MY + 권장가 만원) · 구매 정보 · 제원 (length/width/height/wheelbase/cc/ps/torque/efficiency/battery/range) · 옵션 (paint `xxxU` & upholstery `xxxA` codes with 기본/선택/유료 선택/미적용) · 장비 matrix by category · 색상 (catalog colours) · 차량 사진 · 관련 영상 (rep YouTube) · 관련 어프로치북 links · 다른 차종.
Total trims across 44 guides: 190.

## 가격·프로모션 (`BenzDream_PriceAndPromotion_2026.html`) — 2026년 10월
기준: 10월 1일자 프로모션·현금 할인 수정본, MY27 권장가 9/25 가격표, VAT 포함·만원 미만 절삭. Columns: 모델명 · 권장 소비자가(개소세 5%) · 기본 할인 · 파이낸셜/모빌리티 JC · 실 구매가(정상 통관) · 개소세인하 적용가(7/1 이전 통관).
- **A클래스** — 5 rows
- **CLA** — 3 rows
- **GLA · GLB** — 5 rows
- **C클래스** — 3 rows
- **E클래스** — 16 rows
- **S클래스** — 17 rows
- **CLE · AMG GT · SL** — 23 rows
- **GLC** — 17 rows
- **GLE** — 11 rows
- **GLS · G클래스** — 15 rows
- **전동화 EQ** — 13 rows
- Accordions: 10월 구매 기준·계약금 (300만원 / S·G·BTO 500만원; 인도 10/1–11/4) · 현금 vs 금융 비교 · 10월 금리(60개월/선수금 30%, 14 models, 일반 할부 vs 안심보장할부; 리텐션 −0.40%p) · 전기차 특별금융·충전 바우처 · 6개월 월 납입금 지원 (12 models) · 골든타임 (7일 이내 완납 → MB 컬렉션) · AMG F1 패독 투어.
- 공통 추가 할인: MOU 2% / TEV+ 법인 2% · 재구매 1–2% (Maybach S680·GLS600 9%) · 인증중고차 매각 +1% · 타브랜드 1% (Maybach 7%) · 장기전시/하자/100km+ 1% · 무상 보증연장.

## 전국 재고 (`BenzDream_Stock.html`) — 기준일 2026-10-13
57 models, 277 exterior/interior combos (e.g. Maybach S 680 4MATIC; GLS 450 4MATIC AMG Line Premium; Maybach S 580 4MATIC; Maybach EQS 680 SUV; E 350 e 4MATIC EXCLUSIVE with EQ Hybrid Technology; Maybach SL 680 Monogram Series …). Page = list of model → "외장 / 실내" combos + 상담 CTA.

## 구매전략리포트 (`BenzDream_MonthlyReport_YYYYMM.html`)
- BenzDream_MonthlyReport_202604.html: "2026년 4월 벤츠 구매전략 리포트 | BenzDream 한호만 팀장" — 16 tables (🎖 140주년 Anniversary Edition, ⚪ RoF Edition, 🚀 Launch Edition, 클래스별 상세 분석, 클래스별 상세 분석, 클래스별 상세 분석 …)
- BenzDream_MonthlyReport_202605.html: "2026년 5월 벤츠 구매전략 리포트 | BenzDream 한호만 팀장" — 16 tables (대외 환경 — 국내 수입차 시장 (KAIDA 1–4월 누적), 4월 → 5월 변동 요약, 4월 → 5월 변동 요약, 클래스별 5월 가이드, 클래스별 5월 가이드, 클래스별 5월 가이드 …)
- BenzDream_MonthlyReport_202606.html: "벤츠파이낸셜이 최고의 금융사가 될 겁니다 | 2026년 6월 BenzDream 구매전략 리포트" — 16 tables (대외 환경 — 국내 수입차 시장 (KAIDA 1–5월 누적), 6월 벤츠파이낸셜 추가할인 — 같은 모델, 결과가 달라지는 달, 6월 벤츠파이낸셜 추가할인 — 같은 모델, 결과가 달라지는 달, 클래스별 6월 가이드, 클래스별 6월 가이드, 클래스별 6월 가이드 …)
- BenzDream_MonthlyReport_202607.html: "개별소비세 정상화. 하지만 아직 끝나지 않았습니다. | 2026년 7월 BenzDream 구매전략 리포트" — 14 tables (대외 환경 — 국내 수입차 시장 (KAIDA 2026년 1–6월 누적), 7월 파이낸셜·모빌리티 조인트 캠페인 — 실구매가를 가르는 카드, 7월 파이낸셜·모빌리티 조인트 캠페인 — 실구매가를 가르는 카드, 7월 파이낸셜·모빌리티 조인트 캠페인 — 실구매가를 가르는 카드, 7월 파이낸셜·모빌리티 조인트 캠페인 — 실구매가를 가르는 카드, 클래스별 7월 가이드 …)
- BenzDream_MonthlyReport_202609.html: "BenzDream 구매전략 리포트 · 2026년 9월" — 18 tables (연식 전환 구도 — 26년식 vs 27년식, 색상 · 사양 선택 가이드, 9월 벤츠 파이낸셜 — 실구매가를 가르는 카드, 9월 벤츠 파이낸셜 — 실구매가를 가르는 카드, 9월 벤츠 파이낸셜 — 실구매가를 가르는 카드, 9월 벤츠 파이낸셜 — 실구매가를 가르는 카드 …)
- BenzDream_MonthlyReport_202610.html: "2026년 10월 벤츠 구매전략리포트 | BenzDream 한호만" — 16 tables (연식 전환 구도 — MY26 vs MY27, 주요 모델의 외장·시트 조합, 모델별 금융 추가 할인, 일반 할부와 안심보장할부 금리 비교, 개인별 추가 조건, A클래스 …)
Content = rep-authored editorial strategy + tables (연식 전환 구도, 재고 조합, 금융 추가 할인, 금리, 개인별 조건, 차종별 가격).

## 카드혜택 (`BenzDream_ShinhanCards.html`)
Payment guide (선입금 카드결제 via 가상계좌 / 자동차 추가한도; 추천인 = rep name; 결제 문의 1688-7474), 3 cards (Avantgarde 7.7만 · Exclusive 19.7만 · MANUFAKTUR 69.7만 연회비; gifts; 국내 할인 0.5–1.5%; 스토어/충전/라운지), 할부 금리 12–60개월 4.1–4.4%, 1억원 결제 예시, 기프트 옵션 table, 전월실적별 할인율 table, 상세 비교 table, Shinhan mycar quick-apply links.

## MOU 확인 (`BenzDream_MOU_List.html`) — 2026년 6월 기준, 603 companies, searchable; 임직원 추가할인 2%.

## 신차·사전예약 / 어프로치북 (`MY2x_*.html`, 39 pages)
- `MY25_EQESUV_EQE350_EQE500_20260228.html` — BenzDream MY26 EQE SUV EQE 350+ vs EQE 500 4MATIC 어프로치북 (1 tables)
- `MY26_AClass_A220_Hatch_Sedan_20260418.html` — 벤츠 A220 해치백 vs 세단 어프로치북 | BenzDream 한호만 팀장 (1 tables)
- `MY26_AMGGT_GT55_GT63Se_20260330.html` — BenzDream | AMG GT 55 4MATIC+ vs GT 63 S E Performance 어프로치북 (1 tables)
- `MY26_CClass_C200_AV_AMG_20260330.html` — BenzDream C-Class C200 AVANTGARDE vs AMG Line 어프로치북 (1 tables)
- `MY26_CLA_CLA250_AMG_20260330.html` — BenzDream CLA-Class CLA 250 4MATIC AMG Line 어프로치북 (1 tables)
- `MY26_CLE53Cab_SL43_20260330.html` — BenzDream | AMG CLE 53 vs SL 43 어프로치북 (1 tables)
- `MY26_CLECabriolet_CLE200_CLE450_AMG_20260330.html` — BenzDream CLE 카브리올레 CLE 200 vs CLE 450 어프로치북 (1 tables)
- `MY26_CLECabriolet_CLE450_AMG53_20260330.html` — BenzDream | CLE Cabriolet 어프로치북 (1 tables)
- `MY26_CLECoupe_CLE200_CLE450_20260330.html` — 벤츠 CLE 쿠페 어프로치북 · CLE200 vs CLE450 4MATIC | BenzDream 한호만 (1 tables)
- `MY26_EClass_E200_AV_AMG_20260330.html` — BenzDream E-Class E200 AVANTGARDE vs AMG Line 어프로치북 (1 tables)
- `MY26_EClass_E220d_E300_EX_20260330.html` — BenzDream E-Class E220d vs E300 EXCLUSIVE 어프로치북 (1 tables)
- `MY26_EClass_E300EX_E350e_20260330.html` — BenzDream E-Class E300 4MATIC EXCLUSIVE vs E350e 4MATIC EXCLUSIVE 어프로치북 (1 tables)
- `MY26_EClass_E300_EX_AMG_20260330.html` — BenzDream E-Class E300 4MATIC EXCLUSIVE vs AMG Line 어프로치북 (1 tables)
- `MY26_EClass_E450AMG_AMGE53_20260330.html` — BenzDream E-Class E 450 AMG Line vs AMG E 53 어프로치북 (1 tables)
- `MY26_EClass_E450_AMG_EX_20260330.html` — BenzDream E-Class E450 4MATIC AMG Line vs EXCLUSIVE 어프로치북 (1 tables)
- `MY26_EClass_FullLineup_20260303.html` — BenzDream E-Class Full Lineup 어프로치북 (2 tables)
- `MY26_EQA_EQA250_PRG_AMG_20260330.html` — BenzDream · EQA 고객 상담 가이드 (1 tables)
- `MY26_EQB_EQB300_PRG_AMG_20260330.html` — BenzDream · EQB 고객 상담 가이드 (1 tables)
- `MY26_GLA_GLB_250_4M_20260330.html` — GLA 250 4MATIC vs GLB 250 4MATIC · BenzDream 어프로치북 (1 tables)
- `MY26_GLB_X244.html` — The all-new electric GLB | BenzDream 한호만 팀장 (1 tables)
- `MY26_GLCCoupe_GLC300_AVG_AMG_AMG43_20260330.html` — BenzDream GLC Coupé 어프로치북 | GLC300 AVANTGARDE · AMG Line · AMG GLC 43 (1 tables)
- `MY26_GLC_GLC220d_GLC300_AV_AMG_AMG43_20260329.html` — BenzDream GLC 어프로치북 | GLC 220d · GLC 300 AVANTGARDE · AMG Line (1 tables)
- `MY26_GLECoupe_GLE450d_GLE450_AMG_20260329.html` — BenzDream GLE Coupé GLE 450d vs GLE 450 AMG Line 어프로치북 (1 tables)
- `MY26_GLE_300d_350_450_AMG_20260329.html` — BenzDream GLE-Class Approach Book (1 tables)
- `MY26_GLE_GLS_140th_Signature.html` — GLE·GLE Coupé·GLS 140주년 에디션 II | BenzDream 한호만 팀장 (1 tables)
- `MY26_GLS_GLS450_GLS580_AMG_20260329.html` — BenzDream GLS-Class GLS 450 AMG Line Premium vs GLS 580 AMG Line 어프로치북 (1 tables)
- `MY26_GLS_GLS580_AMG_AMGGLS63_20260329.html` — 벤츠 GLS 580 vs AMG GLS 63 어프로치북 | BenzDream (1 tables)
- `MY26_MaybachGLS_GLS580_GLS600_20260330.html` — 벤츠 GLS 580 vs 마이바흐 GLS 600 비교 | BenzDream 한호만 팀장 (1 tables)
- `MY26_MaybachS_S580_S680_20260301.html` — BenzDream 마이바흐 S580 vs S680 어프로치북 (1 tables)
- `MY26_SClass_S350d_S450SWB_20260330.html` — BenzDream S-Class 어프로치북 | S350d · S450 SWB 4MATIC (1 tables)
- `MY26_SClass_S450_S500_S580_20260330.html` — BenzDream S-Class 어프로치북 | S450 · S500 · S580 4MATIC (1 tables)
- `MY26_SClass_S500_S580_20260330.html` — BenzDream S-Class S500 vs S580 어프로치북 (1 tables)
- `MY26_SClass_S580_AMGS63_20260330.html` — 벤츠 S580 vs AMG S63 E Performance 어프로치북 | BenzDream (1 tables)
- `MY26_SClass_S580_MaybachS580_20260330.html` — BenzDream 벤츠 S580 vs 마이바흐 S580 어프로치북 (1 tables)
- `MY26_SL_SL43_SL63_20260330.html` — BenzDream | AMG SL 어프로치북 (1 tables)
- `MY27_CLA_C174_electric.html` — MY27 The all-new electric CLA (C174) 국내 사양 총정리 | BenzDream 한호만 팀장 (3 tables)
- `MY27_GClass_465_1.html` — The new G-Class (W465) MY27 | BenzDream 한호만 팀장 (0 tables)
- `MY27_GLC_EV_709_1.html` — The all-new GLC Electric (X540) · 사전계약 | BenzDream 한호만 팀장 (3 tables)
- `MY27_TheNew_SClass_807_1.html` — The new S-Class MY27 (807) 카탈로그 | BenzDream 한호만 팀장 (1 tables)

## About (`BenzDream_About.html`) & 콘텐츠 이용 안내
Personal bio of the rep (YouTube 2.56만 subscribers, 254 videos as of 2026-09-12), services (차종·옵션 비교 / 가격·구매 조건 / 재고·출고 상담), channels, contact, showroom address. **Not reproduced** — replaced with original placeholder copy.

## 2단계 (2026-10-18) — 공식 사이트 반영 메모
- www.mercedes-benz.co.kr / assets.oneweb.mercedes-benz.com / shop.mercedes-benz.com: 제작 환경(box)에서 curl·헤드리스 브라우저 모두 Akamai 차단(403/연결 끊김). 외부 WebFetch도 모델 페이지에서 차단 페이지 반환. 가격표는 PDF라 수집 불가.
- 모델 하이라이트 문구: 검색 색인에 저장된 공식 overview 페이지 본문을 요약 → `build/official_kr.json` (출처 URL 포함).
- 차량 사진: Mercedes-Benz USA 공식 뉴스룸(media.mbusa.com) 보도자료 대표 이미지 → `build/model_images.json` (원본 URL·제목 포함).
- 공식 제원 반영: Mercedes-AMG E 53 HYBRID 4MATIC+ (공식 카탈로그 2026-05-19) — 참고 데이터에 비어 있던 배기량·변속기·복합효율·전장/전폭/전고를 채움.
- 가격: 공식 가격표 PDF에 접근할 수 없어 교차 검증 불가. 참고 데이터(딜러 기준 2026-10)를 유지.
