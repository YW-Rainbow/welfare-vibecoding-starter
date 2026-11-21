# 버전 기록

판단 기준이 바뀐 것을 버전으로 묶어 적습니다. 새 판단 문서가 생기거나 판정이 달라질 만큼 바뀌면 버전을 올리고, 그 사이의 보완(끝자리)은 그 버전 절 안에 적습니다. 보완이 길면 절 안에 소제목(예: `### 1.5.1`)을 둡니다. 문장 손질과 오타 수정은 적지 않습니다. README의 "최근 바뀐 것"에는 최근 3개 큰 버전(앞 두 자리)만 짧게 요약하고, 보완은 따로 줄을 두지 않습니다. 보완이 이미 만든 앱에 할 일을 남길 때만 그 버전 줄의 "할 일"을 고칩니다.

템플릿으로 복사한 저장소는 원본을 따라 바뀌지 않습니다. 플러그인도 판정을 마친 뒤 `starter/`를 앱 폴더에 복사하므로 그때의 기준으로 고정됩니다. 이미 만든 앱은 [`DECISION.md`](starter/templates/DECISION.md)의 "참고한 저장소 주소와 버전"에 적은 번호의 앞 두 자리와 같은 절부터 봅니다(1.2.1이면 1.2 절부터). 보완은 `plugin.json`의 끝자리만 올리고 그 버전 절 안에 적기 때문입니다. 반영할 곳을 찾을 때는 AI에게 "원본 저장소의 CHANGELOG를 보고 내 [`DECISION.md`](starter/templates/DECISION.md)에 반영할 곳을 찾아 줘"라고 부탁합니다.

## 1.6 AI 윤리·활용 가이드라인 전면 개편 (2026.11)

1.6의 핵심은 기관용 「AI 윤리·활용 가이드라인」([`ai-guideline.md`](agency/ai-guideline.md))의 전면 개편입니다. 일곱 원칙을 새로 짜고, 민감정보 판단 기준을 법이 요구하는 것과 기관이 더하는 기준으로 나눴습니다. 어느 도구에 어느 등급까지 보내는지에 대한 판정은 1.5와 거의 같습니다.

### 가이드라인

- **일곱 원칙을 새로 짬(1부 4·5절)**: 생각·시간·계정·정보·당사자·존중·책임. 직원과 기관이 실제로 고민하고 실천하는 순서대로 배열했습니다.
  - 사람의 존엄성은 원칙 하나가 아니라 원칙 앞의 머리말(「사회복지사 윤리강령」)에 두어 모든 원칙의 바탕으로 삼았습니다. 이 원칙은 기관이 자체 기준을 제정할 때 참고하는 예시이며, 직원과 당사자의 의견을 반영하여 수정한 후 사용한다고 밝혔습니다.
  - 새 원칙 '생각'은 직원이 AI의 결과를 보기 전에 먼저 판단하고 그 이유를 기존 기록 양식에 직접 기록하게 합니다. 새 원칙 '시간'은 AI로 절감한 시간의 사용처를 기관장이 직원과 함께 정하고, 새로 생긴 검토·유지 관리 업무를 업무량에 포함하게 합니다.
  - 1.5의 원칙 1 '사람이 판단하고 기관이 책임진다'는 '책임'이 되었습니다. 원칙 6 '기록과 판단 근거는 사람이 쓴다'는 '생각'이 되었고, 원칙 7에 있던 원래 기록과의 대조는 '책임'으로 옮겼습니다. 원칙 5 '사람을 존중하는 말을 쓴다'와 원칙 7 '공정하게 쓰고 편향을 점검한다'는 '존중'으로 합쳤고, AI에 편향이 있음을 전제로 직원이 직접 판단하게 했습니다. 원칙 2 '정보'는 원칙 4로, 원칙 4 '당사자'는 원칙 5로 옮겼고, 원칙 3 '계정'은 번호가 그대로입니다.
  - 4절에는 원칙과 핵심 기준만 두고, 원칙별 세부 기준과 예시는 5절에 두었습니다. 예시는 특정 직무가 아니라 기술이 바뀌어도 남는 상황으로 들었습니다.
  - 1부 3절에 직원, 담당자, 기관장, AI 활용 담당자를 구분해 정의했습니다. 행정안전부 「공공부문 인공지능 윤리기준」의 6대 핵심가치와 원칙의 대응을 4절 끝에 적었습니다.
- **AI가 대신하는 일과 에이전트 권한(원칙 3·7, 3부 3장)**: AI가 메일 보내기, 파일 지우기·공유하기, 결제하기처럼 되돌리기 어려운 작업을 대신하면 승인 권한이 있는 직원이 실행 직전에 확인하고 승인합니다. AI 에이전트에 기관 계정을 연결할 때는 직원이 허용하는 권한을 직접 읽고, 연결한 뒤에도 권한을 확인하고, 필요하면 연결을 해제하고 업체에 삭제를 요청합니다. 3부 3장의 관리자 설정, 퇴사·전보, 분기 점검에 에이전트 권한을 넣고, 권한을 주고 바꾸고 회수한 내역을 3년 이상 보관하게 했습니다(「개인정보의 안전성 확보조치 기준」 제5조 제3항).
- **AI 사용 중지와 재개(원칙 7, 3부 4장)**: 피해가 의심되면 AI 활용 담당자가, 자리에 없으면 대리자가 해당 업무에서 AI 사용을 중지합니다. 기관은 원인을 바로잡은 뒤 다시 사용할지 정하고 그 과정을 기록합니다. 3부 5장에 당사자가 사람의 재검토를 요청하는 길을 더했습니다.
- **사진, 목소리, 영상(원칙 6, 2부 2장)**: 실제 인물의 얼굴이나 목소리를 AI로 변환하기 전에 목적과 공개 범위를 설명하고 동의를 받습니다. 그림체를 바꿔도 알아볼 수 있으면 원본 사진과 같이 다루고, 등급에 맞는 도구로 변환합니다. 동의서 양식 A ②와 양식 B에 "사진·영상의 AI 변환과 국외이전 동의" 칸을 더하고, AI 변환과 국외이전은 따로 묻게 했습니다([`consent.md`](agency/consent.md) 2부). 기관 밖으로 내보내는 결과물의 AI 활용 표시는 AI로 만들거나 변환한 이미지, 음성, 영상에 하고, AI로 초안을 쓴 문서는 직원이 확인해 기관 이름으로 내보내므로 따로 표시하지 않아도 되는 것으로 정리했습니다.
- **법과 기관 기준을 나눔(3부 1장)**: "왜 업체마다 결론이 다른가"에서 GDPR의 데이터 처리 계약(DPA)과 그 안의 '민감정보' 칸을 업체마다 어떻게 채웠는지 차례로 설명합니다. "법이 요구하는 것과 이 가이드라인이 더하는 것"에서 개인정보보호위원회 안내서의 기준(처리 근거, 학습을 배제한 기업용 계약, 위탁 계약의 법정 항목, 처리방침 공개, 사람 확인)과 이 가이드라인이 더하는 기준(DPA가 민감정보를 적었나)을 쪽수와 함께 나눴습니다. 공공기관용 국가정보원 기준은 참고로 적었습니다.
- **약관으로 맺는 위탁 계약(3부 1장, [`consent.md`](agency/consent.md) 6절)**: OpenAI를 포함해 각 업체의 DPA는 약관에 들어 있어 기관 계정으로 가입하면 적용되고, 서명본을 따로 받을 필요는 없습니다. 약관으로 맺는 위탁 계약에 들어 있어야 할 일곱 항목(법 제26조 제1항, 시행령 제28조 제1항)과 확인 방법을 적었습니다.
- **정부 업무 시스템(2부 2장, 3부 6장)**: 희망이음 같은 정부 시스템의 화면과 자료는 그 시스템의 이용 기준과 위탁 협약이 허용하는 범위에서만 AI로 처리하고, 에이전트 브라우저 동기화는 사전 검토를 거치며 주민등록번호가 보이는 화면에서는 쓰지 않습니다([`agent-browser.md`](starter/assess/agent-browser.md)도 같은 기준).
- **'AI로 처리한다'로 통일**: 개인정보 문맥에서 'AI에 보낸다·넣는다'를 'AI로 처리한다'로 맞췄습니다. 법의 '제3자 제공'과 헷갈리지 않게 하려는 것입니다. 2부 2장 제목도 "AI로 처리하기 전에"로 바꿨습니다.
- **늘 하는 일(3부 1장)**: 신청 전(의뢰·발굴) 정보는 동의서를 받기 전까지 AI로 처리하지 않습니다. 보고, 평가, 사례회의 자료는 원래 업무와 같은 근거로 처리합니다. 사례발표 자료는 같은 지역 사람도 누구인지 모를 수준(N)일 때만 등급 제한 없이 AI로 처리합니다.
- **운영과 부록**: 운영에 교육의 편향 실습, 점검의 업무량 조정, 자원(가벼운 모델, 필요 없는 반복 생성 줄이기)을 더했습니다. 부록 1 조문은 새 원칙에 맞춰 13개 조로, 부록 2 점검표는 원칙 순서로 다시 짰습니다. 부록 3 Q5에 개인정보보호위원회 기준과의 차이를, Q6에 미국 의료정보용 계약(BAA)과 개별 계약을 더하고, Q11 "기업용 Claude를 쓰는데 왜 상담 요약을 못 하게 하나요?"를 새로 넣었습니다.

