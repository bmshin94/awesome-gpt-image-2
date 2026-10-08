# awesome-gpt-image-2 전수조사 분석 및 활용 전략 (한국어 정리)

> 이 문서는 `awesome-gpt-image-2` 저장소를 전수조사(393MB / 725파일 / 코드 약 10,200줄 / 이미지 547장)한 결과와,
> 설치·사용법, 정체(플러그인/스킬/MCP), API 토큰, AI 에이전트 활용, 수익화, React·PHP 이식, 유튜브 제작 가능성까지
> 정리한 종합 문서입니다. 조사 기준일: 2026-10-08.

---

## 📌 관련 주소 (GitHub & 서비스)

| 구분 | 주소 |
|---|---|
| **내 포크 (작업 저장소)** | https://github.com/bmshin94/awesome-gpt-image-2 |
| **원본 (Upstream)** | https://github.com/freestylefly/awesome-gpt-image-2 |
| 실서비스 웹사이트 | https://gpt-image2.canghe.ai |
| GPT Image 2.5 스포트라이트 | https://gpt-image2.canghe.ai/gpt-image-2-5/?lang=en |
| 커뮤니티 페이지 | https://gpt-image2.canghe.ai/community |
| npm 패키지 (스킬) | https://www.npmjs.com/package/gpt-image-2-style-library |
| GitHub Packages (스킬) | https://github.com/freestylefly/awesome-gpt-image-2/pkgs/npm/gpt-image-2-style-library |
| 스킬 소스 경로 | `agents/skills/gpt-image-2-style-library/SKILL.md` |
| 이슈 | https://github.com/freestylefly/awesome-gpt-image-2/issues |
| 라이선스 | MIT (코드 기준) — https://github.com/bmshin94/awesome-gpt-image-2/blob/main/LICENSE |

### 주요 문서 바로가기
- 전체 갤러리 색인: [`docs/gallery.md`](../gallery.md)
- 케이스 1~165: [`docs/gallery-part-1.md`](../gallery-part-1.md)
- 케이스 166~544: [`docs/gallery-part-2.md`](../gallery-part-2.md)
- 산업용 템플릿 + 避坑指南(삽질 방지 가이드): [`docs/templates.md`](../templates.md)
- 에이전트 스킬: [`agents/skills/gpt-image-2-style-library/SKILL.md`](../../agents/skills/gpt-image-2-style-library/SKILL.md)
- 면책 조항: [`docs/disclaimer.md`](../disclaimer.md)

---

## 1. 한 줄 정의

> **"AI 이미지 생성 프롬프트 541개를 산업 표준처럼 규격화한 도서관 + 그걸 AI 에이전트가 자동으로 꺼내 쓰게 만든 스킬 + 그 전체를 상품으로 판매하는 결제형 웹사이트"** 3개가 한 저장소에 들어있다.

단순 "awesome 리스트"가 아니라, **실제로 과금 중인 SaaS 제품의 전체 소스코드**가 포함된 저장소다.

---

## 2. 기본 정보

| 항목 | 내용 |
|---|---|
| 원작자 | 중국 개발자 苍何 (Canghe) |
| 라이선스 | MIT (**코드에만** 적용) |
| 용량 | 393MB (이미지 159MB) |
| 파일 수 | 725개 |
| 지원 언어 | 영어 / 简体中文 / 日本語 — **한국어 없음** |
| Trendshift 등재 | 있음 |

---

## 3. 저장소의 4개 레이어

### 🟦 레이어 1 — 콘텐츠 자산 (541 케이스)

```
docs/gallery-part-1.md   6,776줄  → 케이스 1~165
docs/gallery-part-2.md  12,527줄  → 케이스 166~544
docs/gallery.md            838줄  → 카테고리별 색인
docs/templates.md        1,080줄  → 21~22개 산업용 템플릿 + 避坑指南
data/images/            547장     → 모든 케이스 결과 이미지
```

케이스 1개 구조 = **결과 이미지 + 출처 + 검증된 프롬프트 원문** 3종 세트.

**카테고리별 실제 분포** (`data/cases.json` 집계, 합계 541)

| 카테고리 | 개수 | 카테고리 | 개수 |
|---|---|---|---|
| 포스터·타이포 | **90** | 일러스트·아트 | 59 |
| 사진·실사 | **78** | 차트·인포그래픽 | 53 |
| UI·인터페이스 | **73** | 상품·이커머스 | 42 |
| 캐릭터·인물 | 31 | 브랜드·로고 | 27 |
| 기타 | 28 | 장면·스토리텔링 | 21 |
| 역사·고전 | 16 | 건축·공간 | 12 |
| 문서·출판 | 11 | **합계** | **541** |

> ⚠️ README 배지는 `544`로 표기되지만 실제 `cases.json`에는 **541개** (번호 공백 구간 존재).

### 🟩 레이어 2 — "프롬프트 애즈 코드" 템플릿 엔진

`docs/templates.md`에 템플릿 21개. 각 템플릿마다 3종 제공:

1. **일반 템플릿** — 대괄호 빈칸 채우기 방식
2. **JSON 고급 템플릿** — 원문 주석에 *"에이전트 호출용 추천"*이라 명시. Prompt-as-Code의 핵심
3. **避坑指南 (삽질 방지 가이드)** — 실무적으로 가장 값진 부분

避坑指南 실제 예시 (UI 카테고리):
- "플랫폼 + 비율 + 레이아웃을 명시하라. 안 쓰면 모델이 인턴처럼 레이아웃을 망친다."
- "'텍스트 반드시 판독 가능, 지정 문자 그대로 표시'를 강제하라. 안 하면 깨진 글자가 나온다."
- "플랫폼 특징을 구분하라 — X는 블루체크, 도우인은 음악 디스크, 샤오홍슈는 2열 워터폴."
- "차량용/스마트홈 화면은 21:9 고정이니 맨 앞에 써라. 안 쓰면 폰 9:16으로 나온다."

