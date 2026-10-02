# Project Analysis — Final ZIP

## Analysis basis

- Uploaded file: `mlo-02-p1-team3-main(1).zip`
- ZIP commit marker: `89c155f0eff166fd41546e5422e1c31aee85bd3a`
- SHA-256: `8a4fd98d603c8122677c585ae44731662104e431a7860303f37d06e7ee0fdc31`
- Archive entries: 248
- Extracted project files: 218

This report was produced by inspecting the final ZIP, not by relying on the README alone.

---

## 1. Project structure found

```text
config/                 Django settings / URLs / WSGI-ASGI
frontend/               app code
  templates/
    frontend/            final signed-in service screens
    pages/               auth/opening and legacy templates
  static/assets/
    css/                 shared/page/chat/recommend styles
    js/                  page interactions and API calls
    images/              character/dragon/room/sports assets
    audio/               room BGM assets
  auth_views.py          account + app APIs
  chatbot_views.py       chatbot HTTP endpoint
  chatbot_service.py     team AI service logic
  recommendation_service.py team recommendation/service logic
pipeline/                scheduler and pipeline runner
docs/                    README evidence, screenshots, diagrams, slides
```

### Frontend files inspected

Final service templates:
- `frontend/templates/frontend/base.html`
- `home.html`
- `recommend.html`
- `profile.html`
- `friends.html`
- `friend_visitor.html`
- `diary.html`

Primary JS:
- `api.js`
- `app.js`
- `chatbot.js`
- `home.js`
- `recommend.js`
- `profile.js`
- `friends.js`
- `dragon_character.js`

Primary CSS:
- `base.css`
- `mini_home.css`
- `character_theme.css`
- `chatbot.css`
- `forms.css`
- `sport_picker.css`
- `recommend.css`

---

## 2. Actual service flow confirmed from code

### Server-rendered shell
`base.html` receives member/session information in `data-*` attributes and renders profile summary, navigation, source ribbon, and AI coach shell.

### Recommendation UI
`recommend.js` confirms the actual browser flow:

1. profile values prefill form
2. region/current-location mode switching
3. browser Geolocation API
4. GET `/nearby-facilities-data/`
5. render score/reasons/operation notice
6. detail dialog with score breakdown/environment/safety
7. POST `/api/selected-recommendation/`
8. Kakao Map navigation

### AI coach UI
`chatbot.js` confirms:

- movable NPC dock
- persisted dock location with localStorage
- dynamic panel positioning
- safe assistant-text formatting
- message/typing UI
- recommendation cards inside chat
- POST `/api/chatbot/`
- POST `/api/chatbot/clear/`

### HOME interaction
`home.js` confirms:

- room state loading/saving
- item layout persistence
- workout progress rendering
- reset/undo actions
- quick recommendation fetch
- friend note fetch/write

---

## 3. Contribution evidence

### Explicit README evidence
Final README records:

- 신경호 → `프론트엔드 · 발표자료`
- 담당 → `서비스 화면 구현, 사용자 인터페이스 구성, 발표자료 준비`
- WBS step 8 Frontend → `신경호·류지예`
- WBS step 10 AI chatbot → `김형준·프론트엔드`

### What the ZIP can and cannot prove

The ZIP contains the final state but **does not include `.git` history**, so it cannot prove which individual authored each line.

Therefore this portfolio uses:

- **Frontend 공동 담당** where final README says both frontend members owned the area
- **My frontend focus** for concrete UI/integration areas the portfolio owner can explain and has worked on
- **Team implementation** for Backend/Data/AI server logic

This is intentionally more conservative than claiming entire files as sole authorship.

---

## 4. Strong portfolio points found

### A. Explainable recommendation UI
The frontend exposes score reasons and raw environment/safety evidence instead of only showing a ranking.

### B. Defensive UI states
Location permission, timeout, API failure, zero results, and storage failure have explicit user-facing states.

### C. Safe rendering
`recommend.js` escapes server-derived strings. `chatbot.js` escapes assistant content before applying limited bold/newline formatting.

### D. Real integration details
The code contains implementation decisions that are good interview material, such as opening a blank map tab before async selection storage to avoid popup blocking.

### E. Character-driven service identity
The room, avatar, dragon/coach, rewards, music, and friend interactions form a consistent visual/product concept rather than unrelated pages.

### F. Data provenance UI
The final common shell visibly links KSPO, DATA.GO.KR, Culture Data, KMA, and AirKorea.

---

## 5. Technical debt / improvement opportunities found

### Frontend architecture
- large `home.js` and large CSS files
- DOM/state/API concerns mixed in page scripts
- global `window.USIMUNKKA`
- localStorage and server state coexist without a formal state layer

### Legacy/duplication
- both `templates/frontend/` and `templates/pages/` exist
- `views.py` retains legacy compatibility routes/templates
- route history makes ownership harder to understand

### Test coverage
- project includes server-side tests but no clear automated browser E2E suite for the key UI flows

### Accessibility
- ARIA labels are present in many areas, which is positive
- focus trapping, reduced motion, full keyboard matrix, and automated accessibility verification could be stronger

### Recommendation UX
- data freshness/confidence is not consistently visible to the user
- travel time remains an estimate rather than route-engine time

---

## 6. Validation performed

- `python -m compileall -q config frontend pipeline` → PASS
- `node --check` on all project JS files → PASS
- secret literal scan → no real API key/DB URL/token literal found

These checks validate syntax/security hygiene of the snapshot, not full runtime behavior against external APIs or the production database.