### 스타터팩 전체

- **등급 표시([`workflow.md`](starter/workflow.md) 1단계)**: 🟢 N(None) · 🟡 P(Personal) · 🔴 S(Sensitive)로 색과 영어 약자를 붙였습니다. 색은 금지 신호가 아니라 정보의 종류를 나타냅니다. 국가정보원의 기밀(C)·민감(S)·공개(O)와 다른 기준이고 기밀은 다루지 않습니다. 얼굴이 나온 사진과 목소리는 P이고, S의 생체인식정보는 얼굴 인식처럼 특정인을 알아보려고 기술로 처리한 정보입니다([`ethics.md`](starter/assess/ethics.md)도 같은 기준으로 맞춤).
- **도구 추가와 재확인(2026-11-20, [`sending-data-to-ai.md`](starter/requirements/sending-data-to-ai.md))**: Microsoft 365 Copilot(업무용)을 "민감정보까지"에, 네이버클라우드 CLOVA Studio를 "개인정보 없음만"에 더했습니다. 업스테이지는 칸을 정하지 않았습니다. Claude는 Microsoft Foundry나 Google Cloud로 써도 대부분 Anthropic 계약이 적용되고, BAA는 한국 기관에 적용되는지 공식 언급이 없습니다. Bedrock에서 30일 보관·사람 검토가 붙는 모델에 Claude Fable 5.2를 더했고, 서울 리전 내 추론의 구조화 출력 미지원은 해소되었습니다. Azure Korea Central은 종량제로는 Global 배포만 되어 작은 기관은 국외이전으로 봅니다. Workspace Gemini의 보관 기간을 기능별로 나눠 적었습니다. 비영리 무료판에서 일부 직원만 골라 Business Standard로 올릴 수 있게 된 것을 관리 콘솔에서 확인해 반영했습니다(도움말 문서는 아직 옛 문구).
- **문서 사이를 맞춤**: Microsoft 365 Copilot을 [`workflow.md`](starter/workflow.md) "꼭 지킬 것" 7번, `sending-data-to-ai.md`의 채팅 절, [`requirements.md`](starter/requirements/requirements.md) 3절에, CLOVA Studio를 `workflow.md` "꼭 지킬 것" 7번에 반영했습니다. S등급 분기(`workflow.md`)에 'DPA가 민감정보를 적은 도구' 조건을 더해 다섯 가지 조건으로 맞췄습니다. 계약서의 민감정보 문구를 보는 문장([`consent.md`](agency/consent.md) 1부 6절과 점검표, `requirements.md`)에 기관 기준이라고 밝혔고, '위탁'이라고 단정한 문장에는 '학습에 쓰지 않는 기업용 계약이면'이라는 조건을 붙였습니다. 신청 전 정보의 기준을 `consent.md` 1부 1절에 더하고, `AI처리_가능`([`single-source.md`](starter/data/single-source.md))은 동의서를 받았고 목적에 AI 정리가 있고 거부하지 않았을 때만 참으로 좁혔습니다. 양식 C의 AI 업무 예시를 '상담 기록 요약·정리 초안'으로 맞췄습니다.
- **앱과 에이전트 문서에 같은 기준**: [`agent-safety.md`](starter/rules/agent-safety.md), [`ai-features.md`](starter/requirements/ai-features.md), [`messenger-bot.md`](starter/assess/messenger-bot.md), [`agent-browser.md`](starter/assess/agent-browser.md)에 실행 직전 승인, AI 기능을 멈출 사람(AI 활용 담당자와 대리자), 권한 회수와 업체 삭제 요청 기록, 화면 정보의 등급에 맞는 도구를 넣었습니다. 학대 신고자 정보, 피해자의 거처·연락처와 함께 주민등록번호도 AI로 처리하지 않는 정보로 문서 전체에서 맞췄습니다. DPA를 볼 때는 '민감정보를 허용하는가'가 아니라 '민감정보를 처리 대상으로 적었는가'를 확인합니다([`sending-data-to-ai.md`](starter/requirements/sending-data-to-ai.md), [`glossary.md`](starter/reference/glossary.md)). [`consent.md`](agency/consent.md) 3부의 처리방침 AI 조항과 [`DECISION.md`](starter/templates/DECISION.md)에 설명·재검토 요청을 더했습니다.
- **동의 문서를 하나로 합침([`consent.md`](agency/consent.md))**: `agency/consent-guide.md`(동의와 처리방침의 판단 기준)와 `agency/consent-forms.md`(동의서 양식)를 `agency/consent.md` 하나로 합쳤습니다. 1부는 판단 기준(옛 consent-guide 1~8절과 10절이 1부 1~9절), 2부는 동의서 양식 A·B·C, 3부는 처리방침 조항 예시(옛 consent-guide 9절)입니다. 옛 파일 자리에는 안내 파일을 남기지 않았습니다. 앱 문서나 기관 문서가 옛 파일을 가리키면 새 파일과 절 번호로 바꿉니다.
- **앱 판단 문서와 가이드라인을 연결**: [`ethics.md`](starter/assess/ethics.md)에 점수·순위·위험도를 매기는 기능의 사전 검토(원칙 7), 직원 정보를 AI로 분석하기 전 노사 협의, AI가 당사자와 직접 대화하는 기능의 안내(원칙 5), 개발·운영 부담과 원칙 2를 더했습니다. [`forms.md`](starter/assess/forms.md)는 판단이 들어가는 양식을 앱으로 옮길 때 담당자가 판단의 이유를 직접 적는 칸을 두게 했고(원칙 1), 문서 안에서 자기 파일을 가리키던 링크를 '1부', '2부'로 고쳤습니다. [`ai-features.md`](starter/requirements/ai-features.md)의 "사람이 쓰는 칸을 남깁니다"를 원칙 1과 연결했습니다.
- **앱 인수인계서**: 가이드라인이 앱 양식인 [`HANDOVER.md`](starter/templates/HANDOVER.md)를 기관 기록처럼 가리키던 곳을 '앱마다 작성하는 인수인계서'로 고쳤고, [`APP-README.md`](starter/templates/APP-README.md)의 인수인계서·파기 대장 경로를 앱 저장소 루트로 맞췄습니다. 권한 기록 3년 보관을 [`requirements.md`](starter/requirements/requirements.md) 요건 11과 `HANDOVER.md`에 넣었습니다.
- **함께 고친 곳**: [`public-ai-standards.md`](starter/reference/public-ai-standards.md)에 개인정보 처리 통합 안내서, 국가정보원 AI보안 가이드북, 과학기술정보통신부·한국인터넷진흥원 AI 보안 안내서를 더했습니다. AI·클라우드 제공자를 부르던 '사업자'를 '업체'로, 권한·계정의 '주인'을 '소유자'로 맞췄습니다. 「인공지능기본법」의 의무 주체를 가리키는 '제공하는 사업자'는 법 용어라 그대로 두었습니다.