### 🟨 레이어 3 — AI 에이전트 스킬

```
agents/skills/gpt-image-2-style-library/
├── SKILL.md                        ← 에이전트 행동 지침 (YAML frontmatter)
├── references/style-library.md      659줄 ← 자동 생성 상세 색인
├── bin/install.mjs                  ← 로컬 에이전트 폴더 설치 CLI
├── agents/openai.yaml               ← Codex/OpenAI 메타데이터
└── assets/city-life-system-map.png
.claude-plugin/marketplace.json      ← Claude Code 플러그인 매니페스트 (v1.0.4)
```

**SKILL.md의 6단계 워크플로우**
1. 사용자 언어 감지 → 같은 언어로 답변
2. 목표 산출물 식별 (product/poster/UI/infographic/brand/photo/illustration/character/scene/history/document/special)
3. 매칭 순서 고정: **템플릿 카테고리 → 스타일 태그 → 장면 태그 → 유사 케이스**
4. 1개가 압도적이면 바로 사용 / 애매하면 2~3개 제시 후 사용자 선택
5. 최종 프롬프트 **6블록 조립**: `주제·과업` → `구도·레이아웃` → `비주얼 스타일·재질` → `텍스트·라벨` → `비율·출력 포맷` → `제약·네거티브`
6. 선택한 템플릿명 + 참조 케이스 ID 함께 출력

**데이터 단일 소스(Single Source of Truth) 구조** — 이 저장소의 가장 잘 만든 부분

```
data/style-library.json (41KB)
  ├─ categories 13 / styles 19 / scenes 10 / templates 22
        │
   ┌────┴────┐
   ▼         ▼
generate-style-skill   generate-site-data
   │         │
   ▼         ▼
references/*.md    data/cases.json
(AI가 읽음)        (웹이 읽음)
```
→ **JSON 하나 고치면 웹사이트와 AI 스킬이 동시에 갱신**된다.

### 🟥 레이어 4 — 상용 결제 웹사이트 전체 소스 (숨은 보물)

**프론트엔드** (React 19 + Vite 7)
```
src/main.jsx          4,315줄  ← 갤러리 본체 (필터/모달/복사/생성/즐겨찾기/결제UI)
src/community.jsx       681줄  ← 유료 커뮤니티 결제 페이지
src/image25/App.jsx     194줄  ← GPT Image 2.5 드래그 비교 슬라이더
src/apimartClient.js    299줄  ← 브라우저 직접 생성 클라이언트
합계 약 5,500줄
```

**백엔드** (Vercel Serverless, 24개 엔드포인트)
```
api/generate-image.js       ← 이미지 생성 (크레딧 예약→호출→확정/환불)
api/generation/status.js    ← 비동기 폴링
api/generation/callback.js  ← 웹훅 수신
api/me.js, api/favorites.js
api/billing/        checkout · webhook · plans · history · portal  (Stripe)
api/billing/alipay/ checkout · notify · query · close · refund-query (支付宝)
api/community/      config · status · qr · alipay/*  (유료 단톡방 ¥9.90)
api/admin/          users · metrics · credits/adjust · community/{orders,qr,refund,revoke}
api/auth/watcha/    start · callback  (Watcha OAuth, PKCE 직접 구현)
```

**DB** (Supabase/PostgreSQL 마이그레이션 13개) — 크레딧 원장, 멤버십·주문, 가격표·관리자 지표, 즐겨찾기, APIMart 태스크·실제 USD 원가, 支付宝, 유료 커뮤니티 등

**이미지 생성 공급자** (`shared/apimart.js` 실측)
```js
APIMART_MODEL = 'gpt-image-2'
APIMART_API_BASE_URL = 'https://api.apimart.ai'
APIMART_DEFAULT_PRICE_USD = 0.010625   // 장당 약 14~15원
APIMART_MAX_PROMPT_LENGTH = 10_000
// 비동기: 작업 제출 → task_id → 폴링 또는 웹훅
```

**실제 가격표** (마이그레이션 실측)

| 상품 | 크레딧 | 가격 |
|---|---|---|
| pack_300 | 300 | **$5.00** |
| pack_3000 | 3,000 | **$39.00** |
| Starter 멤버십 | 700/월 | — |
| Creator 멤버십 | 1,800/월 | — |
| Studio 멤버십 | 5,200/월 | — |
| 유료 단톡방 (支付宝) | 입장권 | **¥9.90** |

**품질 관리 흔적** — `npm test` 40개 통과 / `npm run test:apimart` 24개 통과 / `design-qa.md` 106줄(뷰포트별 실측 + 프롬프트·이미지 해시 대조) / GitHub Actions 태그 배포 / GA4 OAuth 리포팅 259줄

---

## 4. 설치 및 사용법

| 목적 | 설치 필요? | 소요 | 난이도 |
|---|---|---|---|
| A. 프롬프트만 보고 쓰기 | **불필요** | 0분 | ⭐ |
| B. 클로드/Codex 스킬로 쓰기 | 명령어 1줄 | 1분 | ⭐⭐ |
| C. 웹사이트 전체 운영 | 환경변수 10개+ | 2~5시간 | ⭐⭐⭐⭐⭐ |

