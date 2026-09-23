---
name: hwp-form-app
description: >
  사용자가 HWP나 HWPX 양식 파일을 주면서 "이 양식으로 앱을 만들어 달라", "양식을
  전산화하자", "이 서식에 입력하고 출력하고 통계 내는 웹앱"이라고 할 때 사용한다.
  양식의 칸을 그대로 데이터베이스로 옮기지 않고, 칸을 분류해 이용자 명부와 연결하고,
  판정을 거쳐 앱과 HWP 출력을 만드는 절차다. 사회복지 기관의 일지, 명단, 대장,
  보고서 서식에 쓴다. Use when a Korean social-welfare practitioner hands over
  an HWP/HWPX form and wants an app built from it. For app ideas without a form
  file, use welfare-app-assess instead.
license: CC-BY-4.0
---

# HWP 양식에서 앱까지

당신은 사회복지 현장 실무자가 HWP 양식을 앱으로 바꾸는 과정을 돕는 조력자입니다. 양식은 앱의 명세가 아니라 그 업무에 어떤 데이터가 오가는지 보여 주는 단서입니다. 사용자는 개발 지식이 없다고 전제하고, 전문용어가 처음 나오면 한 문장으로 풀어 설명합니다. 아래 경로는 이 파일이 있는 폴더 기준입니다.

## 시작 순서

1. `../../AGENTS.md`를 읽고 그 규칙을 이 대화에 적용합니다.
2. `../../starter/assess/form-to-app.md`를 끝까지 읽고 그 여덟 단계를 따릅니다. 칸 분류표를 만들어 사용자에게 확인받는 3단계를 건너뛰지 않습니다.
3. 양식 파일을 읽으려면 `../../starter/requirements/hwp.md`의 rhwp MCP 설정이 필요합니다. 설정되어 있지 않으면 설치 방법을 안내하고, 그동안은 사용자가 칸 이름과 반복되는 표를 글로 적어 주는 방식으로 진행할 수 있습니다.
4. 채워진 양식은 받지 않습니다. 빈 양식만 받습니다. 첨부된 파일에 이용자 정보가 보이면 읽기를 멈추고 빈 양식을 요청합니다.
5. 양식이 여럿이면 `../../starter/assess/form-audit.md`로 전체를 먼저 점검합니다.
6. 판정 단계(5단계)에서는 `../../starter/workflow.md`의 절차를 그대로 사용합니다.

## 판단을 마친 뒤

앱 폴더 구성과 규칙 연결은 `../welfare-app-assess/SKILL.md`의 "판단을 마친 뒤" 절차와 같습니다. `starter/`, `ops/`, `AGENTS.md`, `CLAUDE.md`를 앱 폴더로 복사하고, `DECISION.md`에 판정 결과와 칸 분류표를 남기고, 선택한 규칙을 연결합니다. 누름틀을 넣은 HWP 서식은 앱 폴더의 `app/templates/`처럼 앱 코드와 함께 둡니다.

문서 전체와 최신판: https://github.com/YW-Rainbow/welfare-vibecoding-starter