### 이미 만든 앱

판정이 바뀐 도구는 없습니다. Azure OpenAI를 Korea Central에서 쓴다면 배포 유형이 Global인지 확인하고, Global이면 처리방침에 국외이전으로 적습니다. 앱의 [`HANDOVER.md`](starter/templates/HANDOVER.md)에 권한을 주고 회수한 기록의 위치를 적고 3년 이상 보관합니다. 명부의 `AI처리_가능`이 동의서를 받기 전(의뢰·발굴 단계)에는 거짓이 되도록 앱의 판정을 확인합니다. 양식 C를 쓰고 있다면 AI 업무 예시와 민감정보 처리 목적을 새 문구로 바꿉니다. 활동 사진을 AI로 변환한다면 동의서(양식 A ②)나 신청서(양식 B)에 AI 변환과 국외이전 동의 칸을 더합니다. 기관 규정이나 앱 문서가 가이드라인의 '원칙 N'을 인용했다면 새 번호로 바꿉니다(정보 2→4, 당사자 4→5). [`HANDOVER.md`](starter/templates/HANDOVER.md)에 AI 기능을 끄는 방법과 끌 수 있는 사람을 적습니다.

## 1.5 기관 AI 가이드라인과 정보 등급별 도구 고르기 (2026.10)

- **새 문서 [`ops/ai-guideline-sample.md`](agency/ai-guideline.md)**: 기관 전체에 쓰는 「AI 윤리·활용 가이드라인」 샘플입니다. 1부 윤리 원칙(일곱 가지 원칙과 운영), 2부 직원이 지킬 것(법률 용어 없이 행동만), 3부 기관·담당자가 챙길 것(AI 사용 목록, 동의와 처리방침, 계정 보안, 사고 대응, 지자체 위탁 사무, 작은 기관), 부록(조문형 규정, 1분 점검표, Q&A, 용어 풀이)으로 나눴습니다. 개인 계정은 업무에 쓰지 않고, 기관이 계정·결제 수단·업무 시간을 제공합니다. 보관과 AI 분석은 따로 판단합니다. 개발자, 정보보안, 개인정보·법률, 인권, 학계, 현장(사회복지사, 생활복지사, 기관장, 당사자·보호자, 지자체 공무원) 관점의 검토를 반영했습니다.
- **정보 등급별 도구 고르기([`ai-send.md`](starter/requirements/sending-data-to-ai.md) "도구 고르기")**: AI에 보내기 전에 정보 등급을 정하고, 그 등급을 계약으로 받는 도구를 고릅니다. 당사자에게서 받을 것(민감정보 동의)과 회사 계약에서 확인할 것은 따로 보며 서로를 대신하지 않습니다. 민감정보까지는 계약에 민감정보 처리가 들어 있는 도구(기관 Workspace의 Gemini와 채팅형 Gemini 앱, 결제를 연결한 Gemini API, Azure OpenAI, AWS Bedrock)이고, ChatGPT Business·Claude Team과 OpenAI·Anthropic API 직접 계약은 표준 DPA가 민감정보를 전제로 하지 않으므로 일반 개인정보까지입니다. 무료 서비스와 결제를 연결하지 않은 API 키에는 개인정보를 넣지 않습니다. 정부 요구에 따른 공개 조항은 회사마다 같아서 기준이 아닙니다.
- **채팅형 AI(1.4.2 정정)**: "채팅형 AI에는 사례 기록 원문을 넣지 않는다"를 바꿨습니다. 기관 Workspace 계정의 Gemini는 민감정보까지 다룰 수 있고, 그 밖의 채팅에는 칸에 맞는 정보만 넣습니다. 채팅에서는 서버 확인이 없으므로 담당자가 동의 표시를 확인하고, 제3자는 관계만 남기고, 피드백을 보내지 않습니다.
- **서비스별 주의점 확인(2026-10-27)**: Gemini API 유료는 오남용 감시로 55일 보관하고 안전 필터에 걸린 내용은 Google 직원이 볼 수 있습니다. Azure OpenAI는 Microsoft DPA가 특별범주를 처리 범위에 넣고 입력이 OpenAI로 가지 않지만, 미리보기·Bing 검색 연결·Web IQ에는 DPA가 적용되지 않고 오남용 감시에 걸린 대화는 Microsoft 직원이 볼 수 있습니다. 비영리 Azure 크레딧(연 2,000달러)도 같은 약관입니다. Workspace 비영리판은 Gemini 앱을 핵심 서비스로 받습니다.
- **`masking.md` → [`ai-send.md`](starter/requirements/sending-data-to-ai.md)**: 마스킹은 의무가 아닌 선택 사항이고 핵심은 보내기 전의 확인이라서 이름을 바꾸고, 마스킹 설계는 "선택: 보내는 정보 줄이기(마스킹)" 절로 내렸습니다. 옛 이름의 파일에는 옮긴 곳만 남겼습니다.
- **함께 고친 곳**: [`workflow.md`](starter/workflow.md) "꼭 지킬 것" 7번과 [`chat-prompt.md`](starter/workflow.md), [`requirements.md`](starter/requirements/requirements.md) 3절, [`consent-notes.md`](agency/consent.md) 1절, `masking.md`를 가리키던 링크 전체.
- **이미 만든 앱**: OpenAI·Anthropic 표준 계약으로 민감정보를 보내고 있다면 "민감정보까지" 칸의 도구로 옮기거나 별도 계약 조건을 확인합니다. Gemini API 키가 결제를 연결한 프로젝트의 키인지 확인합니다. 오남용 감시 기록과 회사 직원의 검토 가능성을 동의서와 처리방침에 사실대로 적었는지 확인합니다. [`DECISION.md`](starter/templates/DECISION.md)와 문서의 `masking.md` 링크는 `ai-send.md`로 바꿉니다.

