# 함께 보면 좋은 자료

> 출처·최신판: https://github.com/YW-Rainbow/welfare-vibecoding-starter

이 저장소의 판단 절차를 거친 뒤 개발과 운영에서 참고할 수 있는 자료입니다.

## 스타터 템플릿

| 경로 | 저장소 |
|---|---|
| 경로 C(GAS) | [apps-script-vibe-starter](https://github.com/YW-Rainbow/apps-script-vibe-starter): clasp 설정과 에이전트 규칙이 갖춰져 있습니다. 별도 저장소로 클론하지 않고 내용을 앱 저장소의 `app/`에 복사해 시작합니다. |

## 만들 때 쓰는 도구

| 저장소 | 소개 |
|---|---|
| [urimal-for-socialworker](https://github.com/dreamworker0/urimal-for-socialworker) | 김종원 선생님이 만든 Claude Code 스킬입니다. 사회복지사가 쓴 계획서와 보고서를 자연스러운 한국어로 수정합니다. 한덕연 선생님의 우리말 36항목을 기준으로 내용은 유지하고 문체를 다듬으며 고친 이유를 표로 보여 줍니다. 앱에서 만든 안내문이나 보고서 초안을 수정할 때 사용할 수 있습니다. |
| [EASYREAD](https://github.com/SWJoong/EASYREAD) | 최중호 선생님이 만든 MCP 서버입니다. 복잡한 한국어를 발달장애인이나 저문해력 당사자를 위한 **쉬운 정보(Easy-Read)**로 변환합니다. 지침·사전·검증 규칙 25종을 제공하며 문장을 실제로 바꾸는 일은 Claude가 합니다. 오프라인으로 작동하고 입력 내용을 저장하지 않습니다. 결과물에는 감수를 거치지 않은 초안이고 최종본은 당사자가 확인해야 한다는 문구를 붙입니다. |
| [rhwp](https://github.com/edwardkim/rhwp) | Edward Kim(edwardkim) 님이 만든 Rust + WebAssembly 기반 HWP/HWPX 뷰어·편집기입니다. npm 패키지 `@rhwp/core`로 브라우저에서 HWP를 읽고 누름틀에 값을 채워 저장할 수 있고, `@rhwp/editor`는 편집기를 웹페이지에 넣습니다. MCP 서버가 내장되어 있어 Claude Code가 HWP 양식을 직접 읽고 채울 수 있습니다. [크롬 확장](https://chromewebstore.google.com/detail/pgakpjflombjmehnebnbpnalhegaanag)과 엣지·파이어폭스 확장으로도 배포되어 브라우저에서 HWP를 바로 열고 편집하고 인쇄할 수 있으며, 파일은 서버로 가지 않습니다. 2026년 9월 기준으로 직전 석 달 동안 다섯 번 릴리스되는 등 꾸준히 업데이트됩니다. [`hwp.md`](requirements/hwp.md)의 기준 도구입니다. |
| [rhwp-studio](https://github.com/dreamworker0/rhwp-studio) | 김종원 선생님이 rhwp 위에 만든 웹 편집기입니다. Google Drive의 HWP·HWPX를 열어 편집하고 다시 저장하며, Google Workspace Marketplace에 등록되어 Drive에서 "연결 앱으로 열기"가 됩니다. 문서는 서버로 가지 않고 브라우저 안에서만 처리됩니다. 기관이 Drive를 쓴다면 이 앱만 설치하면 HWP를 편집할 수 있습니다. |

## 현장에서 만든 앱

| 저장소 | 소개 |
|---|---|
| [vehicle-drive-log](https://github.com/dreamworker0/vehicle-drive-log) | 김종원 선생님이 사회복지기관과 비영리단체를 위해 만든 차량 운행일지 웹앱입니다. 실제 운영 중인 MIT 라이선스 오픈소스 프로젝트이며 한 번 설치해 여러 기관이 함께 쓸 수 있습니다. README의 **"떼어 쓸 수 있는 것"** 표에는 기관별 데이터 격리, 접속 기록, 무료 한도에 맞춘 비용 설계와 fork해서 쓸 때 주의할 점이 정리되어 있습니다. |
| [Family-tree](https://github.com/dreamworker0/Family-tree) | 김종원 선생님이 만든 대화형 가계도(Genogram) 웹앱입니다. 인물을 추가하고 결혼·이혼·입양·임신·사망 등 가계도 기호로 관계를 그린 뒤 PNG로 내보내거나 JSON 파일로 저장해 다시 불러올 수 있습니다. 서버 없이 브라우저 안에서만 동작하므로 가족관계 같은 민감한 내용이 외부로 전송되지 않습니다. [`workflow.md`](workflow.md)의 경로 B(로컬 퍼스트)에 해당하는 사례입니다. |
| [SW_EDMS](https://github.com/SWJoong/SW_EDMS) | 최중호 선생님이 바이브코딩으로 만든 전자결재 학습용 샘플입니다. 실제 근태·회계 업무에 바로 사용할 수 없다는 한계를 명시하고 기록 무결성을 보강한 스키마와 등급표를 공개했습니다. [`record-integrity.md`](data/record-integrity.md)의 원칙을 적용한 사례입니다. |

## 읽을거리

| 자료 | 소개 |
|---|---|
| [사회복지사가 바이브 코딩까지 해요](https://socialwork-vibecoding.jijun74.workers.dev/) | 전재일 선생님이 쓴 온라인 책으로, 부제는 "연결과 확장"입니다. 독자가 글자 크기와 배경색을 고를 수 있고, 책갈피와 이어 읽기 기능도 제공합니다. 읽기 화면 자체가 [`ethics.md`](assess/ethics.md)에서 말하는 적정기술의 좋은 사례입니다. |
| [모두를 위한 스마트워크](https://wish.welfare.seoul.kr/swflmsfront/coworker/ksdetail.do?pno=10026&userno=58550) | 이 저장소를 만든 신용우가 서울시복지재단 지식공유 플랫폼에 연재하는 시리즈입니다. 현장 경험을 바탕으로 구글 스마트워크, 생성형 AI, 디지털 전환을 다룹니다. 이 가운데 「AI 시대를 위한 데이터 설계 방법론」 1~6편([1편](https://wish.welfare.seoul.kr/swflmsfront/board/boardr.do?bmno=10001&bno=107717&pno=10019&opno=0&)·[2편](https://wish.welfare.seoul.kr/swflmsfront/board/boardr.do?bmno=10001&bno=107727&pno=10019&opno=0&)·[3편](https://wish.welfare.seoul.kr/swflmsfront/board/boardr.do?bmno=10001&bno=107789&pno=10019&opno=0&)·[4편](https://wish.welfare.seoul.kr/swflmsfront/board/boardr.do?bmno=10001&bno=108035&pno=10019&opno=0&)·[5편](https://wish.welfare.seoul.kr/swflmsfront/board/boardr.do?bmno=10001&bno=108362&pno=10019&opno=0&)·[6편](https://wish.welfare.seoul.kr/swflmsfront/board/boardr.do?bmno=10001&bno=108366&pno=10019&opno=0&))은 생태도를 데이터로 바꾸고, 기관의 판단 기준을 기계도 읽을 수 있는 구조로 만드는 온톨로지를 설명합니다. [`levels.md`](data/levels.md)의 4단계는 이 여섯 편의 내용을 요약하고 보충한 것입니다. |
| [AI 시대, 사회복지 현장이 바꿀 것, 버릴 것, 지킬 것](https://www.welfare.net/communication/promotion/card-news-detail?searchType=all&searchValue=%EC%8B%A0%EC%9A%A9%EC%9A%B0&id=888716) | 신용우의 칼럼으로, 한국사회복지사협회 카드뉴스로 실렸습니다. 바꿀 것으로는 상담 일지의 현장 관찰 메모 칸, 동의서의 AI 활용 네 항목, 당사자에게 편한 방식과 AI에 맡기는 행정을 꼽습니다. 버릴 것은 AI 요약을 의심 없이 믿는 습관(스웨덴·암스테르담의 AI 감시 중단 사례), 배려가 빠진 말투, 최종 판단을 기계에 미루는 태도입니다. 지킬 것은 가장 느리게 걸을 수 있는 실력, 배려의 근육, 글로 길러지는 실천지혜입니다. 같은 주제의 연작 [실천지혜의 상실](https://wish.welfare.seoul.kr/swflmsfront/board/boardr.do?bno=106704), [AI의 정답이 아닌 우리의 선택](https://wish.welfare.seoul.kr/swflmsfront/board/boardr.do?bno=106730), [종이 설문지로 돌아갈 용기](https://wish.welfare.seoul.kr/swflmsfront/board/boardr.do?bno=106318)와 함께 [`ai.md`](requirements/ai.md)의 바탕이 되었습니다. |
| [기록에서 데이터로, 데이터에서 삶으로](https://www.dtsw.org/journal/5668173483343872) | 김진래 선생님이 『디지털과 사회복지』 4권 3호에 쓴 실천 보고입니다. 긍정행동지원팀이 흩어진 기록을 원장 하나로 모으고, AI를 연계하고, 당사자마다 다른 웹앱을 만들어 온 2년의 과정을 담았습니다. **"AI 이전에 데이터가, 데이터 이전에 실천 철학이 있어야 한다"**는 순서, 그리고 AI에 맡길 일과 맡기지 않을 일을 가르는 기준이 특히 볼 만합니다. 이 저장소의 [`ssot.md`](data/ssot.md)에 담긴 데이터 이관 절차와 품질 등급, [`workflow.md`](workflow.md)의 AI 활용 원칙, [`ai.md`](requirements/ai.md)에서 사람이 할 일과 AI에 맡길 일을 나눈 방식은 이 글을 참고했습니다. |
| [vibecoding-pub의 사용자 권한 프로토콜](https://github.com/elbumlee/vibecoding-pub/blob/main/references/user-authority.md) | 이경태 선생님이 만든 Claude Code 스킬 vibecoding-pub의 참고 문서입니다. 사용자를 단순한 승인자가 아니라 목적과 범위를 정하는 결정권자, 의견 제출자, 최종 결재자로 정의하고 에이전트가 이를 어떻게 존중해야 하는지 적었습니다. [`agentic.md`](rules/agentic.md)의 "사용자와 에이전트의 결정 범위를 구분합니다"는 이 관점을 참고했습니다. 스킬 자체는 페르소나 16명을 사람이 설계해 작업을 배정하는 방식으로, 모델이 계획과 역할 분담을 스스로 하는 지금은 설치를 권하지 않고 이 문서만 소개합니다. |
| [사회복지 현장 AI·바이브코딩 안전사용 가이드](https://docs.google.com/document/d/1at2PqpW1kG3zEh5XIDaTLMC2ozN0Ar1Gf9YgvSjmnTc/edit?usp=sharing) | 신용우가 기관에서 함께 읽고 AI 사용 가이드라인과 이용자 동의서, 개인정보 처리방침을 만들도록 쓴 매뉴얼입니다. 당사자와 기관 사이는 동의와 안내로, 기관과 외부 회사 사이는 계약·공개·안전조치로 나눠 설명하고, 국외이전 가운데 클라우드 보관은 처리방침 공개로, AI 전송은 동의로 처리한다는 2023년 개정 기준을 따릅니다. 2026년 9월 개정판으로 갱신 중인 Google 문서입니다. 부록의 동의서 양식 원본은 이 저장소의 [`consent-form-intake.md`](../ops/consent-form-intake.md)에서 관리하며, 그 기준은 [`consent-notes.md`](../ops/consent-notes.md), [`masking.md`](requirements/masking.md), [`ai.md`](requirements/ai.md)와 같습니다. |
| [AI는 만들고, 리더는 판단한다](https://thornjsh.github.io/AI%20%EB%A6%AC%EB%8D%94%EC%8B%AD%202026-0819.pdf) | 정수홍 선생님(부민노인복지관)이 쓴 글로, 부제는 "사회복지시설의 DX·AX를 이끄는 리더십"입니다. 새 시스템은 직원이 만들 수 있어도 기존 업무를 끝내는 결정은 리더만 할 수 있다고 보고, 기술과 현실 사이의 틈은 허용 범위와 확인 절차와 책임 소재를 미리 정해 메우자고 합니다. 문제가 생기면 가장 가까운 실무자에게 책임이 쏠리는 '도덕적 충격흡수대'를 경계하는 대목은 [`ethics.md`](assess/ethics.md) 6절과 같은 방향입니다. 판정 결과를 들고 기관장과 이야기할 때 함께 건네기 좋습니다. 글에 나오는 GPS 출퇴근 사례를 따라 만들 때는 [`ethics.md`](assess/ethics.md)의 다섯 질문을 먼저 적용합니다. |
