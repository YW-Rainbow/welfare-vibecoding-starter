# 버전 기록

판단 기준이 바뀐 것을 버전으로 묶어 적습니다. 새 판단 문서가 생기거나 판정이 달라질 만큼 바뀌면 버전을 올리고, 그 사이의 보완은 지금 버전에 더합니다. 문장 손질과 오타 수정은 적지 않습니다. 최근 3개 버전은 README의 "최근 바뀐 것"에 표로 요약합니다.

템플릿으로 복사한 저장소는 원본을 따라 바뀌지 않습니다. 플러그인도 판정을 마친 뒤 `starter/`를 앱 폴더에 복사하므로 그때의 기준으로 고정됩니다. 이미 만든 앱은 [`DECISION.md`](starter/templates/DECISION.md)의 "참고한 저장소 주소와 버전"에 적은 번호의 앞 두 자리와 같은 절부터 봅니다(1.2.1이면 1.2 절부터). 보완할 때는 `plugin.json`의 끝자리만 올리고 CHANGELOG에는 따로 절을 두지 않기 때문입니다. 반영할 곳을 찾을 때는 AI에게 "원본 저장소의 CHANGELOG를 보고 내 [`DECISION.md`](starter/templates/DECISION.md)에 반영할 곳을 찾아 줘"라고 부탁합니다.

## 1.4 AI로 보내는 기록의 국외이전 근거 정정 (2026.10)