### A. 설치 없이 바로 쓰기 (가장 추천)
1. `docs/gallery.md`에서 카테고리 선택
2. 비슷한 이미지 찾아 아래 ```text 블록 프롬프트 복사
3. 주제 단어만 교체 → ChatGPT·Claude·Gemini에 붙여넣기

이미지(159MB) 제외하고 문서만 받기:
```bash
git clone --filter=blob:none --no-checkout https://github.com/bmshin94/awesome-gpt-image-2
cd awesome-gpt-image-2
git sparse-checkout init --cone
git sparse-checkout set docs agents data/style-library.json
git checkout main
```

### B. 에이전트 스킬 설치

**B-1. Claude Code 플러그인 마켓플레이스 (가장 깔끔)**
```
/plugin marketplace add bmshin94/awesome-gpt-image-2
/plugin install gpt-image-2-style-library@awesome-gpt-image-2
```
> README는 `freestylefly/...`를 가리킨다. 내 포크를 쓰려면 `bmshin94`로 교체.

**B-2. skills CLI**
```bash
npx skills add bmshin94/awesome-gpt-image-2 \
  --skill gpt-image-2-style-library \
  --agent claude-code codex --global --yes --copy

npx skills add bmshin94/awesome-gpt-image-2 --global --all --copy
```

**B-3. npm CLI**
```bash
npm install -g gpt-image-2-style-library
gpt-image-2-style-library install all
# 또는
npx gpt-image-2-style-library install all
```

`install all`이 복사하는 경로 (`bin/install.mjs` 실측):
```
~/.claude/skills/gpt-image-2-style-library/    ← Claude Code
~/.codex/skills/gpt-image-2-style-library/     ← Codex
~/.agents/skills/gpt-image-2-style-library/    ← 공용
  (CLAUDE_HOME / CODEX_HOME / AGENTS_HOME 로 변경 가능)
