# 버전 기록

판단 기준이 바뀐 것을 버전으로 묶어 적습니다. 새 문서가 생기거나 판정이 달라질 만큼 바뀌면 버전을 올리고, 그 사이의 보완은 지금 버전에 더합니다. 문장 손질과 오타 수정은 적지 않습니다. 최근 3개 버전은 README의 "최근 바뀐 것"에 표로 요약합니다.

템플릿으로 복사한 저장소는 원본을 따라 바뀌지 않습니다. 플러그인도 판정을 마친 뒤 `starter/`를 앱 폴더에 복사하므로 그때의 기준으로 고정됩니다. 이미 만든 앱은 [`DECISION.md`](starter/templates/DECISION.md)의 "참고한 저장소 주소와 버전"에 적은 번호의 앞 두 자리와 같은 절부터 봅니다(1.2.1이면 1.2 절부터). 보완할 때는 `plugin.json`의 끝자리만 올리고 CHANGELOG에는 따로 절을 두지 않기 때문입니다. 반영할 곳을 찾을 때는 AI에게 "원본 저장소의 CHANGELOG를 보고 내 [`DECISION.md`](starter/templates/DECISION.md)에 반영할 곳을 찾아 줘"라고 부탁합니다.

## 1.2 에이전트 브라우저로 정부 업무 시스템 동기화 (2026.09)

- **새 문서 [`starter/assess/screen-agent.md`](starter/assess/screen-agent.md)**: Aside 같은 에이전트 브라우저로 정부 업무 시스템(희망이음 등)과 기관 앱·시트를 동기화할 때 적용합니다. 쓰기 전 확인(운영 기관 약관, 위수탁 협약, DPA와 동의, 개인 구독 금지, 계정·인증), 원본 정하기, 운영 순서(동작 확인, 대조만, 소량 시험, 확대), 지시문에 넣을 것, Aside 설정의 주의점을 담았습니다. 공개 사례가 없어 사용법이 아니라 주의점으로 적었습니다.
- **[`masking.md`](starter/requirements/masking.md)**: AI 전송 제외 대상을 정부 업무 시스템(희망이음 등)에서 받은 자료로 정리하고, 에이전트 브라우저로 화면을 읽는 것도 같은 확인을 거치게 했습니다. 추론 위치 표를 2026-09-30 기준으로 고쳤습니다. 업체의 자체 API로는 한국 안에서만 추론할 수 없지만, Bedrock 서울의 Claude Opus 5·Sonnet 5처럼 클라우드를 거치는 일부 모델은 가능합니다. 옛 장애등급(1~6급)은 장애 정도로 적습니다.
- **[`requirements.md`](starter/requirements/requirements.md), [`gas.md`](starter/rules/gas.md)**: 웹훅 요건을 더했습니다. payload에는 ID만 싣고, HMAC 서명을 검증하고(Standard Webhooks), 이벤트 ID로 멱등 처리합니다. GAS `doPost(e)`는 헤더를 읽지 못하므로 서명은 Cloudflare Workers에서 검증합니다. 접속기록은 2026년 11월 1일부터 개인정보처리시스템에 접속한 모든 사람(정보주체 제외)이 대상이고, 점검 주기는 내부 관리계획에서 정합니다.
- **[`design.md`](starter/requirements/design.md)**: 화면을 읽는 AI 에이전트에 대비해 서버 검증, 재확인 단계, 접근 로그를 둡니다.
- **이미 만든 앱**: 에이전트 브라우저를 쓰면 원본, 운영 기관 약관·위수탁 협약 확인 결과, 사람이 누르는 버튼(저장, 제출, 결재 요청), 작업 로그 위치를 [`DECISION.md`](starter/templates/DECISION.md)에 적습니다. 웹훅을 쓰면 payload에 개인정보가 없는지 확인합니다. 접속기록에 기관 관리자와 수탁자의 접속도 남는지, 점검 주기가 내부 관리계획에 있는지 확인합니다. 협약의 국외 반출 제한 때문에 AI 기능을 뺐다면 [`masking.md`](starter/requirements/masking.md)의 추론 위치 표를 다시 봅니다.

## 1.1 보호 기준 강화, 운영하고 있는 앱에 반영하는 일은 사람이 승인 (2026.09)

- **데이터 등급([`workflow.md`](starter/workflow.md))**: S등급에 생체정보와 주민등록번호를 넣고, 만 14세 미만 아동의 정보에는 법정대리인 동의가 필요합니다. 학대 이력과 가족 관계는 민감정보에 준해 보호합니다. 민감정보가 있는 작은 앱의 경로 세 가지와 구글 시트에 S등급을 둘 때의 조건을 정했습니다.
- **동의([`ops/consent-notes.md`](ops/consent-notes.md), [`ops/consent-form-intake.md`](ops/consent-form-intake.md))**: 클라우드 보관은 처리방침 공개(국외 처리위탁)로, AI API 전송은 국외이전 동의로 나눴습니다. 동의서 참고 양식에 AI 처리 항목과 거부 시 대체 처리를 넣었습니다.
- **AI 기능([`ai.md`](starter/requirements/ai.md))**: 통계를 말로 묻는 기능은 AI 도구에 집계 함수만 노출하고 숫자만 받습니다.
- **운영하고 있는 앱에 반영([`agentic.md`](starter/rules/agentic.md))**: 운영하고 있는 앱에 반영하는 일과 DB를 바꾸는 일은 사람이 승인하고 AI가 실행합니다. `.claude/settings.json`에 확인 규칙을 둡니다.
- **맨 앞 요약**: [`workflow.md`](starter/workflow.md) 맨 앞에 "꼭 지킬 것"을, [`DECISION.md`](starter/templates/DECISION.md) 맨 앞에 "기관의 실천 원칙"을 두었습니다.
- **이미 만든 앱**: 동의서를 [`ops/consent-form-intake.md`](ops/consent-form-intake.md)와 비교하고, `.claude/settings.json` 확인 규칙이 없으면 넣고, [`DECISION.md`](starter/templates/DECISION.md) 맨 앞에 실천 원칙을 적습니다.

## 1.0 템플릿·플러그인·채팅 (2026.09)

- **사용법**: 같은 문서를 템플릿(Use this template), 플러그인, 채팅([`starter/chat-prompt.md`](starter/chat-prompt.md))의 세 가지로 씁니다.
- **새 문서**: [`form-to-app.md`](starter/assess/form-to-app.md)(HWP 양식에서 앱까지), [`ai.md`](starter/requirements/ai.md)(AI 기능 요건), [`agent.md`](starter/assess/agent.md)(Slack 봇 등 기관 공용 AI). [`design.md`](starter/requirements/design.md)에 부르는 말과 이름 기준을 더했습니다.

## 1.0 이전 (2026.08~09)

[`workflow.md`](starter/workflow.md) 판단 절차, [`form-audit.md`](starter/assess/form-audit.md), [`ssot.md`](starter/data/ssot.md), [`record-integrity.md`](starter/data/record-integrity.md)(보관 등급), [`levels.md`](starter/data/levels.md)(데이터 관리 다섯 단계), [`ethics.md`](starter/assess/ethics.md), [`design.md`](starter/requirements/design.md), [`print.md`](starter/requirements/print.md), [`masking.md`](starter/requirements/masking.md)를 차례로 두었습니다. 자세한 내용은 커밋 이력에 있습니다.
