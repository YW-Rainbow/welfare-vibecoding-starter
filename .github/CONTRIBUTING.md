# 기여하기

- **플랫폼 추가**: `starter/workflow.md`의 요건 매트릭스에 열 하나를 더하고 4단계의 경로별 규칙 파일 목록에 연결한 뒤, `starter/rules/`에 규칙 파일을 추가합니다. 규칙 파일에는 다른 규칙 파일처럼 배포와 스테이징을 다루는 절을 두고, 운영하고 있는 앱에 반영하는 명령과 DB를 바꾸는 명령을 `starter/rules/agentic.md`의 확인 규칙 예시에 더하고, 바뀔 수 있는 사실은 `starter/platform-facts.md`에 적습니다.
- **스타터 템플릿 추가**: 경로별 스타터 템플릿 저장소를 만들어 `starter/resources.md`에 연결합니다.
- **정보 업데이트**: 가격, 무료 한도, 관련 제도는 자주 바뀝니다. 문서의 기준일을 확인하고 이슈나 PR로 알려 주세요.
- **규칙·절차 수정**: `AGENTS.md`나 `starter/workflow.md`를 고치면 `skills/welfare-app-assess/SKILL.md`, `skills/hwp-form-app/SKILL.md`, `starter/chat-prompt.md`도 어긋나지 않는지 확인합니다. `chat-prompt.md`는 머리말 아래에 `workflow.md` 본문을 다시 붙여 만듭니다. `workflow.md` 맨 앞의 "꼭 지킬 것"이 가리키는 원문(`consent-notes.md`, `ai.md`, `gas.md` 등)을 고쳤다면 그 블록도 함께 고칩니다. 원본 저장소에 반영할 때는 `plugin.json`, `.claude-plugin/plugin.json`, `.codex-plugin/plugin.json`의 `version`을 함께 올립니다. 올리지 않으면 이미 설치한 사용자는 바뀐 문서를 받지 못합니다.
- **현장 사례**: 사용한 구성, 만든 앱, 운영 과정에서 발생한 문제와 해결 방법을 공유해 주세요.