- **국외이전 근거([`consent-notes.md`](ops/consent-notes.md) 1절)**: "AI 분석을 위한 전송은 국외이전 동의를 받아야 한다"는 틀렸습니다. 개인정보 보호법 제28조의8은 보관과 AI 처리를 나누지 않습니다. 업체가 입력을 학습에 쓰지 않고 계약이 있는 이용자와 직원의 정보를 그 서비스를 위해 맡긴다면, 클라우드 보관과 같이 처리방침 공개(제1항 제3호)로 됩니다. 학습에 쓰는 업체에 주면 위탁이 아니라 제3자 제공이라 동의가 필요합니다(대법원 2016도13263). 국외이전 동의(제1호)는 설문 응답자처럼 기관과 계약이 없는 사람의 정보에만 받습니다. "거부를 들어줄 수 있으면 동의로 받는다"는 기준은 법에 없어서 뺐습니다. 제3호로 처리해도 거부 방법과 효과는 알려야 합니다(제2항 제5호). 이 규칙은 `consent-notes.md` 1절에만 자세히 적고, 다른 문서에는 결론과 링크만 둡니다.
- **동의서 양식([`consent-form-intake.md`](ops/consent-form-intake.md), [`consent-form-sample.md`](ops/consent-form-sample.md))**: AI 국외이전 동의 항목을 뺐습니다. 국외 처리 사실과 거부 방법은 안내로 알립니다. 한 장 양식은 ⑥ 안내 사항이 ⑤가 되었고 그 안에 "AI 처리" 항목을 넣었습니다. 별도 양식은 ① AI 활용 안내에 넣었고, ④ 민감정보가 ③이 되었습니다. 처리방침 예시도 제3호 하나로 고쳤습니다.
- **서버 확인([`masking.md`](starter/requirements/masking.md))**: 명부 필드 `동의_AI분석`을 `AI처리_가능`으로 바꿨습니다. 이용자가 AI 처리를 거부하지 않았으면 참입니다.
- **민감정보 근거([`consent-notes.md`](ops/consent-notes.md) 1절)**: 민감정보는 동의가 아니어도 법령이 허용하면 처리할 수 있습니다(제23조 제1항 제2호). 사회보장급여법·노인복지법·장애인복지법 시행령에 국가·지자체와 그 업무를 위탁받은 기관의 정해진 사무에 건강정보 처리를 허용하는 조항이 있습니다. 기관이 스스로 하는 상담과 사례관리는 대개 해당하지 않으므로 민감정보 동의를 받습니다.
- **AI에 보내지 않는 정보와 쓰는 순서([`masking.md`](starter/requirements/masking.md) 5번, [`ai.md`](starter/requirements/ai.md))**: 학대를 신고한 사람의 정보와 피해자가 머무는 곳·연락처는 조건을 모두 갖춰도 AI에 보내지 않습니다(아동학대처벌법 제10조 제3항, 노인복지법 제39조의6 제3항). 상담 기록과 사례 기록은 담당자가 먼저 쓰고, AI는 요약하고 다듬는 일을 돕습니다.
- **함께 고친 곳**: [`workflow.md`](starter/workflow.md)의 "꼭 지킬 것" 5·7번, S등급 판정, 5절 제목("AI 분석은 전송 조건과 사람의 판단을 전제로 합니다"), [`requirements.md`](starter/requirements/requirements.md), [`ai.md`](starter/requirements/ai.md), [`screen-agent.md`](starter/assess/screen-agent.md), [`agent.md`](starter/assess/agent.md), [`glossary.md`](starter/glossary.md), [`DECISION.md`](starter/templates/DECISION.md).
- **업체 계약 비교 정정([`masking.md`](starter/requirements/masking.md), [`requirements.md`](starter/requirements/requirements.md))**: Anthropic 표준 DPA도 OpenAI처럼 민감정보를 받는 것을 전제로 하지 않습니다(처리 설명 B.3 "None"). 이전에는 고객이 작성하는 항목이라고 잘못 적었습니다. AWS Bedrock(민감정보 제외 조항 없음, 학습 미사용, 기본 무보관)을 비교표에 더했습니다.
- **개인정보보호위원회 안내서(1.4.1, [`consent-notes.md`](ops/consent-notes.md) 1절·6절)**: "AI만 따로 다룬 개인정보보호위원회 해석은 아직 없다"는 틀렸습니다. 「생성형 AI 개발·활용을 위한 개인정보 처리 안내서」(2025.8)가 상용 AI API를 기업용 계약으로 쓰는 것을 처리위탁으로 보고, 국외이전 근거로 처리방침 공개(제1항 제3호)를 듭니다. 1.4의 판단과 같습니다. 2026년 4월 개정된 「개인정보 처리방침 작성지침」에 맞춰 6절 점검 항목에 AI 처리 내용(보관 기간, 학습 미사용, 거부 절차, 챗봇 답변 이의 제기)을 더했습니다.
- **참고 문서 [`starter/public-ai-standards.md`](starter/public-ai-standards.md)(1.4.1)**: 공공 AI와 클라우드 기준(개인정보보호위원회 안내서와 지침, 행정안전부 공공부문 인공지능 윤리기준, 대한민국 인공지능 윤리원칙, 인공지능기본법, CSAP와 그 개편)이 무엇이고 사회복지 기관과 어떤 관계인지 적었습니다. 공공은 보안 체계 안에서 AI를 쓰고 민간 기관은 그 밖에서 쓰므로 공공 기준을 그대로 옮기지 않았습니다. 판정 절차에서는 쓰지 않는 참고 문서라서 보완(1.4.1)으로 넣었습니다. CSAP가 국가정보원 보안검증으로 합쳐지는 개편에 맞춰 [`glossary.md`](starter/glossary.md), [`platform-facts.md`](starter/platform-facts.md), [`consent-form-sample.md`](ops/consent-form-sample.md) 참고 5의 설명도 고쳤습니다.
- **보안 점검 순서(1.4.2, [`agentic.md`](starter/rules/agentic.md))**: 보안 점검은 먼저 보고만 하고, 사용자가 승인한 항목만 고치고, 다시 점검합니다. AI는 "안전"이라고 판정하지 않고 "확인함·확인 필요·위험·해당 없음"과 근거를 적으며, 기능마다 "로그인하지 않은 사람"과 "다른 사용자"가 무엇을 볼 수 있는지 표로 보여 줍니다. 점검은 시험용 사이트에서만 합니다.
- **Apps Script 공개 범위(1.4.2, [`gas.md`](starter/rules/gas.md))**: 이름이 `_`로 끝나지 않는 전역 함수는 화면에서 부를 수 있으므로 쓰지 않는 함수는 비공개로 둡니다. 비밀값을 돌려주는 함수를 만들지 않고, 공개 웹앱과 관리 기능은 다른 프로젝트로 나누고, 시트에 쓰는 글자의 수식 실행을 막고, 끝난 웹앱은 배포를 보관 처리합니다.
- **사고 대응과 이상 징후 알림(1.4.2, [`handover.md`](ops/handover.md), [`requirements.md`](starter/requirements/requirements.md) 8절)**: 인수인계서의 장애 대응에 유출 사고 보고 체계, 72시간 통지·신고 요건, 알림을 받는 사람, 마지막 보안 점검일을 더했습니다. 접근 로그는 월 1회 점검에 더해 로그인 실패 급증, 대량 조회·내보내기, 관리자 권한 변경을 알리게 합니다.
- **채팅형 AI(1.4.2, [`masking.md`](starter/requirements/masking.md))**: 직원이 채팅창에 기록을 붙여 넣을 때는 서버 확인과 전송 기록을 갖출 수 없으므로, 기관이 승인한 계정에서만 쓰고 실명과 연락처와 사례 기록 원문을 넣지 않습니다.
- **읽을거리([`resources.md`](starter/resources.md), 1.4.2)**: 김종원 선생님의 「사회복지기관 DX·AX 전략서」를 더했습니다. 국외이전을 동의로 받는 쪽을 권하는 부분이 1.4와 다르다는 점을 함께 적었습니다. 안전사용 가이드 소개에도 AI 전송을 동의로 처리한다는 설명이 1.4와 다르다는 점을 밝혔습니다.
- **이미 만든 앱**: AI 전송에 국외이전 동의를 받고 있어도 위법은 아닙니다. 동의서에서 빼려면 처리방침의 국외이전 조항에 AI 회사와 거부 방법을 적고, 안내 사항에 AI 처리 항목을 넣고, 명부 필드를 `AI처리_가능`(거부하지 않았으면 참)으로 바꿉니다. 전에 동의하지 않은 이용자는 거부한 것으로 둡니다. 지자체에서 위탁받은 사무라면 민감정보의 법령 근거를 확인합니다. AI에 보내는 칸에 신고자 정보나 피해자의 거처·연락처가 섞여 있지 않은지 확인합니다. Anthropic API로 S등급 기록을 보내고 있다면 별도 계약 조건을 확인합니다.

