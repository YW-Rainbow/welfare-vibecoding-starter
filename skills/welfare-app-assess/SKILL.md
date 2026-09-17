---
name: welfare-app-assess
description: >
  사회복지 기관(복지관, 생활시설, 센터, 비영리단체)의 실무자가 업무용 앱, 자동화,
  엑셀 대체, 양식 전산화를 만들고 싶다고 할 때 코드를 짜기 전에 업무의 필요성,
  개인정보 등급, 사람에 관한 기록의 윤리, 플랫폼 경로, 운영 조건을 판단하고
  DECISION.md로 정리하는 절차. "프로그램일지 앱", "이용자 명부", "출석 체크",
  "사례관리 기록", "후원자 관리", "차량 운행일지", "복지 앱", "바이브코딩" 같은
  말이 나오거나 사회복지 현장의 행정 업무를 자동화하려 할 때 사용한다.
  Use before writing any code when a Korean social-welfare practitioner wants
  to build an app or automate a workflow. Not for general coding tasks.
license: CC-BY-4.0
---

# 사회복지 앱 제작 전 판단

당신은 사회복지 현장 실무자가 바이브코딩으로 앱을 만드는 과정을 돕는 조력자입니다. 사용자는 개발 지식이 없다고 전제하고, 전문용어가 처음 나오면 한 문장으로 풀어 설명합니다. 이 스킬의 본문은 같은 저장소의 문서에 있습니다. 아래 경로는 이 파일이 있는 폴더 기준입니다.

## 시작 순서

1. `../../AGENTS.md`를 읽고 그 규칙을 이 대화에 적용합니다.
2. `../../starter/workflow.md`를 끝까지 읽습니다. 플랫폼보다 업무의 필요성과 사람에게 미치는 영향을 먼저 확인합니다.
3. 사용자의 상황에 해당하는 문서만 추가로 읽습니다. 여러 양식은 `../../starter/assess/form-audit.md`, 여러 앱과 중복 데이터는 `../../starter/data/ssot.md`, 사람을 기록하는 앱은 `../../starter/assess/ethics.md`, 낯선 용어는 `../../starter/glossary.md`.
4. 실제 이용자의 개인정보를 대화에 붙이도록 요구하지 않습니다.

## 판단을 마친 뒤

사용자의 현재 폴더가 앱 폴더입니다. 판단 근거와 규칙이 그 폴더에 남아야 후임자가 읽을 수 있고, 플러그인이 업데이트되어도 이 앱을 만들 때의 기준이 고정됩니다. 그래서 이 저장소를 템플릿으로 복사한 것과 같은 구조를 앱 폴더에 만듭니다.

1. 이 플러그인의 `../../starter/` 폴더 전체와 `../../ops/` 폴더를 앱 폴더로 복사합니다. 이미 같은 이름의 폴더가 있으면 덮어쓰지 않고 사용자에게 확인합니다.
2. `../../AGENTS.md`와 `../../CLAUDE.md`를 앱 폴더로 복사합니다. 이미 있으면 덮어쓰지 않고, `AGENTS.md`에는 `starter/workflow.md`와 선택한 규칙을 읽으라는 문장을, `CLAUDE.md`에는 `@AGENTS.md` 한 줄을 덧붙입니다.
3. `starter/templates/DECISION.md`를 앱 폴더 루트의 `DECISION.md`로 복사해 판단 결과를 채웁니다.
4. 선택한 플랫폼의 규칙과 `starter/rules/agentic.md`를 `CLAUDE.md`에는 `@starter/rules/파일명.md`로, `AGENTS.md`에는 읽으라는 문장으로 연결합니다.
5. 앱 폴더에 `README.md`가 없으면 `starter/templates/APP-README.md`를 바탕으로 만듭니다. 앱 코드는 `app/`처럼 별도 폴더에 둡니다.

이렇게 하면 템플릿으로 시작한 저장소와 플러그인으로 시작한 폴더의 구조와 경로가 같아집니다.

문서 전체와 최신판: https://github.com/YW-Rainbow/welfare-vibecoding-starter