복사 항목: SKILL.md, agents/, assets/, references/
```
> ⚠️ 설치 후 **에이전트 세션 재시작** 필요.

**B-4. GitHub Packages**
```bash
npm login --scope=@freestylefly --registry=https://npm.pkg.github.com
npm install -g @freestylefly/gpt-image-2-style-library --registry=https://npm.pkg.github.com
gpt-image-2-style-library install all
```

**B-5. 소스에서 직접**
```bash
npm install
npm run generate:style-skill   # style-library.json → references/style-library.md
npm run install:skill          # 로컬 스킬 폴더로 복사
```

**사용 예시**
```
"gpt-image-2-style-library로 카페 신메뉴 포스터 프롬프트 만들어줘"
"gpt-image-2-style-library 기준으로 이 프롬프트 개선해줘: [기존 프롬프트]"
```

### C. 웹사이트 로컬 실행
```bash
npm install
cp .env.example .env.local      # ⚠️ SUPER_ADMIN_EMAILS 반드시 교체
npm run dev                      # predev가 cases.json + 스킬 자동 생성
npm run build
npm test                         # 40개
npm run test:apimart             # 24개
```

Supabase 마이그레이션 적용 순서:
```
1. 202605090001_user_credits.sql
2. 20260509090000_membership_billing.sql
3. 20260512090000_google_account_center.sql
4. 20260512143000_pricing_admin_metrics.sql
5. 20260515090000_case_favorites.sql
6. 20260828090000_apimart_generation_tasks.sql
7. 20260721090000_alipay_webpay.sql       (선택)
8. 20260722090000_paid_community.sql      (선택)
```

---

## 5. 플러그인? 스킬? MCP?

### 정답: **"플러그인 껍데기에 담긴 스킬"** — MCP는 아니다.

```
┌─ Claude Code 플러그인 (배포 포장지) ──────┐
│  .claude-plugin/marketplace.json          │
│  ┌─ Agent Skill (실제 내용물) ────────┐   │
│  │  SKILL.md + references/ + assets/  │   │
│  └────────────────────────────────────┘   │
└───────────────────────────────────────────┘
❌ MCP 서버 — 없음
```

| | Skill | Plugin | MCP |
|---|---|---|---|
| 본질 | 지식·지침 문서 | 배포 패키지 | 외부 시스템 연결 프로토콜 |
| 형태 | `SKILL.md` + 참조 파일 | 마켓 매니페스트 | 실행되는 서버 프로세스 |
| 기능 | AI의 **판단** 가이드 | 스킬/명령 **묶음 배송** | AI에게 **새 도구** 제공 |
| 네트워크 | 불필요 | 불필요 | 필요 |
| 이 저장소 | ✅ 있음 | ✅ 있음 | ❌ 없음 |

근거: `SKILL.md`에 `name` + `description` frontmatter(Agent Skill 표준) 존재 / `.claude-plugin/marketplace.json` 존재 / `mcpServers` 설정·`@modelcontextprotocol` 의존성·서버 프로세스 **전부 없음**.

> ⚠️ 혼동 주의: README 후원사 설명의 *"hiapi는 Native Remote MCP 제공"* 문구는 **후원사 상품 설명**이며 이 저장소가 MCP를 제공한다는 뜻이 아니다.

**장점:** 스킬은 텍스트 파일이라 서버 실행·인증·포트 설정이 없다. 설치 1분, 오프라인 작동.

---

## 6. API 토큰이 필요한가?

### 정답: **프롬프트·스킬만 쓰면 토큰 0개.**

| 쓰는 범위 | 필요한 토큰 | 비용 |
|---|---|---|
| 프롬프트 열람·복사 | 없음 | 무료 |
| 에이전트 스킬 사용 | 없음 (기존 클로드 구독만) | 추가 0원 |
| 저장소 코드로 이미지 생성 | APIMart 키 | 장당 ~$0.0106 |
| 웹사이트 전체 운영 | 7종 이상 | 아래 표 |

### `.env.example` 전수 분석

| 환경변수 | 서비스 | 용도 | 필수? |
|---|---|---|---|
| `APIMART_API_KEY` | APIMart | **이미지 생성(핵심)** | 생성 시 필수 |
| `VITE_SUPABASE_URL` | Supabase | DB 주소 (공개 가능) | 필수 |
| `VITE_SUPABASE_ANON_KEY` | Supabase | 익명 키 (공개 가능) | 필수 |
| `SUPABASE_SERVICE_ROLE_KEY` | Supabase | **서버 전용, 절대 노출 금지** | 필수 |
| `SUPER_ADMIN_EMAILS` | — | 관리자 이메일 ⚠️**교체 필수** | 필수 |
| `STRIPE_SECRET_KEY` / `_WEBHOOK_SECRET` | Stripe | 글로벌 결제 | 결제 시 |
| `ALIPAY_*` (5종) | 支付宝 | 중국 결제 | 선택(한국 불필요) |
| `VITE_GA_MEASUREMENT_ID` / `GA4_PROPERTY_ID` | GA4 | 분석 | 선택 |
| `GOOGLE_ANALYTICS_*` (3종) | Google | 지표 리포팅 | 선택 |
| `WATCHA_CLIENT_ID` / `_SECRET` | Watcha | OAuth | 선택 |

**비용:** 100장 ≈ $1.06(1,500원) / 1,000장 ≈ $10.6(15,000원)

### 보안 — 반드시 지킬 3가지
1. **`VITE_` 접두사** = 브라우저 노출. `SUPABASE_SERVICE_ROLE_KEY`에 실수로 `VITE_`를 붙이면 **DB 전체 공개**된다.
2. **`SUPER_ADMIN_EMAILS` 교체** — 현재 `2689458656@qq.com,canghe0818@gmail.com` (원작자). 안 바꾸면 원작자가 내 서비스 최고관리자가 된다.
3. **프롬프트가 제3자 서버를 통과** — APIMart는 중국계 중계 플랫폼. 민감 정보 금지. 필요 시 `shared/apimart.js` 1개 파일만 교체해 OpenAI 공식 API로 전환 가능.

### 토큰 전략
```
Phase 0 → 토큰 0개 (프롬프트 + 스킬만). 비용 0원
Phase 1 → APIMart $5 충전 (약 470장). 배치 테스트
Phase 2 → + Supabase/Vercel 무료 티어 + 토스페이먼츠
Phase 3 → OpenAI 공식 API 직결 + 유료 티어
```

---

## 7. AI 에이전트 구축에 도움이 될까?

### 정답: **도움된다. "프롬프트 자료"보다 "아키텍처 교본"으로 훨씬 더.**

### ① 스킬 작성법의 모범 교본
- **점진적 공개(Progressive Disclosure)**: `SKILL.md` 약 50줄(항상 로드) → `references/` 659줄(필요 시 로드). 컨텍스트 낭비 없이 대용량 지식 처리
- **결정론적 매칭 순서**: "카테고리 → 스타일 → 장면 → 케이스" 순서를 못 박아 재현성 확보
- **구조화된 출력 계약**: 6블록 고정 → 품질 분산 감소
- **불확실성 처리 규칙**: "확신 있으면 진행 / 애매하면 2~3개 선택지 제시"를 명시

### ② 데이터 기반 단일 소스 아키텍처
JSON 1개가 진실의 원천, 나머지는 생성물. 생성 스크립트도 작다 (`generate-style-skill.mjs` 169줄, `generate-site-data.mjs` 189줄). 어떤 도메인(법률 서식, 회계 규정, 사내 디자인 가이드)에든 그대로 재사용 가능.

### ③ 에이전트 호출용 API 설계 패턴
JSON 템플릿 → 필드 단위 채우기, 스키마 검증, 변형 생성, 로깅·재현이 모두 가능. 자연어 프롬프트는 조립·검증이 어렵다.

### ④ 비동기 롱러닝 작업 처리
```
api/generate-image.js       → 작업 제출, task_id 즉시 반환 (3초 내)
api/generation/status.js    → 클라이언트 폴링
api/generation/callback.js  → 웹훅 완료 통보
supabase: apimart_generation_tasks → task_id·상태·원가·만료URL
```
공급자별 상태 문자열을 내부 표준으로 정규화(`in_progress → processing`)해 **공급자 교체 가능** 구조.

### ⑤ 에이전트 과금·크레딧 시스템
```
1. reserveGeneration()       → RPC 'reserve_generation_usage'  크레딧 예약 홀드
2. submitApimartGeneration() → 실제 AI 호출
3-a. 성공 → 확정 차감 + 실제 USD 원가 DB 기록
3-b. 실패 → releaseReservation() → RPC 'release_generation_reservation' 자동 환불
```
에러 코드 매핑:
```
APIMART_RATE_LIMITED      → UPSTREAM_BUSY          → 503
APIMART_API_KEY_INVALID   → SERVER_NOT_CONFIGURED  → 500
APIMART_BALANCE_REQUIRED  → SERVER_NOT_CONFIGURED  → 500
기타                       → GENERATION_FAILED      → 502
```
→ 내부 장애 원인을 노출하지 않으면서 적절한 상태코드 반환. 테스트 40개로 검증됨.

### 도움이 안 되는 부분
LLM 에이전트 프레임워크 ❌ / 멀티에이전트 오케스트레이션 ❌ / RAG·벡터DB ❌ / Function Calling 예제 ❌ / 자율 루프 ❌ / Eval 프레임워크 ❌

→ **"에이전트에 도메인 지식 주입"과 "에이전트 서비스 과금 운영"에 강하고, "에이전트 자체의 추론·행동 설계"에는 자료가 없다.**

### 로드맵
```
단기(오늘)   SKILL.md를 내 도메인용 스킬 템플릿으로 복제
중기(1~2주)  내 도메인 JSON → references 자동 생성 파이프라인 구축
             이미지 배치 생성 스크립트