### 1.5.1 폴더와 파일 이름 정리, 제품별 표 재확인 (2026.10)

판단 기준은 1.5와 같고, 사람이 읽고 찾기 쉽게 구조를 바꿨습니다. 옮긴 자리에 안내 파일은 남기지 않았습니다.

- **기관 문서는 [`agency/`](agency/)로**: 기관에 하나만 두는 가이드라인과 동의서를 앱마다 채우는 양식과 나눴습니다. `agency/`는 앱 폴더로 복사하지 않습니다.
  - `ops/ai-guideline-sample.md` → [`agency/ai-guideline.md`](agency/ai-guideline.md)
  - `ops/consent-form-intake.md`, `ops/consent-form-sample.md` → [`agency/consent-forms.md`](agency/consent.md)의 양식 A·B·C
  - `ops/consent-notes.md` → [`agency/consent-guide.md`](agency/consent.md). 처리방침 조항 예시는 9절로 옮김
- **앱마다 채우는 양식은 [`starter/templates/`](starter/templates/)로**: `ops/handover.md` → [`HANDOVER.md`](starter/templates/HANDOVER.md), `ops/destruction-log.md` → [`DESTRUCTION-LOG.md`](starter/templates/DESTRUCTION-LOG.md). `ops/` 폴더는 없어졌습니다.
- **합친 파일**
  - `starter/chat-prompt.md`는 [`workflow.md`](starter/workflow.md) 본문을 복사한 파일이라 지우고, 채팅용 규칙은 workflow.md의 "채팅창에서 쓸 때" 절로 옮겼습니다. 채팅에서는 workflow.md 전체를 붙입니다.
  - `starter/platform-facts.md` → workflow.md의 "바뀔 수 있는 플랫폼 정보" 절
  - `starter/assess/form-audit.md`, `form-to-app.md` → [`forms.md`](starter/assess/forms.md)의 1부·2부
- **찾아보는 자료는 [`starter/reference/`](starter/reference/)로**: `glossary.md`, `public-ai-standards.md`, `resources.md`
- **줄임말 이름을 풀어 씀**
  - `requirements/ai-send.md` → [`sending-data-to-ai.md`](starter/requirements/sending-data-to-ai.md), `requirements/ai.md` → [`ai-features.md`](starter/requirements/ai-features.md). `requirements/masking.md` 안내 파일은 지웠습니다.
  - `assess/agent.md` → [`messenger-bot.md`](starter/assess/messenger-bot.md), `assess/screen-agent.md` → [`agent-browser.md`](starter/assess/agent-browser.md)
  - `rules/gas.md` → [`apps-script.md`](starter/rules/apps-script.md), `gcp.md` → [`google-cloud.md`](starter/rules/google-cloud.md), `cf-only.md` → [`cloudflare.md`](starter/rules/cloudflare.md), `cf-supabase.md` → [`cloudflare-supabase.md`](starter/rules/cloudflare-supabase.md), `agentic.md` → [`agent-safety.md`](starter/rules/agent-safety.md)
  - `data/ssot.md` → [`single-source.md`](starter/data/single-source.md)
