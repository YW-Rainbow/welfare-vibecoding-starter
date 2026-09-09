# 함께 보면 좋은 자료

이 저장소의 판단 절차를 거친 뒤 개발과 운영에서 참고할 수 있는 자료입니다.

## 스타터 템플릿

| 경로 | 저장소 |
|---|---|
| 경로 C(GAS) | [apps-script-vibe-starter](https://github.com/YW-Rainbow/apps-script-vibe-starter) — clasp 설정과 에이전트 규칙이 갖춰져 있어 클론한 뒤 바로 시작할 수 있습니다. |

## 만들 때 쓰는 도구

| 저장소 | 소개 |
|---|---|
| [urimal-for-socialworker](https://github.com/dreamworker0/urimal-for-socialworker) | 김종원 선생님이 만든 Claude Code 스킬입니다. 사회복지사가 쓴 계획서와 보고서를 자연스러운 한국어로 수정합니다. 한덕연 선생님의 우리말 36항목을 기준으로 내용은 유지하고 문체를 다듬으며 변경 이유를 표로 제공합니다. 앱에서 만든 안내문이나 보고서 초안을 수정할 때 사용할 수 있습니다. |
| [EASYREAD](https://github.com/SWJoong/EASYREAD) | 최중호 선생님이 만든 MCP 서버입니다. 복잡한 한국어를 발달장애인이나 저문해력 당사자를 위한 **쉬운 정보(Easy-Read)**로 변환합니다. 지침·사전·검증 규칙 25종을 제공하며 실제 문장 변환은 Claude가 수행합니다. 오프라인으로 작동하고 입력 내용을 저장하지 않습니다. 결과물에는 감수를 거치지 않은 초안이며 최종본은 당사자의 확인이 필요하다는 점을 명시합니다. |
| [vibecoding-pub](https://github.com/elbumlee/vibecoding-pub) | 이경태 선생님이 만든 Claude Code 스킬입니다. 비개발자의 요청을 기획, 디자인, 개발, 오류 수정, 검토, 배포 역할로 나누어 처리합니다. `references/user-authority.md`는 사용자를 단순한 승인자가 아니라 결정권, 의견권, 최종 결재권을 가진 주체로 정의하고 에이전트가 이를 존중하는 방법을 설명합니다. |

## 실제로 만든 앱

| 저장소 | 소개 |
|---|---|
| [vehicle-drive-log](https://github.com/dreamworker0/vehicle-drive-log) | 김종원 선생님이 사회복지기관과 비영리단체를 위해 만든 차량 운행일지 웹앱입니다. 실제 운영 중인 MIT 라이선스 오픈소스 프로젝트이며 하나의 인스턴스에서 여러 기관을 운영할 수 있습니다. README의 **"떼어 쓸 수 있는 것"** 표에는 기관별 데이터 격리, 접속 기록, 무료 한도에 맞춘 비용 설계와 fork할 때의 제약이 정리되어 있습니다. |
| [SW_EDMS](https://github.com/SWJoong/SW_EDMS) | 최중호 선생님이 바이브코딩으로 만든 전자결재 학습용 샘플입니다. 실제 근태·회계 업무에 바로 사용할 수 없다는 한계를 명시하고 기록 무결성을 보강한 스키마와 등급표를 공개했습니다. [`record-integrity.md`](data/record-integrity.md)의 원칙을 적용한 사례입니다. |

## 읽을거리

| 곳 | 소개 |
|---|---|
| [사회복지사가 바이브 코딩까지 해요](https://socialwork-vibecoding.jijun74.workers.dev/) | 전재일 선생님이 쓴 온라인 책으로, 부제는 "연결과 확장"입니다. 독자가 글자 크기와 배경색을 고를 수 있고, 책갈피와 이어 읽기 기능도 제공합니다. 읽기 화면 자체가 [`ethics.md`](assess/ethics.md)에서 말하는 적정기술의 좋은 사례입니다. |
| [모두를 위한 스마트워크](https://wish.welfare.seoul.kr/swflmsfront/coworker/ksdetail.do?pno=10026&userno=58550) | 이 저장소를 만든 신용우가 서울시복지재단 지식공유 플랫폼에 연재하는 시리즈입니다. 구글 스마트워크, 생성형 AI, 디지털 전환을 현장 경험을 바탕으로 다룹니다. 이 가운데 「AI 시대를 위한 데이터 설계 방법론」 1~6편([1편](https://wish.welfare.seoul.kr/swflmsfront/board/boardr.do?bmno=10001&bno=107717&pno=10019&opno=0&)·[2편](https://wish.welfare.seoul.kr/swflmsfront/board/boardr.do?bmno=10001&bno=107727&pno=10019&opno=0&)·[3편](https://wish.welfare.seoul.kr/swflmsfront/board/boardr.do?bmno=10001&bno=107789&pno=10019&opno=0&)·[4편](https://wish.welfare.seoul.kr/swflmsfront/board/boardr.do?bmno=10001&bno=108035&pno=10019&opno=0&)·[5편](https://wish.welfare.seoul.kr/swflmsfront/board/boardr.do?bmno=10001&bno=108362&pno=10019&opno=0&)·[6편](https://wish.welfare.seoul.kr/swflmsfront/board/boardr.do?bmno=10001&bno=108366&pno=10019&opno=0&))은 생태도를 데이터로 바꾸고, 기관의 판단 기준을 기계도 읽을 수 있는 구조로 만드는 온톨로지를 설명합니다. [`levels.md`](data/levels.md)의 4단계는 이 여섯 편의 내용을 요약한 것입니다. |
| [기록에서 데이터로, 데이터에서 삶으로](https://www.dtsw.org/journal/5668173483343872) | 김진래 선생님이 『디지털과 사회복지』 4권 3호에 쓴 실천 보고입니다. 긍정행동지원팀이 흩어진 기록을 하나의 원장으로 모으고, AI를 연계하고, 당사자마다 다른 웹앱을 만들어 온 2년의 과정을 담았습니다. **"AI 이전에 데이터가, 데이터 이전에 실천 철학이 있어야 한다"**는 순서와 AI에게 맡길 일과 맡기지 않을 일의 경계가 특히 볼 만합니다. 이 저장소의 [`ssot.md`](data/ssot.md)에 담긴 데이터 이관 절차와 품질 등급, [`workflow.md`](workflow.md)의 AI 활용 원칙은 이 글을 참고했습니다. |