장기(1~3개월) 스킬 → MCP 서버 확장 (generate_image / review_image 툴)
             api/ + supabase/ 패턴으로 유료 에이전트 서비스
             생성 → 비전모델 검증 → 실패 시 프롬프트 수정 → 재생성 루프
```

---

## 8. React / PHP로 만들 수 있나?

### React — **이미 React로 만들어져 있다**

`package.json` 실측: React 19.2.1 / Vite 7.2.7 / @vitejs/plugin-react / lucide-react / @supabase/supabase-js 2.105.4 / stripe 22.1.1 / alipay-sdk 4.14.0 / @google-analytics/data / google-auth-library

현재 React 코드 약 5,500줄. **할 일은 "만들기"가 아니라 "고치기"**:
```
□ 한국어 i18n 추가 (en/zh/ja → ko)
□ 결제를 토스페이먼츠/포트원으로 교체
□ 支付宝 + 유료 단톡방 코드 제거
□ SUPER_ADMIN_EMAILS 교체
□ 디자인 리브랜딩
□ (선택) Next.js 이전 → SEO 필요 시
```
> 개선 제안: `src/main.jsx` 4,315줄은 단일 파일로 너무 크다. 컴포넌트 분리(Gallery / FilterBar / CaseModal / GenerationPanel / BillingPanel)가 유지보수 1순위.

권장 신규 스택: **Next.js 15 (App Router) + Tailwind + shadcn/ui + Supabase(마이그레이션 13개 재사용) + 포트원·토스 + Vercel/Cloudflare**

### PHP — 가능하며, 한국 시장에선 유리한 면도 있다

백엔드가 복잡한 상태 서버가 아니라 **24개 독립 함수**라 1:1 대응이 쉽다.

| 현재 (Node/Vercel) | PHP 대응 |
|---|---|
| `api/generate-image.js` | `api/generate-image.php` |
| `@supabase/supabase-js` | Supabase REST(Guzzle) 또는 MySQL 교체 |
| `stripe` npm | `stripe/stripe-php` |
| `alipay-sdk` | 토스/포트원 PHP SDK |
| Vercel 서버리스 | Apache/Nginx + PHP-FPM |
| `node --test` | PHPUnit |
| React SPA | Blade(Laravel) 또는 React 유지 |

Laravel 11 예시:
```php
Route::post('/generate-image', [GenerationController::class, 'store']);
Route::get ('/generation/status/{taskId}', [GenerationController::class, 'status']);
Route::post('/generation/callback', [GenerationController::class, 'callback']);

// 크레딧 예약 패턴 (Supabase RPC 대체)
DB::transaction(function () use ($user) {
    $reservation = CreditReservation::create([
        'user_id' => $user->id, 'amount' => 1, 'status' => 'reserved',
    ]);  // 잔액 확인은 SELECT ... FOR UPDATE 로 락
});