- **AI 처리 안내와 거부를 문서 전체에서 맞춤**: 가이드라인과 [`sending-data-to-ai.md`](starter/requirements/sending-data-to-ai.md)의 "'AI 분석 동의' 표시 확인"을 "AI 처리 거부 표시가 없는지, 민감정보면 민감정보 동의가 있는지 확인"으로 바꿨습니다. 민감정보가 없는 기록은 `동의_민감정보`가 없어도 보낼 수 있습니다. 명부 필드 `AI처리_가능`, `동의_민감정보`, `동의_확인일`의 정의를 [`single-source.md`](starter/data/single-source.md)에 두고, 비어 있으면 거짓으로 봅니다.
- **남용을 막는 장치**: AI를 쓰는 업무를 수집 목적과 처리방침에 좁혀 적고(예측·분류·점수에는 쓰지 않음), 동의서에 'AI 처리를 원하지 않음' 칸을 두고, 거부하지 않았어도 등급에 맞는 도구에 필요한 만큼만 보내고, 연 1회 목록 밖 사용과 거부자 수를 점검합니다. 오남용 감시 기록이 남는 서비스는 그 사실을 동의서와 처리방침에 적습니다. 철회했을 때의 처리를 동의서 참고 1에 더했습니다.
- **제품별 표 재확인(2026-10-28, [`sending-data-to-ai.md`](starter/requirements/sending-data-to-ai.md) "도구 고르기")**: 칸을 가르는 기준을 "계약(DPA)이 민감정보를 처리 대상으로 적고 있는가"로 못 박고, 각 회사 DPA 원문을 다시 읽어 줄마다 확인일을 적었습니다.
  - **Gemini API 유료 → 일반 개인정보까지.** 1.5에서 Cloud DPA가 적용된다고 적었지만, 약관상 유료 Gemini API에는 Cloud DPA가 아니라 「Data Processing Addendum for Products Where Google is a Data Processor」가 적용되고 이 DPA에는 민감정보 문구가 없습니다.
  - **AWS Bedrock → 일반 개인정보까지.** AWS DPA에는 민감정보를 빼는 문구도 넣는 문구도 없습니다. 1.5는 "제외 조항 없음"을 민감정보 허용으로 읽었습니다.
  - **Gemini Enterprise Agent Platform(옛 Vertex AI) → 민감정보까지.** Google Cloud Platform 서비스라 Cloud DPA가 적용됩니다. 앱에서 Gemini로 민감정보를 다룰 때는 이 경로를 씁니다.
  - Workspace의 Gemini(Gemini 앱, Gemini Notebook 포함)와 Azure OpenAI는 그대로 "민감정보까지"입니다. OpenAI DPA(v.010126)와 Anthropic DPA(2025-02-24)의 문구도 바뀌지 않았습니다.
  - **저장과 AI 분석을 한 장으로([`ai-guideline.md`](agency/ai-guideline.md) 3부 1장)**: "어디에 저장할 수 있나"와 "어디서 AI로 분석할 수 있나" 두 표를 민감정보(S)·일반 개인정보(P) 칸으로 나눠 두었습니다. 둘 다 위탁이므로 같은 기준(계약이 민감정보를 맡는가)을 씁니다. 저장소도 확인했습니다: Supabase DPA는 민감정보를 정의하고 기관이 동의를 받을 책임을 적고, Firebase 데이터 처리 약관은 특별범주를 포함합니다. 민감정보를 저장할 때도 위탁 계약과 안전조치를 확인하도록 가이드라인 2장과 [`consent-guide.md`](agency/consent.md) 6절을 보완했습니다.
  - **Agent Platform 익스프레스 모드 키는 개인정보 금지**: 같은 Gemini Enterprise Agent Platform이라도 익스프레스 모드(무료 90일 체험, @gmail.com 계정)는 약관 3.2가 개인정보 처리를 금지합니다. 민감정보는 기관 Google Cloud 프로젝트에 결제를 연결하고 만든 키나 서비스 계정으로만 보냅니다.
  - **키 발급과 호출 방식([`sending-data-to-ai.md`](starter/requirements/sending-data-to-ai.md) "앱에서 부를 때")**: 앱을 만드는 AI가 그대로 따를 수 있게 Google은 제품별 키를 만드는 곳·인증·호출 주소·적용 계약을 표로 나누고, Agent Platform 키 발급 순서(기관 프로젝트, 결제, 서비스 계정, 운영은 ADC, SDK 환경 변수)를 적었습니다. Azure는 플레이그라운드가 아니라 앱 서버가 배포의 엔드포인트와 키로 부르는 경우가 "민감정보까지"이고, 정식 모델만 쓰며 웹 검색(Bing)과 미리 보기 기능을 끄고, 배포 유형(글로벌·데이터 영역·Regional Provisioned)별 처리 위치를 적었습니다.
  - **이름 짓기([`ai-guideline.md`](agency/ai-guideline.md) 원칙 5, 2부, 1분 점검표)**: '수혜자 관리' 같은 나쁜 예만 들고 바꿔 쓸 말은 제시하지 않습니다. 호칭은 기관이 직원·당사자와 정합니다. [`design.md`](starter/requirements/design.md)의 동사 예시 단어도 뺐습니다.
  - **추론 위치 표도 다시 확인(2026-10-28)**: 서울에서 처리를 보장하던 Gemini 2.5 Flash가 2026-10-20에 종료되어 Gemini Enterprise Agent Platform 서울은 사실상 한국 안 처리가 되지 않습니다. 한국 안 추론이 되는 경로는 Bedrock 서울의 Claude Opus 5·Sonnet 5(구조화 출력 미지원)와 Azure Regional Provisioned 배포뿐입니다. Anthropic은 저장 위치도 미국만 있습니다.
  - 함께 고친 곳: [`ai-guideline.md`](agency/ai-guideline.md)의 AI 사용 목록과 마스킹 Q&A, [`workflow.md`](starter/workflow.md) "꼭 지킬 것" 7번과 플랫폼 정보, [`requirements.md`](starter/requirements/requirements.md), [`messenger-bot.md`](starter/assess/messenger-bot.md)
- **고친 오기**: AI 동의서 "네 항목"(실제 세 항목), "1.4까지 `ai-send.md`였습니다"(실제 `masking.md`)
- **이미 만든 앱**: 앱 폴더의 `starter/`는 복사한 때의 기준으로 남아 있어 링크가 깨지지 않습니다. 새 기준을 쓰려면 `starter/`를 새로 복사하고, 앱 폴더에 복사해 둔 `ops/`의 동의서·가이드라인 사본은 지우고 기관 원본으로 연결합니다. 이용자 명부에 `동의_확인일`을 더합니다.

### 1.5.2 권장안과 용어 사전 (2026.11)

- **권장안과 용어 사전([`workflow.md`](starter/workflow.md) "꼭 지킬 것" 3번, [`design.md`](starter/requirements/design.md))**: 기관이 정할 것(실천 원칙, 보관 기간, 동의, 법적 판단)을 물을 때 AI는 권장안을 붙이지 않고 선택지와 근거만 보여 줍니다. 기관 용어 사전이 있으면 AI는 화면, 데이터 항목, 출력물에 들어갈 말이 사전과 다를 때 짚고 어느 말로 할지 묻습니다. 대화에서 쓰는 말은 짚지 않습니다.
- **기록 속 가족·이웃 정보의 근거 정정**: 제20조를 동의가 필요 없는 근거처럼 쓴 문장을 고쳤습니다. 제20조는 근거가 아니라 그 사람이 요구할 때 출처와 목적을 알리는 의무이고, 처리 근거는 제15조 제1항에서 따로 찾습니다. 가족의 건강·장애 정보는 [`consent-guide.md`](agency/consent.md) 8절에 기준을 더했습니다. 가족 본인의 동의를 받거나, 희망이음에 기록할 때의 법령 근거(「사회보장급여법 시행령」 제28조 제4항)를 씁니다. 함께 고친 곳: [`workflow.md`](starter/workflow.md) "꼭 지킬 것" 9번과 판정 절차, [`ethics.md`](starter/assess/ethics.md), consent-guide.md 1절.
- **계약이 주는 보호**: [`ai-guideline.md`](agency/ai-guideline.md) 3부 2장에 기관이 회사와 계약하면 받는 보호(제26조 제4항~제7항)와 개인 계정과의 차이를 더하고, 원칙 3에서 그 절로 잇습니다.
- **학대 신고자·피해자 거처의 근거 보완**: [`sending-data-to-ai.md`](starter/requirements/sending-data-to-ai.md) 5번에 장애인복지법 제59조의6, 아동학대처벌법 제35조 제3항, 가정폭력처벌법 제18조 제3항을 더하고, 법이 AI 사용을 따로 금지한 것은 아니며 기관 기준으로 보내지 않는 이유를 적었습니다.
- **가이드라인은 정답이 아닌 예시**: 가이드라인 머리말에 정부 가이드와 함께 보고 기관의 기준을 만들라는 안내를 더하고, [`public-ai-standards.md`](starter/reference/public-ai-standards.md)에 「복지·돌봄 AI 대전환 로드맵」(보건복지부, 2026.10)과 「정신건강 목적 생성형 AI 이용 가이드라인」(보건복지부·대한신경정신의학회, 2026.10)을 더했습니다.
- **'회사'를 '업체'로**: AI·클라우드 서비스를 제공하는 쪽을 '업체'로 통일했습니다. '회사'라고 쓰면 기관과 헷갈릴 수 있습니다. 앞 버전 기록의 표현은 그대로 둡니다.

## 1.4 AI로 보내는 기록의 국외이전 근거 정정 (2026.10)