## 1.3 근태·급여와 전자결재를 직접 만들 때의 기준 (2026.10)

- **증거급 기록의 판정([`workflow.md`](starter/workflow.md))**: "무결성 요구가 낮은 기능부터 적용한다"를 뺐습니다. 근태·급여와 전자결재를 직접 만든다면 처음 설계할 때 8개 원칙을 넣고, 운영 전에 "최종 확인"의 질문에 답할 수 있게 한 뒤 전문가 검토를 한 번 받습니다. 기성 제품을 먼저 검토하는 것은 그대로입니다.
- **[`record-integrity.md`](starter/data/record-integrity.md)**: 실무자가 먼저 정할 것을 맨 앞에 두고, 원칙마다 쉬운 설명과 구현을 나눴습니다. 목표는 외부 감사에게 승인된 문서가 그대로이고, 바꿀 일은 취소와 새 기안으로 처리했으며, DB를 직접 고치지 않았다고 보여 줄 수 있는 수준입니다. 승인된 문서는 고치지 않고, 바꿀 일이 생기면 취소 상태와 사유를 남긴 뒤 다음 번호로 새로 기안합니다. 근태·급여는 확정 내역과 급여명세서를 직원 개인 메일로 보내는 것으로 보관 등급 4의 외부 확인을 갖출 수 있고, hash는 직원에게 보낼 수 없는 기록에만 더합니다. 기관 메일과 기관 Slack은 기관 관리자가 관리하므로 이 사본이 되지 못합니다. 이사장·감사·지자체에 hash를 보내는 방법은 뺐습니다.
- **[`DECISION.md`](starter/templates/DECISION.md)**: 증거로 쓰는 기록에 승인된 문서를 바꿀 때의 절차를 적는 칸을 더했습니다.
- **이미 만든 앱**: 증거급 기록을 직접 만들었다면 승인된 문서를 고치거나 지우는 기능이 있는지 확인하고, 있으면 취소와 새 기안으로 바꿉니다. 그 절차를 [`DECISION.md`](starter/templates/DECISION.md)에 적습니다. 기관 밖으로 hash를 보내고 있다면 그대로 써도 됩니다.

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
