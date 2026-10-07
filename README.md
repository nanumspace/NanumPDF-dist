# NanumPDF 배포

NanumPDF는 Nanum Space Co., Ltd.가 개발한 Windows용 PDF 뷰어 및 편집기입니다. 이 저장소에는 **다운로드 웹사이트와 설치 파일 배포 안내**만 있으며 앱 소스 코드는 포함하지 않습니다. 릴리스 페이지의 `Source code` 항목은 GitHub 가 자동으로 만드는 것으로 내용이 비어 있습니다. 설치 파일(`.msi`)만 받으세요.

## 다운로드

[다운로드 페이지](https://nanumspace.github.io/NanumPDF-dist/) · [최신 릴리스 받기](https://github.com/nanumspace/NanumPDF-dist/releases/latest)

| 파일 | 대상 |
|---|---|
| `NanumPDF-1.0.0-win-x64.msi` | Intel/AMD 64비트 Windows (x64) |
| `NanumPDF-1.0.0-win-arm64.msi` | ARM64 Windows (Snapdragon 등) |

각 설치 파일 옆에 `.sha256` 체크섬 파일이 있습니다. 내 PC 종류는 **설정 > 시스템 > 정보 > 시스템 종류**에서 확인할 수 있습니다.

## 요구 사항

- Windows 10 또는 Windows 11 (x64 또는 ARM64)
- 별도의 .NET 런타임 설치는 필요하지 않습니다(설치 파일에 포함되어 있습니다).
- 관리자 권한이 필요하지 않습니다. 현재 사용자 계정에만 설치됩니다.

## 설치

1. 내 PC에 맞는 `.msi` 파일을 내려받아 더블 클릭합니다.
2. 설치 마법사에서 설치 경로(기본값 `%LocalAppData%\Programs\NanumPDF`)와 선택 기능을 고릅니다.
   - 바탕화면 바로가기
   - PDF 파일의 '연결 프로그램' 목록과 Windows 설정 > 앱 > 기본 앱에 NanumPDF 등록 (기본 앱은 바뀌지 않습니다)

   두 기능은 기본으로 선택되어 있으며, 조용히 설치(`/qn`)해도 함께 설치됩니다. 등록을 원하지 않으면 설치 화면에서 해제하세요. PDF를 더블 클릭했을 때 NanumPDF로 열리게 하려면 PDF 파일을 우클릭 > `연결 프로그램` > `다른 앱 선택`에서 NanumPDF를 고르고 `항상`을 누르거나, `설정 > 앱 > 기본 앱`에서 `.pdf`를 NanumPDF로 지정하세요(Windows는 기본 앱 변경을 사용자가 직접 하도록 제한합니다).
3. 설치가 끝나면 시작 메뉴에서 **NanumPDF**를 실행합니다.

조용히 설치하려면 다음 명령을 사용합니다.

```powershell
msiexec /i NanumPDF-1.0.0-win-x64.msi /qn
```

같은 이름의 이전 버전이 설치되어 있으면 새 설치 파일이 자동으로 교체합니다. x64와 ARM64 설치 파일을 바꿔 설치해도 마찬가지입니다.

## 내려받은 파일 확인

설치하기 전에 파일이 변조되지 않았는지 확인할 수 있습니다.

**1. 체크섬** — 아래 값이 같은 파일 옆의 `.sha256` 값과 같아야 합니다.

```powershell
Get-FileHash .\NanumPDF-1.0.0-win-x64.msi -Algorithm SHA256
```

**2. 디지털 서명** — 파일 속성 > 디지털 서명 탭에서 서명자가 **Nanum Space Co,. Ltd**(발급자: GlobalSign GCC R45 EV CodeSigning CA 2020)인지 확인합니다. 서명 인증서에 등록된 표기는 `Co,.`(쉼표 뒤 마침표)이며, 인증서 표기 그대로입니다.

```powershell
(Get-AuthenticodeSignature .\NanumPDF-1.0.0-win-x64.msi).Status   # Valid
```

서명이 없거나 서명자가 다르면 설치하지 마세요. 새로 배포된 파일은 Windows SmartScreen이 평판을 쌓기 전까지 경고를 표시할 수 있습니다. 이 경우에도 위 두 가지가 맞으면 정상 파일입니다.

## 제거

**설정 > 앱 > 설치된 앱**에서 NanumPDF를 제거합니다. 설정과 로그(`%LocalAppData%\NanumPDF`)는 제거 후에도 남을 수 있으며 직접 삭제해도 됩니다.

## 업데이트

자동 업데이트 기능은 없습니다. 새 버전이 나오면 이 저장소의 [릴리스](https://github.com/nanumspace/NanumPDF-dist/releases)에서 새 설치 파일을 받아 설치하면 이전 버전이 교체됩니다. 변경 내용은 각 릴리스 설명에 있습니다.

## 이용 조건

NanumPDF는 **무료로 배포**되는 소프트웨어입니다. 누구나 비용 없이 내려받아 설치하고 사용할 수 있습니다. 소스 코드는 공개하지 않습니다. 전체 조건은 이 저장소의 [LICENSE.txt](https://github.com/nanumspace/NanumPDF-dist/blob/main/LICENSE.txt)(설치 폴더에도 함께 설치됨)에 있으며 요약은 다음과 같습니다.

- **모든 권리는 Nanum Space Co., Ltd.(나눔스페이스)에 있습니다.** 사용 권한만 주어지며 소유권이나 그 밖의 권리는 넘어가지 않습니다.
- **재배포 금지**: 설치 파일과 그 안에 포함된 파일을 복사·게시·판매·대여하는 등 제3자에게 다시 배포할 수 없습니다. 다른 사람에게 알려 줄 때는 이 저장소의 주소를 알려 주세요.
- **역공학 금지**: 법령이 명시적으로 허용하는 범위를 제외하고 프로그램을 역컴파일·역어셈블·분해하거나 소스 코드를 알아내려는 시도를 할 수 없습니다.
- **수정 금지**: 프로그램을 수정하거나 이를 바탕으로 파생 제품을 만들 수 없고, 저작권·서명 표시를 제거하거나 바꿀 수 없습니다.
- 소프트웨어는 있는 그대로 제공되며 명시적이든 묵시적이든 어떠한 보증도 하지 않고, 사용으로 생긴 손해(데이터 손실 포함)에 대해 책임을 지지 않습니다. 중요한 문서는 편집하기 전에 사본을 보관하세요.

위 조건에 동의하지 않으면 설치하거나 사용하지 마세요.

## 제3자 구성 요소

설치 파일에는 DevExpress 구성 요소와 .NET 런타임 및 오픈 소스 라이브러리가 포함되어 있으며 각 구성 요소는 해당 라이선스를 따릅니다. 위 이용 조건은 NanumPDF 자체에 적용되며, 포함된 제3자 구성 요소에는 각 구성 요소의 라이선스 조건이 우선합니다.

## 문의

문의와 오류 보고는 support@nanumspace.com 으로 보내 주세요. 이 저장소는 이슈를 받지 않습니다.

Copyright © 2026 Nanum Space Co., Ltd. All rights reserved.