- **국외이전 근거([`consent-notes.md`](agency/consent.md) 1절)**: "AI 분석을 위한 전송은 국외이전 동의를 받아야 한다"는 틀렸습니다. 개인정보 보호법 제28조의8은 보관과 AI 처리를 나누지 않습니다. 업체가 입력을 학습에 쓰지 않고 계약이 있는 이용자와 직원의 정보를 그 서비스를 위해 맡긴다면, 클라우드 보관과 같이 처리방침 공개(제1항 제3호)로 됩니다. 학습에 쓰는 업체에 주면 위탁이 아니라 제3자 제공이라 동의가 필요합니다(대법원 2016도13263). 국외이전 동의(제1호)는 설문 응답자처럼 기관과 계약이 없는 사람의 정보에만 받습니다. "거부를 들어줄 수 있으면 동의로 받는다"는 기준은 법에 없어서 뺐습니다. 제3호로 처리해도 거부 방법과 효과는 알려야 합니다(제2항 제5호). 이 규칙은 `consent-notes.md` 1절에만 자세히 적고, 다른 문서에는 결론과 링크만 둡니다.
- **동의서 양식([`consent-form-intake.md`](agency/consent.md), [`consent-form-sample.md`](agency/consent.md))**: AI 국외이전 동의 항목을 뺐습니다. 국외 처리 사실과 거부 방법은 안내로 알립니다. 한 장 양식은 ⑥ 안내 사항이 ⑤가 되었고 그 안에 "AI 처리" 항목을 넣었습니다. 별도 양식은 ① AI 활용 안내에 넣었고, ④ 민감정보가 ③이 되었습니다. 처리방침 예시도 제3호 하나로 고쳤습니다.
- **서버 확인([`masking.md`](starter/requirements/sending-data-to-ai.md))**: 명부 필드 `동의_AI분석`을 `AI처리_가능`으로 바꿨습니다. 이용자가 AI 처리를 거부하지 않았으면 참입니다.
- **민감정보 근거([`consent-notes.md`](agency/consent.md) 1절)**: 민감정보는 동의가 아니어도 법령이 허용하면 처리할 수 있습니다(제23조 제1항 제2호). 사회보장급여법·노인복지법·장애인복지법 시행령에 국가·지자체와 그 업무를 위탁받은 기관의 정해진 사무에 건강정보 처리를 허용하는 조항이 있습니다. 기관이 스스로 하는 상담과 사례관리는 대개 해당하지 않으므로 민감정보 동의를 받습니다.
- **AI에 보내지 않는 정보와 쓰는 순서([`masking.md`](starter/requirements/sending-data-to-ai.md) 5번, [`ai.md`](starter/requirements/ai-features.md))**: 학대를 신고한 사람의 정보와 피해자가 머무는 곳·연락처는 조건을 모두 갖춰도 AI에 보내지 않습니다(아동학대처벌법 제10조 제3항, 노인복지법 제39조의6 제3항). 상담 기록과 사례 기록은 담당자가 먼저 쓰고, AI는 요약하고 다듬는 일을 돕습니다.
- **함께 고친 곳**: [`workflow.md`](starter/workflow.md)의 "꼭 지킬 것" 5·7번, S등급 판정, 5절 제목("AI 분석은 전송 조건과 사람의 판단을 전제로 합니다"), [`requirements.md`](starter/requirements/requirements.md), [`ai.md`](starter/requirements/ai-features.md), [`screen-agent.md`](starter/assess/agent-browser.md), [`agent.md`](starter/assess/messenger-bot.md), [`glossary.md`](starter/reference/glossary.md), [`DECISION.md`](starter/templates/DECISION.md).
- **업체 계약 비교 정정([`masking.md`](starter/requirements/sending-data-to-ai.md), [`requirements.md`](starter/requirements/requirements.md))**: Anthropic 표준 DPA도 OpenAI처럼 민감정보를 받는 것을 전제로 하지 않습니다(처리 설명 B.3 "None"). 이전에는 고객이 작성하는 항목이라고 잘못 적었습니다. AWS Bedrock(민감정보 제외 조항 없음, 학습 미사용, 기본 무보관)을 비교표에 더했습니다.
- **개인정보보호위원회 안내서(1.4.1, [`consent-notes.md`](agency/consent.md) 1절·6절)**: "AI만 따로 다룬 개인정보보호위원회 해석은 아직 없다"는 틀렸습니다. 「생성형 AI 개발·활용을 위한 개인정보 처리 안내서」(2025.8)가 상용 AI API를 기업용 계약으로 쓰는 것을 처리위탁으로 보고, 국외이전 근거로 처리방침 공개(제1항 제3호)를 듭니다. 1.4의 판단과 같습니다. 2026년 4월 개정된 「개인정보 처리방침 작성지침」에 맞춰 6절 점검 항목에 AI 처리 내용(보관 기간, 학습 미사용, 거부 절차, 챗봇 답변 이의 제기)을 더했습니다.
- **참고 문서 [`starter/public-ai-standards.md`](starter/reference/public-ai-standards.md)(1.4.1)**: 공공 AI와 클라우드 기준(개인정보보호위원회 안내서와 지침, 행정안전부 공공부문 인공지능 윤리기준, 대한민국 인공지능 윤리원칙, 인공지능기본법, CSAP와 그 개편)이 무엇이고 사회복지 기관과 어떤 관계인지 적었습니다. 공공은 보안 체계 안에서 AI를 쓰고 민간 기관은 그 밖에서 쓰므로 공공 기준을 그대로 옮기지 않았습니다. 판정 절차에서는 쓰지 않는 참고 문서라서 보완(1.4.1)으로 넣었습니다. CSAP가 국가정보원 보안검증으로 합쳐지는 개편에 맞춰 [`glossary.md`](starter/reference/glossary.md), [`platform-facts.md`](starter/workflow.md), [`consent-form-sample.md`](agency/consent.md) 참고 5의 설명도 고쳤습니다.
- **보안 점검 순서(1.4.2, [`agentic.md`](starter/rules/agent-safety.md))**: 보안 점검은 먼저 보고만 하고, 사용자가 승인한 항목만 고치고, 다시 점검합니다. AI는 "안전"이라고 판정하지 않고 "확인함·확인 필요·위험·해당 없음"과 근거를 적으며, 기능마다 "로그인하지 않은 사람"과 "다른 사용자"가 무엇을 볼 수 있는지 표로 보여 줍니다. 점검은 시험용 사이트에서만 합니다.
- **Apps Script 공개 범위(1.4.2, [`gas.md`](starter/rules/apps-script.md))**: 이름이 `_`로 끝나지 않는 전역 함수는 화면에서 부를 수 있으므로 쓰지 않는 함수는 비공개로 둡니다. 비밀값을 돌려주는 함수를 만들지 않고, 공개 웹앱과 관리 기능은 다른 프로젝트로 나누고, 시트에 쓰는 글자의 수식 실행을 막고, 끝난 웹앱은 배포를 보관 처리합니다.
- **사고 대응과 이상 징후 알림(1.4.2, [`handover.md`](starter/templates/HANDOVER.md), [`requirements.md`](starter/requirements/requirements.md) 8절)**: 인수인계서의 장애 대응에 유출 사고 보고 체계, 72시간 통지·신고 요건, 알림을 받는 사람, 마지막 보안 점검일을 더했습니다. 접근 로그는 월 1회 점검에 더해 로그인 실패 급증, 대량 조회·내보내기, 관리자 권한 변경을 알리게 합니다.
- **채팅형 AI(1.4.2, [`masking.md`](starter/requirements/sending-data-to-ai.md))**: 직원이 채팅창에 기록을 붙여 넣을 때는 서버 확인과 전송 기록을 갖출 수 없으므로, 기관이 승인한 계정에서만 쓰고 실명과 연락처와 사례 기록 원문을 넣지 않습니다.
- **읽을거리([`resources.md`](starter/reference/resources.md), 1.4.2)**: 김종원 선생님의 「사회복지기관 DX·AX 전략서」를 더했습니다. 국외이전을 동의로 받는 쪽을 권하는 부분이 1.4와 다르다는 점을 함께 적었습니다. 안전사용 가이드 소개에도 AI 전송을 동의로 처리한다는 설명이 1.4와 다르다는 점을 밝혔습니다.
- **남이 만든 앱을 받아 쓸 때(1.4.3, [`workflow.md`](starter/workflow.md) "판단을 마친 뒤", `AGENTS.md` 1번, 플러그인 스킬)**: 채워진 `DECISION.md`가 있으면 다시 판정하지 않는다는 규칙에 예외를 두었습니다. 다른 기관에서 받은 앱이면 실천 원칙, 등급과 보관 기간, 권한, 동의서와 처리방침의 위치, 보호책임자처럼 기관마다 다른 항목은 받은 기관의 기준으로 다시 판정합니다. 만든 사람의 계정과 주소가 코드에 남아 있는지 확인하고, 처리방침에 회사를 적고, 보안 점검을 한 번 합니다. 앱을 나눠 줄 때의 준비도 함께 적었습니다.
- **쓰기 시작한 뒤에 볼 것(1.4.3)**: 통계 화면에는 언제부터 모은 자료인지, 입력하지 않은 담당자가 몇인지, 항목을 바꾼 날을 함께 보여 주고, 기록이 적은 것을 실적이 적은 것으로 읽지 않습니다([`ssot.md`](starter/data/single-source.md)). 인수인계서의 기관 캘린더에 사용 점검을 더했습니다. 종이와 대리 입력 비율, 앱 밖에서 따로 입력되는 비율, 잘못 입력된 값이 몰리는 칸을 보고, 잘못 입력된 값은 화면이 어렵다는 신호로 읽습니다([`handover.md`](starter/templates/HANDOVER.md)). 시작 전 확인의 "독자"에는 입력하는 사람도 얻는 것이 있는지를, 마이그레이션 시점에는 쓰는 사람이 지금 화면에 익숙해졌는지를 더했습니다([`workflow.md`](starter/workflow.md)).
- **공공에서 직접 만드는 흐름과 도구(1.4.4, [`public-ai-standards.md`](starter/reference/public-ai-standards.md), [`resources.md`](starter/reference/resources.md))**: 행정안전부 AI 정부 실험실을 적었습니다. 공무원도 민간 AI 도구로는 공개 자료만 다루고 내부 데이터는 업무망 안에서 쓴다는 점, 산출물을 프롬프트와 함께 공공 GitLab에 등록한다는 점입니다. 발표 예정인 공공 AX 업무 지침(가칭)을 기준 표에 더했습니다. 현장 공무원이 만든 `korean-law-mcp`, `kordoc`, 복지정보MCP를 만들 때 쓰는 도구에 더했습니다. MCP 서버는 필요한 대화에서만 켜고, 질문에 이용자 정보를 넣지 않고, 개인이 운영하는 공개 서버는 앱이 실행 중에 부르지 않고 원래 API를 씁니다.
- **기관 용어 사전(1.4.5, [`design.md`](starter/requirements/design.md), [`DECISION.md`](starter/templates/DECISION.md))**: 앱의 메뉴와 버튼 이름을 짓기 전에 기관이 쓰는 말을 한곳에 정해 두기를 권했습니다. 사람을 부르는 말, 업무 동사, 상태값부터 쓰는 말과 쓰지 않는 말과 이유를 적고, 직원과 당사자가 함께 정하고, 기관에 하나만 둡니다. 판정을 정리할 때 AI가 용어 사전이 있는지 묻고, 없으면 첫 앱의 이름 목록을 기관에서 합의해 첫 사전으로 삼습니다. 읽을거리에 「성민복지용어사전」을 기관의 말을 정한 예로 더했습니다. 실린 용어는 그 기관의 기준이므로 AI가 그 말을 추천하지 않습니다.
- **이미 만든 앱**: AI 전송에 국외이전 동의를 받고 있어도 위법은 아닙니다. 동의서에서 빼려면 처리방침의 국외이전 조항에 AI 회사와 거부 방법을 적고, 안내 사항에 AI 처리 항목을 넣고, 명부 필드를 `AI처리_가능`(거부하지 않았으면 참)으로 바꿉니다. 전에 동의하지 않은 이용자는 거부한 것으로 둡니다. 지자체에서 위탁받은 사무라면 민감정보의 법령 근거를 확인합니다. AI에 보내는 칸에 신고자 정보나 피해자의 거처·연락처가 섞여 있지 않은지 확인합니다. Anthropic API로 S등급 기록을 보내고 있다면 별도 계약 조건을 확인합니다.

