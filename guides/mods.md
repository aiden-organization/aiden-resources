# Claude Code 모드 만들기·설치하기 실습 가이드

영상에서 사용한 프롬프트와 소개한 모드의 설치 방법을 모았습니다. 컨텍스트 패널을 직접 만든 뒤, 필요한 모드를 골라 사용해보세요.

확인 기준: 2026년 10월 9일. 앱과 모드 업데이트에 따라 화면이나 설치 방식이 달라질 수 있습니다.

## 1. 시작하기 전에

실습은 **클로드 데스크톱 앱의 코드(Code) 탭**에서 진행합니다. 일반 채팅 탭이 아닙니다. 코드 탭에서 로컬 작업 폴더를 선택하고 대화를 시작해주세요.

앱을 최신 버전으로 업데이트한 뒤 진행하세요. 공식 안내 기준으로 모드는 터미널의 Claude Code 2.1.287 이상, 데스크톱 앱에 포함된 Claude Code 2.1.286 이상에서 지원됩니다. 코드 세션에서 `/status`로 포함된 Claude Code 버전을 확인할 수 있습니다. [공식 모드 안내](https://code.claude.com/docs/en/plugins/mods/overview)

이 문서에서 **‘클로드에게 요청’**은 코드 탭의 입력창에 복사할 문장이고, **‘터미널에서 설치’**는 컴퓨터의 터미널에 입력할 명령입니다. 터미널 명령을 직접 실행하려면 해당 명령에 필요한 도구가 설치되어 있어야 합니다. 설치 과정이 익숙하지 않다면 먼저 클로드에게 요청하는 방법을 사용하세요.

| 실습·모드 | 하는 일 | 사용할 환경 |
| --- | --- | --- |
| 직접 만드는 컨텍스트 패널 | 컨텍스트 사용량과 항목별 비중 표시 | 영상에서는 데스크톱 Code |
| Prompt Cache Control | 캐시 재사용량과 예상 만료 시간 표시 | 데스크톱 Code·터미널 |
| Plan Progress | 작업 단계와 진행 상태 표시 | 데스크톱 Code·터미널 |
| Next Steps | 다음에 요청할 작업 추천 | 영상에서는 데스크톱 Code에서 기본 설정으로 사용 |
| Claude Toons | 작업에 맞는 애니메이션 표시 | 터미널 |

## 2. 컨텍스트 사용 현황 패널 만들기

컨텍스트 윈도우는 클로드가 한 번에 참고할 수 있는 정보의 공간입니다. 대화뿐 아니라 지침과 도구 정보 등도 포함됩니다. 이번 실습에서는 이 공간의 사용 현황을 입력창 위에 표시합니다.

### ① 만들기 요청

코드 탭의 입력창에 아래 내용을 붙여넣으세요.

```text
입력창 위에 컨텍스트 사용 현황을 보여주는 모드를 만들어줘.
전체 용량과 현재 사용량, 남은 공간을 숫자로 표시하고, 가로 막대에도 보여줘.
대화, 시스템 지침, 도구, 스킬처럼 확인할 수 있는 항목은 색깔별로 구분하고,
각 항목의 이름과 사용량도 표시해줘.
매 응답이 끝날 때마다 최신 사용량 정보로 갱신하고,
지금 이 세션에서 바로 확인할 수 있게 적용해줘.
```

원하는 화면이 있다면 참고 이미지를 첨부하고 “이런 형태로 만들어줘”라고 덧붙여도 됩니다. 같은 프롬프트를 사용해도 디자인은 영상과 다르게 나올 수 있습니다.

### ② 실행과 자동 재로딩 허용

파일 생성이나 실행 승인을 요청하면 내용을 확인한 뒤 진행합니다. **“Enable hot reloading for this session?”** 안내가 나타나면 **“Enable for this session”**을 선택하세요.

이 선택은 현재 대화에서 만든 모드를 불러오고, 이후 모드 파일을 수정했을 때 변경 사항도 반영하도록 허용하는 것입니다. 수정 사항은 해당 작업이 끝난 뒤 반영됩니다. [공식 제작 안내](https://code.claude.com/docs/en/plugins/mods/create)

### ③ 표시와 갱신 확인

전체 용량, 사용량, 남은 공간과 항목별 표시를 확인하세요. 처음에는 사용량 데이터를 기다릴 수 있으니, 패널이 바로 나오지 않으면 짧은 메시지를 보내 응답이 끝난 뒤 다시 확인합니다.

그래도 표시되지 않으면 다음처럼 요청하세요.

```text
만든 컨텍스트 패널이 보이지 않아.
현재 세션에 모드가 불러와졌는지와 사용량 정보를 받아오고 있는지 확인하고,
데스크톱 코드 탭의 입력창 위에 표시되도록 수정해줘.
```

이 영상에서 제작한 패널은 보정된 추정치를 사용하는 방식입니다. 모든 항목이 정확한 실측값이라는 의미는 아니며, 생성된 구현에 따라 계산 방식이 달라질 수 있습니다. 용량이나 사용량을 임의의 고정 숫자로 표시하지 않는지도 확인하세요.

### ④ 원하는 모습으로 수정

영상에서 사용한 수정 요청입니다.

```text
아래 항목들의 이름을 한글로 바꿔줘.
```

추가로 이런 요청도 할 수 있습니다.

```text
항목 이름과 숫자를 더 읽기 쉽게 정리해줘.
남은 공간은 회색으로 표시하고, 사용 중인 항목은 서로 구분되는 색으로 보여줘.
기존의 사용량 갱신 기능은 유지해줘.
```

### ⑤ 새 대화에서도 사용할 수 있도록 설정

직접 만든 모드는 기본적으로 제작한 세션에 연결됩니다. 계속 사용하려면 세션용 개발 폴더 밖에 보관하고, 새 세션에서도 불러오도록 설정해야 합니다. 자동 재로딩을 허용하는 것만으로 모든 새 대화에 적용되지는 않습니다. [공식 제작 안내](https://code.claude.com/docs/en/plugins/mods/create#use-the-mod-in-other-sessions)

```text
지금 만든 모드를 계속 보관할 수 있는 폴더에 저장하고,
새로운 데스크톱 코드 세션에서도 사용할 수 있게 설정해줘.
기존 설정은 유지해줘.
완료되면 저장 위치와 적용 범위도 알려줘.
```

설정이 끝나면 새 코드 대화를 열어 패널이 나타나는지 확인하세요. 특정 프로젝트에만 적용됐는지, 다른 프로젝트에서도 사용할 수 있는지도 클로드의 설명에서 확인하면 됩니다.

## 3. Prompt Cache Control — 캐시 사용 현황 확인

클로드는 입력 내용 중 이전과 동일한 부분을 캐시로 재사용할 수 있습니다. 캐시는 일정 시간 다시 사용되지 않으면 만료되며, 유지 시간은 계정과 설정에 따라 다릅니다. 캐싱은 클로드 코드가 기본적으로 관리하는 기능입니다. [공식 캐시 설명](https://code.claude.com/docs/en/prompt-caching)

이 모드는 캐시 재사용량과 예상 만료 시간을 표시하고 알림을 제공합니다. 캐시를 새로 켜는 기능이 아니라, 사용 현황을 확인하는 도구입니다.

- [모드 설명·소스](https://github.com/davila7/claude-code-templates/tree/main/cli-tool/components/mods/observability/prompt-cache-control)
- [영상에서 소개한 Daniel San의 X 게시물](https://x.com/dani_avila7/status/2106455605925822967)

### 클로드에게 설치 요청

```text
아래 명령으로 Prompt Cache Control 모드를 현재 프로젝트에 설치해줘.
설치 후 지금 사용 중인 데스크톱 Code 세션에 적용하고,
캐시 상태 표시와 /cache 패널을 확인할 수 있게 해줘.

npx claude-code-templates@latest --mod observability/prompt-cache-control
```

### 터미널에서 직접 설치하려면

프로젝트 폴더에서 실행합니다. 이 명령에는 Node.js의 npx가 필요합니다.

```bash
npx claude-code-templates@latest --mod observability/prompt-cache-control
```

### 사용하기

설치한 모드를 세션에 불러온 뒤 대화를 진행하면 상태 표시줄을 확인할 수 있습니다. 자동 재로딩 안내가 나오면 `Enable for this session`을 선택하세요.

코드 입력창에 다음 명령을 입력하면 상세 패널이 열립니다.

```text
/cache
```

`read`는 캐시에서 재사용한 입력, `wrote`는 새로 캐시에 저장한 입력, `new`는 캐시로 처리되지 않은 입력을 나타냅니다. 상세 패널에서는 턴별 내역도 확인할 수 있습니다. 남은 시간은 모드가 추정한 값이며, 알림은 설정과 입력량 조건에 따라 나타납니다. [표시 방식 설명](https://github.com/davila7/claude-code-templates/blob/main/cli-tool/components/mods/observability/prompt-cache-control/README.md)

## 4. Plan Progress — 작업 진행 상황 확인

입력창 위에 작업 단계와 진행 상태를 표시합니다. 진행 중, 입력 대기, 오류, 완료 상태를 구분하며 데스크톱과 터미널에서 사용할 수 있습니다. 진행률은 클로드가 등록하고 갱신하는 작업 단계에 따른 값으로, 남은 시간을 정확히 예측하는 수치는 아닙니다. [모드 설명·소스](https://github.com/zycck/claude-mods)

### 클로드에게 설치 요청

```text
https://github.com/zycck/claude-mods 의 plan-progress 모드를 설치해줘.
현재 데스크톱 Code 세션에서 사용할 수 있게 적용하고,
기존 설정은 유지해줘.
```

### 직접 설치하려면

Claude Code 입력창에서 다음 두 명령을 차례로 실행합니다.

```text
/plugin marketplace add zycck/claude-mods
/plugin install plan-progress@zycck-mods
```

### 확인용 요청 예시

```text
초보자를 위한 AI 도구 활용 워크숍을 기획해줘.
대상과 목표 정리, 60분 교육 구성, 실습 과제, 준비물 목록 순서로 진행해줘.
설치된 plan-progress를 사용해서 작업 단계와 진행 상황을 표시해줘.
```

진행 표시를 보이거나 숨기려면 `/progress`를 사용합니다. `/progress-clear`는 표시된 진행 바를 지웁니다. [명령어 안내](https://github.com/zycck/claude-mods#commands)

## 5. Next Steps — 다음 요청 추천받기

대화를 바탕으로 다음에 할 만한 요청을 최대 세 개까지 추천합니다. 사용할 수 있는 스킬이나 명령어도 제안할 수 있습니다. 항목을 선택하면 요청 문장이 입력창에 들어오며, 사용자가 확인하고 전송합니다. 추천 생성에는 추가 모델 사용량이 발생합니다. [모드 설명·소스](https://github.com/anthropics/claude-plugins-community/tree/main/next-steps)

**영상에서는 데스크톱 앱에서 기본 설정으로 사용했습니다.** 공개 README에는 터미널 표시를 기준으로 한 안내가 있어 영상의 확인 환경과 차이가 있습니다. 여기서는 별도 옵션 변경 없이 기본값으로 진행합니다.

### 클로드에게 설치 요청

```text
아래 명령으로 next-steps 모드를 설치해줘.
두 가지 옵션은 모두 기본값을 유지하고,
현재 데스크톱 Code 세션에서 사용할 수 있게 적용해줘.
기존 설정은 유지해줘.

claude plugin marketplace add anthropics/claude-plugins-community
claude plugin install next-steps@claude-community
```

### 터미널에서 직접 설치하려면

Claude Code CLI가 설치된 환경에서 다음 두 명령을 차례로 실행합니다.

```bash
claude plugin marketplace add anthropics/claude-plugins-community
claude plugin install next-steps@claude-community
```

설치 대상 이름은 [마켓플레이스 등록 정보](https://github.com/anthropics/claude-plugins-community/blob/main/.claude-plugin/marketplace.json)를 기준으로 합니다.

### 영상에서 활용할 수 있는 요청

```text
오늘 나온 주요 AI 뉴스 3가지를 찾아서 정리해줘.
각 뉴스마다 핵심 내용과 주목할 이유를 짧게 설명하고,
출처 링크도 함께 알려줘.
```

답변이 끝난 뒤 추천 중 하나를 선택해 이어가세요. 추천 문구는 대화에 따라 달라집니다. 아주 짧은 답변에서는 기본 설정상 추천이 생략될 수 있습니다. [동작 및 기본 설정](https://github.com/anthropics/claude-plugins-community/blob/main/next-steps/README.md)

## 6. Claude Toons — 기다리는 화면을 애니메이션으로

클로드가 작업하는 동안 작업 내용에 맞는 작은 애니메이션을 보여주는 커뮤니티 모드입니다. **터미널용**이며, 데스크톱 코드 탭에서 진행하는 앞의 실습과 사용 환경이 다릅니다. [모드 설명·소스](https://github.com/achimala/claude-toons)

### 터미널에서 설치하고 실행

아래는 macOS·Linux 계열 셸 기준입니다. Git과 Claude Code CLI가 필요합니다. 같은 위치에 이미 저장소가 있다면 복제 명령을 반복하지 마세요.

```bash
git clone https://github.com/achimala/claude-toons ~/src/claude-toons
claude --plugin-dir ~/src/claude-toons
```

열린 Claude Code 세션에서 작업을 요청하면 작업 중에 애니메이션이 나타납니다. 위 실행 방법은 해당 세션에서 모드를 불러오는 방식입니다.

### 표시와 생성 방식 설정

| 명령·설정 | 용도 |
| --- | --- |
| `/toons` | 애니메이션 표시·숨기기 |
| `/toons settings` | 장면 설정과 사용량 확인 |
| `Ready-made only` | 준비된 장면만 사용. 장면 생성을 위한 추가 모델 요청 없음 |
| `Mix` | 준비된 장면과 새로 생성한 장면을 함께 사용. 기본값 |
| `Fresh only` | 새 장면 생성에 추가 사용량 발생 |

추가 장면 생성 없이 먼저 사용해보려면 설정에서 `Ready-made only`를 선택하세요. 기본값인 `Mix`도 장면 생성에 추가 사용량이 듭니다. [제작자의 사용량 안내](https://github.com/achimala/claude-toons#what-it-costs)

## 7. 보너스: 이메일 주소 가리기

인트로처럼 이메일 주소에 마우스를 올릴 때만 보이게 하는 기능을 직접 만들어보고 싶다면, 코드 탭에서 다음처럼 요청할 수 있습니다. 특정 배포 모드의 설치 명령이 아니라 **새 모드를 만드는 요청 예시**입니다.

```text
데스크톱 Code 탭에서 클로드의 답변에 포함된 이메일 주소를
기본적으로 가리고, 마우스를 올렸을 때만 보이게 하는 모드를 만들어줘.
모델이 참고하는 원문이나 저장된 대화 내용은 바꾸지 말고,
화면에 표시되는 방식만 변경해줘.
지금 이 세션에서 바로 확인할 수 있게 적용해줘.
```

테스트에는 `sam@example.com` 같은 예시 주소를 사용하세요. 이 기능은 화면 표시를 바꾸는 것이므로 원문에서 이메일 주소를 삭제하거나 익명화하는 기능은 아닙니다.

## 8. 설치했는데 화면에 보이지 않을 때

먼저 코드 탭과 올바른 프로젝트를 사용 중인지 확인하세요. 설치가 완료돼도 현재 세션에 아직 불러와지지 않았을 수 있습니다. 공식 문서는 외부에서 설치한 플러그인을 열린 세션에 반영할 때 `/reload-plugins`를 사용하거나 새 세션을 시작하도록 안내합니다. [공식 설치 안내](https://code.claude.com/docs/en/plugins/mods/overview#install-or-update-a-mod)

데스크톱에서 직접 해결하기 어렵다면 다음 내용을 복사해 요청하세요.

```text
방금 설치한 모드가 화면에 보이지 않아.
현재 세션에서 사용하는 Claude Code 버전과 모드의 설치 상태,
적용 범위, 불러오기 상태를 확인해줘.
데스크톱 지원 여부와 기본 설정도 확인하고,
지금 적용할 수 있는지 또는 새 세션을 열어야 하는지 알려줘.
기존 설정과 다른 모드는 유지해줘.
```

화면이 나타나는 조건도 확인하세요. 컨텍스트·캐시 패널은 사용량 데이터를 받은 뒤, Next Steps는 응답이 끝난 뒤, Claude Toons는 터미널에서 작업 중일 때 확인합니다.

## 더 알아보기

- [Claude Code 모드 공식 소개](https://code.claude.com/docs/en/plugins/mods/overview)
- [클로드에게 모드 제작 요청하기](https://code.claude.com/docs/en/plugins/mods/create)
- [모드 시작하기 공식 블로그](https://claude.dev/blog/getting-started-with-claude-code-mods/)
- [기존 훅 활용 가이드](https://code.claude.com/docs/en/hooks-guide)

처음에는 자주 확인하는 정보 하나를 화면에 추가하거나, 반복해서 입력하는 요청 하나를 줄이는 것부터 시작해보세요.
