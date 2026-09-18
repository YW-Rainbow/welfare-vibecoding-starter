# 이 저장소를 사용하는 AI 에이전트의 작업 규칙

이 저장소는 코드 템플릿이 아니라 사회복지 현장 실무자가 앱을 만들기 전에 업무, 데이터, 윤리, 플랫폼, 운영 조건을 판단하도록 돕는 문서 모음입니다. 사용자는 보통 GitHub의 "Use this template"으로 이 저장소를 복사해 자기 앱 저장소로 삼거나, `skills/`의 스킬을 플러그인으로 설치해 자기 앱 폴더에서 씁니다. 어느 쪽이든 아래 규칙은 같습니다.

1. 먼저 `README.md`와 `starter/workflow.md`를 읽습니다. 두 문서는 빠뜨리지 말아야 할 판단 기준이며 고정된 질문 목록이 아닙니다. 플랫폼 선택보다 업무의 필요성과 영향을 먼저 살핍니다.
2. 대화와 저장소에서 알 수 있는 내용은 다시 묻지 않고 합리적으로 추론합니다. 결과를 크게 바꿀 수 있는 정보가 빠져 있을 때만 질문하며, 질문 순서와 분석 방법은 상황에 맞게 정합니다.
3. 사용자의 목적, 현장에 관한 설명과 명시적인 결정이 일반적인 권장사항보다 우선합니다. 개인정보 보호, 법적 의무, 보안 또는 되돌리기 어려운 영향과 충돌하면 구체적인 근거와 대안을 설명하고 확인합니다.
4. 사용자의 상황에 해당하는 문서만 추가로 읽습니다. 여러 양식은 `starter/assess/form-audit.md`, 여러 앱과 중복 데이터는 `starter/data/ssot.md`, 사람을 기록하는 앱은 `starter/assess/ethics.md`, 기관 서식이 HWP 파일이면 `starter/requirements/hwp.md`를 적용합니다. 사용자가 HWP 양식 파일을 주며 앱을 만들자고 하면 `starter/assess/form-to-app.md`의 절차를 따르고, 양식의 칸을 그대로 데이터 항목으로 삼지 않습니다. AI 기능(요약·초안·분류·추천)을 넣는 앱은 `starter/requirements/ai.md`를 적용합니다. 나머지 조건별 문서는 `starter/workflow.md`의 안내를 따릅니다.
5. 사용자는 개발 지식이 없다고 가정하고, 전문용어가 처음 나오면 `starter/glossary.md`를 참고해 한 문장으로 설명합니다.
6. 실제 이용자의 개인정보를 대화나 에이전트 컨텍스트에 제공하도록 요구하지 않습니다.
7. 판단 결과는 앱 저장소 루트의 `DECISION.md`에 기록합니다. `starter/templates/DECISION.md`를 복사해 사용합니다. 이 저장소를 템플릿으로 복사해 쓰고 있다면 그 저장소가 곧 앱 저장소입니다.
8. 판정이 끝나면 앱은 같은 저장소에서 만듭니다. 플러그인으로 쓰는 경우에는 먼저 `starter/`, `ops/`, `AGENTS.md`, `CLAUDE.md`를 앱 폴더로 복사해 같은 구조를 만든 뒤 아래를 적용합니다. `starter/`와 `ops/`(템플릿으로 복사했다면 `skills/`도)는 판단 근거와 운영 자료이므로 삭제하거나 앱 코드로 덮어쓰지 않습니다. 앱 코드는 `app/`처럼 별도 폴더에 두고, 선택한 `starter/rules/` 파일과 `starter/rules/agentic.md`를 `CLAUDE.md`에는 `@starter/rules/파일명.md`로, `AGENTS.md`에는 읽으라는 문장으로 연결합니다. 앱 개발을 시작할 때 `README.md`는 `starter/templates/APP-README.md`를 바탕으로 앱 소개로 바꾸고(앱 소개가 이미 있으면 덧붙이고), 스타터 안내는 원본 저장소 링크로 대신합니다. 다음 앱은 템플릿을 다시 복사해 새 저장소에서 시작합니다.
9. 가격, 한도, 서비스 정책처럼 바뀔 수 있는 정보는 인터넷에 접근할 수 있다면 해당 사업자의 공식 문서에서 최신 내용을 확인합니다.
10. 이 저장소의 문서를 사용하는 방법은 세 가지이고, 각각 시작 파일이 다릅니다. `CLAUDE.md`·`AGENTS.md`(폴더 안에서 실행하는 도구), `skills/welfare-app-assess/SKILL.md`와 `skills/hwp-form-app/SKILL.md`(플러그인으로 설치한 도구), `starter/chat-prompt.md`(채팅창에 붙이는 사람). 규칙이나 `starter/workflow.md`를 고쳤다면 이 시작 파일들이 서로 어긋나지 않는지 확인하고, `starter/chat-prompt.md`는 머리말 아래에 `starter/workflow.md` 본문을 다시 붙여 새로 만듭니다.