## 1.3 근태·급여와 전자결재를 직접 만들 때의 기준 (2026.10)

- **증거급 기록의 판정([`workflow.md`](starter/workflow.md))**: "무결성 요구가 낮은 기능부터 적용한다"를 뺐습니다. 근태·급여와 전자결재를 직접 만든다면 처음 설계할 때 8개 원칙을 넣고, 운영 전에 "최종 확인"의 질문에 답할 수 있게 한 뒤 전문가 검토를 한 번 받습니다. 기성 제품을 먼저 검토하는 것은 그대로입니다.
- **[`record-integrity.md`](starter/data/record-integrity.md)**: 실무자가 먼저 정할 것을 맨 앞에 두고, 원칙마다 쉬운 설명과 구현을 나눴습니다. 목표는 외부 감사에게 승인된 문서가 그대로이고, 바꿀 일은 취소와 새 기안으로 처리했으며, DB를 직접 고치지 않았다고 보여 줄 수 있는 수준입니다. 승인된 문서는 고치지 않고, 바꿀 일이 생기면 취소 상태와 사유를 남긴 뒤 다음 번호로 새로 기안합니다. 근태·급여는 확정 내역과 급여명세서를 직원 개인 메일로 보내는 것으로 보관 등급 4의 외부 확인을 갖출 수 있고, hash는 직원에게 보낼 수 없는 기록에만 더합니다. 기관 메일과 기관 Slack은 기관 관리자가 관리하므로 이 사본이 되지 못합니다. 이사장·감사·지자체에 hash를 보내는 방법은 뺐습니다.
- **[`DECISION.md`](starter/templates/DECISION.md)**: 증거로 쓰는 기록에 승인된 문서를 바꿀 때의 절차를 적는 칸을 더했습니다.
- **이미 만든 앱**: 증거급 기록을 직접 만들었다면 승인된 문서를 고치거나 지우는 기능이 있는지 확인하고, 있으면 취소와 새 기안으로 바꿉니다. 그 절차를 [`DECISION.md`](starter/templates/DECISION.md)에 적습니다. 기관 밖으로 hash를 보내고 있다면 그대로 써도 됩니다.