GenerateImageJob::dispatch($reservation->id, $prompt);  // Laravel Queue + Horizon
```

**PHP 장점:** 호스팅 월 5천~2만원(카페24/가비아) / 국내 PG PHP 예제 풍부 / PHP·Laravel 인력 풀 넓음 / `max_execution_time` 조정으로 서버리스 10초 제약 없음 / Laravel에 큐·스케줄러·인증·관리자(Filament) 내장

**PHP 단점:** Node 백엔드 약 3,000줄 재작성 / PL/pgSQL RPC 13개를 Laravel 마이그레이션으로 재작성 / WebSocket은 Node 유리

### 최종 권장
| 상황 | 권장 |
|---|---|
| 빠르게 띄우기 | 현재 React 포크 → 결제·언어만 교체 (1~2주) |
| SEO·마케팅 중요 | Next.js 재작성 |
| 비용 최소화 + 국내 PG | Laravel 백엔드 + 기존 React 프론트 유지 (하이브리드) |
| PHP 팀 보유 | Laravel 전면 이전 |

> **가장 현실적인 답: 백엔드만 선택하고 프론트엔드는 기존 React 재사용.** 5,500줄 UI를 다시 쓰는 건 낭비다. API 응답 형태만 맞추면 프론트엔드는 그대로 돈다.

---

## 9. 유튜브 강의 영상 제작 가능성

### 정답: 가능하며 소재로 좋다. **저작권 경계만 지키면 된다.**

### 왜 좋은 소재인가
1. 547장 이미지 = 썸네일·b-roll 소재. "프롬프트 → 이미지" 비포애프터는 시청 유지율이 높다
2. 즉시 재현 가능 → 시청자 실행률·저장률 높음
3. **한국어 콘텐츠 공백** (README에 한국어 없음, 경쟁자 사실상 없음)
4. 난이도 스펙트럼이 넓어 시리즈 확장성 있음
5. "케이스 541개" 숫자 자체가 클릭을 유도

### 저작권 경계

저장소 원문 경고: *"This repository does not guarantee that third-party content can be used commercially."* / 출처는 **YouMind, OpenNana** 등 커뮤니티.

**🟢 안전**
- 저장소 소개·리뷰 / 구조·방법론 해설 / 코드 설명(MIT) / 프롬프트 일부 인용 + 출처 표기 / 참고해서 **내가 직접 생성한 이미지** / **내가 새로 쓴 한국어 프롬프트** / 설치·사용법 실연

**🔴 위험**
- 541개 프롬프트를 PDF로 묶어 유료 판매 / 저장소 이미지 무출처 도배 / "제가 만든 프롬프트 541개" 표시 / 중국어 프롬프트 전문을 자막으로 전부 노출 / 저장소 이미지를 썸네일로 사용

**✅ 추천 구성 — "방법론 중심 + 내 실연"**
```
1. 저장소 소개 (화면 녹화, 출처 명시)        2분
2. 원리 설명 (6블록 구조, 避坑指南 핵심)      5분
3. 【내가 직접】 한국어 프롬프트 작성 실연     8분
4. 【내가 생성한】 결과물 공개                3분
5. 저장소 링크 제공 → "직접 보세요"           1분
→ 자료는 '참고 문헌', 콘텐츠 본체는 '내 실연'
```

### 8편 시리즈 기획안

| # | 제목 | 길이 | 타겟 | 성과 |
|---|---|---|---|---|
| 1 | AI 이미지 프롬프트 541개 무료 저장소 (전체 투어) | 12분 | 전체 | 조회수 |
| 2 | 글자 깨짐 끝내는 7가지 규칙 — 避坑指南 완전 해설 | 15분 | 실무자 | **저장률 최고** |
| 3 | 프롬프트를 "코드"로 쓰는 법 — JSON 템플릿 실전 | 18분 | 개발자 | 구독 전환 |
| 4 | 클로드 코드에 스킬 설치 — 프롬프트 자동 작성 | 14분 | 클로드 유저 | 구독 전환 |
| 5 | 한글 포스터가 깨지는 이유와 해결책 (한국 특화) | 12분 | 🇰🇷 전용 | 검색 유입 |
| 6 | 이미지 100장 배치 생성 자동화 (코드 실습) | 20분 | 개발자 | 강의 리드 |
| 7 | AI 이미지 서비스 수익 구조 분석 — 크레딧 과금 해부 | 22분 | 창업자 | **고단가 리드** |
| 8 | 541케이스를 내 업종에 적용하기 | 16분 | 소상공인 | 컨설팅 리드 |

**가장 먼저 만들 것: 2번(避坑指南)** — 저장·공유가 많이 나오는 유형(알고리즘 선호), 저작권 위험 거의 없음, 한국어 경쟁자 없음, 제작 난이도 낮음.

### 기대치 (냉정하게)
| 항목 | 예상 |
|---|---|
| 주제 수요 | 중상 |
| 경쟁 (한국어) | 낮음 |
| 제작 난이도 | 낮음 |
| **직접 수익(애드센스)** | ⭐⭐ 낮음 (니치) |
| **간접 수익(강의·컨설팅·전자책)** | ⭐⭐⭐⭐⭐ 높음 |

> **전략: 유튜브를 "광고 수익원"이 아니라 "유입 깔때기"로 쓴다.**
> 유튜브(무료, 신뢰) → 한국어 템플릿 무료 배포(이메일 수집) → 유료 강의·전자책·컨설팅·SaaS 구독(실제 수익)

---

## 10. 수익화 아이디어 (상세)

### 원작자의 현재 수익 구조 (실측)

| 수익원 | 가격 | 근거 |
|---|---|---|
| 크레딧 팩 | $5 / 300 | `20260512143000_pricing_admin_metrics.sql` |
| 크레딧 팩(대) | $39 / 3,000 | 동일 |
| 멤버십 3단계 | 700 / 1,800 / 5,200 크레딧·월 | `20260509090000_membership_billing.sql` |
| 유료 단톡방 | ¥9.90 (支付宝) | `20260722090000_paid_community.sql` |
| 후원사 어필리에이트 | 5곳 (`?aff=`) | `README.md` |
| GitHub Sponsors | — | `.github/FUNDING.yml` |

**마진 계산**
```
원가 장당 $0.010625
300 크레딧 = $5.00  → 장당 판매가 $0.01667 → 마진율 약 36%
3,000 크레딧 = $39  → 장당 $0.013        → 마진율 약 18%
```
→ **순수 "이미지 생성 대행"은 원가 압박이 큰 사업.** 그대로 복제하면 같은 문제를 겪는다. 아래 아이디어는 "장당 과금"에서 벗어나는 방향에 집중한다.

### 🏆 Tier 1 — 가장 유망

#### ① 수직 특화 SaaS — 업종별 이미지 자동 생성기
| 타겟 | 해결할 반복 작업 | 가격 |
|---|---|---|
| 스마트스토어 셀러 | 상품 상세페이지 이미지 10종 세트 | 월 49,000원 |
| 부동산 중개 | 매물 홍보 카드뉴스 | 월 39,000원 |
| 요식업 | 메뉴판·배달앱 썸네일·인스타 피드 | 월 29,000원 |
| 강사·교육 | 강의 썸네일·교재 인포그래픽 | 월 39,000원 |
| 1인 기업 | 블로그 썸네일 월 30장 | 월 19,000원 |

```
❌ "프롬프트 541개 보여드립니다"            → 사용자가 직접 골라야 함 = 가치 체감 낮음
✅ "상품명만 넣으면 상세페이지 10장 나옵니다" → 결과를 바로 받음 = 가치 체감 높음
```
- **저작권 안전성 ⭐⭐⭐⭐⭐** — 업종 프롬프트를 내가 새로 작성. 가져오는 건 방법론(저작권 대상 아님) + MIT 코드
- **난이도 ⭐⭐⭐⭐** 이지만 설계도가 이미 있어 0에서 3~4개월 → **3~4주**
- 손익(100명 × 49,000원): MRR 490만원, 원가 약 20만원 → **마진율 약 96%** (장당 과금 36%와 구조가 다름)

#### ② 교육 콘텐츠 패키지 (가장 빠른 현금화)
```
1단계 무료: 유튜브 8편 시리즈 → 신뢰 + 이메일 수집
2단계 저가: 한국어 프롬프트 템플릿 팩 19,000~39,000원 (⚠️ 내가 새로 작성)
3단계 중가: 온라인 강의 89,000~149,000원 (인프런/클래스101/탈잉)
4단계 고가: 기업 출강·컨설팅 회당 100~300만원
5단계 구독: 멤버십 커뮤니티 월 9,900~19,900원
```
개발 없이 **2~4주 내 첫 매출** 가능. ①을 만드는 동안의 현금 흐름 + ①의 고객 모집 채널. → **①과 ②를 동시에 진행하는 것이 최적.**

#### ③ 에이전트 스킬 / MCP 생태계 B2B
```
현재: 스킬이 "프롬프트 텍스트"만 제공 → 사람이 수동 생성
확장: MCP 서버로 툴 제공 → AI가 직접 생성·검증·재시도
  ├─ search_cases(query)       541케이스 의미 검색
  ├─ get_template(category)    템플릿 + 避坑指南
  ├─ build_prompt(intent)      6블록 조립
  ├─ generate_image(prompt)    실제 생성
  └─ review_image(url, intent) 비전모델 검증 → 실패 시 수정 후 재생성