## 1.2 에이전트 브라우저로 정부 업무 시스템 동기화 (2026.09)

- **새 문서 [`starter/assess/screen-agent.md`](starter/assess/agent-browser.md)**: Aside 같은 에이전트 브라우저로 정부 업무 시스템(희망이음 등)과 기관 앱·시트를 동기화할 때 적용합니다. 쓰기 전 확인(운영 기관 약관, 위수탁 협약, DPA와 동의, 개인 구독 금지, 계정·인증), 원본 정하기, 운영 순서(동작 확인, 대조만, 소량 시험, 확대), 지시문에 넣을 것, Aside 설정의 주의점을 담았습니다. 공개 사례가 없어 사용법이 아니라 주의점으로 적었습니다.
- **[`masking.md`](starter/requirements/sending-data-to-ai.md)**: AI 전송 제외 대상을 정부 업무 시스템(희망이음 등)에서 받은 자료로 정리하고, 에이전트 브라우저로 화면을 읽는 것도 같은 확인을 거치게 했습니다. 추론 위치 표를 2026-09-30 기준으로 고쳤습니다. 업체의 자체 API로는 한국 안에서만 추론할 수 없지만, Bedrock 서울의 Claude Opus 5·Sonnet 5처럼 클라우드를 거치는 일부 모델은 가능합니다. 옛 장애등급(1~6급)은 장애 정도로 적습니다.
- **[`requirements.md`](starter/requirements/requirements.md), [`gas.md`](starter/rules/apps-script.md)**: 웹훅 요건을 더했습니다. payload에는 ID만 싣고, HMAC 서명을 검증하고(Standard Webhooks), 이벤트 ID로 멱등 처리합니다. GAS `doPost(e)`는 헤더를 읽지 못하므로 서명은 Cloudflare Workers에서 검증합니다. 접속기록은 2026년 11월 1일부터 개인정보처리시스템에 접속한 모든 사람(정보주체 제외)이 대상이고, 점검 주기는 내부 관리계획에서 정합니다.
- **[`design.md`](starter/requirements/design.md)**: 화면을 읽는 AI 에이전트에 대비해 서버 검증, 재확인 단계, 접근 로그를 둡니다.
- **이미 만든 앱**: 에이전트 브라우저를 쓰면 원본, 운영 기관 약관·위수탁 협약 확인 결과, 사람이 누르는 버튼(저장, 제출, 결재 요청), 작업 로그 위치를 [`DECISION.md`](starter/templates/DECISION.md)에 적습니다. 웹훅을 쓰면 payload에 개인정보가 없는지 확인합니다. 접속기록에 기관 관리자와 수탁자의 접속도 남는지, 점검 주기가 내부 관리계획에 있는지 확인합니다. 협약의 국외 반출 제한 때문에 AI 기능을 뺐다면 [`masking.md`](starter/requirements/sending-data-to-ai.md)의 추론 위치 표를 다시 봅니다.

## 1.1 보호 기준 강화, 운영하고 있는 앱에 반영하는 일은 사람이 승인 (2026.09)

- **데이터 등급([`workflow.md`](starter/workflow.md))**: S등급에 생체정보와 주민등록번호를 넣고, 만 14세 미만 아동의 정보에는 법정대리인 동의가 필요합니다. 학대 이력과 가족 관계는 민감정보에 준해 보호합니다. 민감정보가 있는 작은 앱의 경로 세 가지와 구글 시트에 S등급을 둘 때의 조건을 정했습니다.
- **동의([`ops/consent-notes.md`](agency/consent.md), [`ops/consent-form-intake.md`](agency/consent.md))**: 클라우드 보관은 처리방침 공개(국외 처리위탁)로, AI API 전송은 국외이전 동의로 나눴습니다. 동의서 참고 양식에 AI 처리 항목과 거부 시 대체 처리를 넣었습니다.
- **AI 기능([`ai.md`](starter/requirements/ai-features.md))**: 통계를 말로 묻는 기능은 AI 도구에 집계 함수만 노출하고 숫자만 받습니다.
- **운영하고 있는 앱에 반영([`agentic.md`](starter/rules/agent-safety.md))**: 운영하고 있는 앱에 반영하는 일과 DB를 바꾸는 일은 사람이 승인하고 AI가 실행합니다. `.claude/settings.json`에 확인 규칙을 둡니다.
- **맨 앞 요약**: [`workflow.md`](starter/workflow.md) 맨 앞에 "꼭 지킬 것"을, [`DECISION.md`](starter/templates/DECISION.md) 맨 앞에 "기관의 실천 원칙"을 두었습니다.
- **이미 만든 앱**: 동의서를 [`ops/consent-form-intake.md`](agency/consent.md)와 비교하고, `.claude/settings.json` 확인 규칙이 없으면 넣고, [`DECISION.md`](starter/templates/DECISION.md) 맨 앞에 실천 원칙을 적습니다.

## 1.0 템플릿·플러그인·채팅 (2026.09)

- **사용법**: 같은 문서를 템플릿(Use this template), 플러그인, 채팅([`starter/chat-prompt.md`](starter/workflow.md))의 세 가지로 씁니다.
- **새 문서**: [`form-to-app.md`](starter/assess/forms.md)(HWP 양식에서 앱까지), [`ai.md`](starter/requirements/ai-features.md)(AI 기능 요건), [`agent.md`](starter/assess/messenger-bot.md)(Slack 봇 등 기관 공용 AI). [`design.md`](starter/requirements/design.md)에 부르는 말과 이름 기준을 더했습니다.

## 1.0 이전 (2026.08~09)

[`workflow.md`](starter/workflow.md) 판단 절차, [`form-audit.md`](starter/assess/forms.md), [`ssot.md`](starter/data/single-source.md), [`record-integrity.md`](starter/data/record-integrity.md)(보관 등급), [`levels.md`](starter/data/levels.md)(데이터 관리 다섯 단계), [`ethics.md`](starter/assess/ethics.md), [`design.md`](starter/requirements/design.md), [`print.md`](starter/requirements/print.md), [`masking.md`](starter/requirements/sending-data-to-ai.md)를 차례로 두었습니다. 자세한 내용은 커밋 이력에 있습니다.