```
| 모델 | 가격 |
|---|---|
| MCP 서버 구독 | 월 $19~49 |
| 기업 커스텀 스킬 납품 | 300~1,000만원 |
| 스킬 제작 템플릿 판매 | $49~199 |

**저작권 위험 없음** (전부 내 코드). 경쟁자 적고 기업 단가 높다.

### 🥈 Tier 2 — 조건부 유망

**④ 한국어 로컬라이즈 + 자체 갤러리** — React 코드 그대로 한국어화(1~2주), SEO 자산화. ⚠️ 저장소 이미지·프롬프트 전재는 위험 → **저장소는 "참고 색인"으로만, 갤러리는 내가 생성한 한국어 케이스로 새로 채우기.**

**⑤ 프롬프트 품질 검증·자동 개선 도구** — 避坑指南을 규칙 엔진으로 코드화:
```
입력: "멋진 앱 화면 만들어줘"
⚠️ 플랫폼 미지정 / 비율 미지정 / 텍스트 제약 없음 / 네거티브 없음
→ 6블록 구조로 재작성된 프롬프트 + 개선 근거
```
원본에 없는 기능. 월 9,900~29,000원 SaaS.

**⑥ 배치 생성 대행** — 쇼핑몰 1,000개 썸네일 / 출판 삽화 / 교재. 원가 15원 → 판매 100~300원 = **마진 85%+**. `api/generation/*` 비동기 패턴 재사용.

### 🥉 Tier 3 — 보조

**⑦ GPTs / Claude Projects 배포** (난이도 ⭐, 유입 채널·포트폴리오)
**⑧ Figma / Canva 플러그인** (난이도 ⭐⭐⭐⭐, 마켓이 결제 처리)
**⑨ 오픈소스 스폰서십** — 원본에 한국어 README·한국 케이스 PR 기여 → 공동 유지보수자 → ①②③의 신뢰 기반
**⑩ 노션 템플릿 / 사내 지식베이스 패키지** (19,000~49,000원, 진입 가장 쉬움)

### ⛔ 하면 안 되는 것

| 금지 | 이유 |
|---|---|
| 541개 프롬프트 재판매(PDF/강의자료) | 제3자 저작물, 상업적 사용 미보장 명시 |
| 저장소 이미지로 유료 상품 제작 | 원작자 이미지 |
| "제가 만든 프롬프트" 표시 | 허위 표시 |
| 원본 사이트 클론 후 과금 | 동일 모델 + 콘텐츠 권리 없음 |
| `SUPER_ADMIN_EMAILS` 미교체 배포 | 원작자가 최고관리자가 됨 |
| 어필리에이트 링크 미공개 삽입 | 표시광고법·공정위 추천보증 심사지침 위반 소지 |

### 🎯 단계별 실행 전략
```
Phase 1 (1~4주, 투자 0원)
  ② 유튜브 2편 (避坑指南 + 스킬 설치 실연)
  ⑨ 원본에 한국어 README PR 기여
  → 신뢰 + 이메일 리스트 + 시장 반응 측정
        ↓
Phase 2 (1~2개월, 투자 ~50만원)
  ② 한국어 템플릿 팩 판매 (첫 현금)
  ⑤ 프롬프트 검증 도구 MVP (무료 → 리드 수집)
  → 첫 매출 + 돈 쓰는 업종 식별
        ↓
Phase 3 (3~6개월, 본게임)
  ① 수직 특화 SaaS (api/ + supabase/ 재사용, 검증된 업종 1개 집중)
  ③ MCP 서버 확장 + 기업 커스텀 납품
  → MRR 500만원 목표 (유료 100명 × 49,000원)
```

**순서의 이유**
1. ②를 먼저 — 개발 없이 시장 반응 확인. SaaS 3개월 만들고 수요 없으면 최악
2. ①은 업종 확정 후 — "범용 프롬프트 사이트"는 가치 전달이 약함
3. ③은 ②의 부산물 — 7번 영상(과금 아키텍처)이 기업 리드를 만든다

> **가장 중요한 한 가지**
> 이 저장소의 진짜 수익 자산은 **"프롬프트 541개"가 아니라 "크레딧 과금 아키텍처"**다.
> 프롬프트는 남의 것이고 복제도 쉽고 저작권 위험이 있다. 하지만 **"AI 서비스를 월 구독으로 과금하는 검증된 코드"는 MIT로 완전히 내 것**이 된다.
> 이걸 **어떤 도메인에 붙이느냐**가 수익의 크기를 결정한다. 이미지 생성이 아니어도 된다 — 같은 뼈대로 AI 글쓰기·번역·영상 요약 서비스를 만들 수 있다.

---

## 11. 반드시 알아야 할 제약 (종합)

| # | 제약 | 상세 |
|---|---|---|
| 1 | **한국어 미지원** | README 영/중/일만. 케이스 프롬프트 다수가 중국어 |
| 2 | **한글 텍스트 취약** | GPT-Image2는 중국어·영어 대비 한글이 약함. 한글 포스터는 추가 검증 필수 |
| 3 | **저작권 경고 명시** | *"상업적 사용 보장하지 않음"*. **MIT는 코드에만** 적용, 프롬프트·이미지는 별개 |
| 4 | **후원 링크 전부 어필리에이트** | APIMart/hiapi/PackyCode/PPToken/Liqiu 모두 `?aff=`. 가격·성능은 직접 검증 |
| 5 | **중국 시장 종속** | 支付宝, 위챗 공식계정, ¥9.90 단톡방, 샤오홍슈 출처 |
| 6 | **하드코딩된 운영자 정보** | `SUPER_ADMIN_EMAILS`에 원작자 이메일 — 포크 시 **반드시 교체** |
| 7 | **생성이 OpenAI 직접 아님** | APIMart 중계 경유 → 민감 프롬프트 주의 |
| 8 | **용량 부담** | 393MB (이미지 159MB). 클론 느림 |
| 9 | **문서/구현 불일치** | 배지 544 vs 실제 541 |
| 10 | **포크 경로 문제** | README 설치 명령이 모두 `freestylefly/...` → 내 포크 쓰려면 교체 |
| 11 | **거대 단일 파일** | `src/main.jsx` 4,315줄 → 컴포넌트 분리 필요 |

---

## 12. 가치 등급 요약

| 레이어 | 등급 | 이유 |
|---|---|---|
| 🟥 상용 SaaS 소스 (`api/` + `supabase/`) | ⭐⭐⭐⭐⭐ | 2~3개월치 설계가 MIT로 공개 |
| 🟨 에이전트 스킬 구조 | ⭐⭐⭐⭐⭐ | 즉시 효용 + 스킬 작성법 교본 |
| 🟩 템플릿 + 避坑指南 | ⭐⭐⭐⭐ | 시간 절약 직접적 (중국어 비중 높음) |
| 🟦 541 케이스 갤러리 | ⭐⭐⭐ | 참고용 우수 (저작권·한국어 제약) |
| ⬜ 중국 결제/커뮤니티 | ⭐ | 한국에선 교체 대상 |

> **결론:** 1순위 가치는 "프롬프트 541개"가 아니라
> **"AI 이미지 서비스를 크레딧 과금으로 운영하는 방법의 완성된 교본" + "클로드 코드용 스킬 즉시 사용"** 이다.

---

## 13. 체크리스트 (바로 실행용)

### 오늘 할 일
```
□ docs/gallery.md 열어 내 업종과 가까운 카테고리 훑기
□ docs/templates.md 의 避坑指南 섹션 전부 읽기 (가장 투자 효율 높음)
□ Claude Code에 스킬 설치
   /plugin marketplace add bmshin94/awesome-gpt-image-2
   /plugin install gpt-image-2-style-library@awesome-gpt-image-2
□ "gpt-image-2-style-library로 ○○ 프롬프트 만들어줘" 로 실제 작동 확인
```

### 이번 주
```
□ SKILL.md 구조를 내 도메인 스킬 템플릿으로 복제
□ api/generate-image.js 의 크레딧 예약 패턴 코드 정독
□ 유튜브 2번 영상(避坑指南) 스크립트 초안
```

### 포크해서 서비스화할 때 (필수 안전 점검)
```
□ SUPER_ADMIN_EMAILS 를 내 이메일로 교체          ← 최우선
□ SUPABASE_SERVICE_ROLE_KEY 에 VITE_ 접두사 없는지 확인
□ 支付宝 / 유료 단톡방 코드 제거
□ 결제를 토스페이먼츠 / 포트원으로 교체
□ 어필리에이트 링크 제거 또는 공개 표기
□ 저장소 프롬프트·이미지 직접 전재 여부 점검 (저작권)
□ ko 로케일 추가
```

---

## 14. 조사 근거 (실측 파일 목록)

| 결론 | 근거 파일 |
|---|---|
| 케이스 541개, 카테고리 분포 | `data/cases.json` |
| 템플릿 22개, 스타일 19, 장면 10, 카테고리 13 | `data/style-library.json` |
| 스킬 6단계 워크플로우 | `agents/skills/gpt-image-2-style-library/SKILL.md` |
| 스킬 설치 경로 | `agents/skills/gpt-image-2-style-library/bin/install.mjs` |
| 플러그인 매니페스트 v1.0.4 | `.claude-plugin/marketplace.json` |
| 환경변수 전체 | `.env.example` |
| 생성 단가 $0.010625, 모델 `gpt-image-2` | `shared/apimart.js` |
| 크레딧 예약·환불 패턴, 에러 매핑 | `api/generate-image.js` |
| 비동기 폴링·웹훅 | `api/generation/status.js`, `api/generation/callback.js` |
| 가격표 ($5/300, $39/3000, 멤버십 3단) | `supabase/migrations/20260512143000_pricing_admin_metrics.sql` |
| 유료 단톡방 ¥9.90 | `supabase/migrations/20260722090000_paid_community.sql`, `docs/paid-community.md` |
| 테스트 40 + 24 | `package.json`, `api/_lib/*.test.js`, `design-qa.md` |
| 避坑指南 원문 | `docs/templates.md` |
| 저작권 경고 | `README.md` (Disclaimer), `docs/disclaimer.md` |
| 후원사 어필리에이트 | `README.md` (Sponsors) |
| React 19 / Vite 7 스택 | `package.json` |
| 스킬 자동 배포 | `.github/workflows/publish-style-skill.yml` |

---

*전수조사·작성: Claude Code 세션 (2026-10-08) · 대상 저장소: https://github.com/bmshin94/awesome-gpt-image-2*
