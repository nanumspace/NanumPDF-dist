# NanumPDF 배포

NanumPDF는 Nanum Space가 개발한 Windows용 PDF 뷰어 및 편집기입니다. 이 저장소는 **설치 파일 배포 전용**이며 소스 코드는 포함하지 않습니다.

## 다운로드

[최신 릴리스 받기](https://github.com/nanumspace/NanumPDF-dist/releases/latest)

| 파일 | 대상 |
|---|---|
| `NanumPDF-<버전>-win-x64.msi` | Intel/AMD 64비트 Windows (x64) |
| `NanumPDF-<버전>-win-arm64.msi` | ARM64 Windows (Snapdragon 등) |

각 설치 파일 옆에 `.sha256` 체크섬 파일이 있습니다. 내 PC 종류는 **설정 > 시스템 > 정보 > 시스템 종류**에서 확인할 수 있습니다.

## 요구 사항

- Windows 10 또는 Windows 11 (x64 또는 ARM64)
- 별도의 .NET 런타임 설치는 필요하지 않습니다(설치 파일에 포함되어 있습니다).
- 관리자 권한이 필요하지 않습니다. 현재 사용자 계정에만 설치됩니다.

## 설치

1. 내 PC에 맞는 `.msi` 파일을 내려받아 더블 클릭합니다.
2. 설치 마법사에서 설치 경로(기본값 `%LocalAppData%\Programs\NanumPDF`)와 선택 기능을 고릅니다.
   - 바탕화면 바로가기
   - PDF 파일의 '연결 프로그램' 목록에 NanumPDF 등록 (기본 앱은 바뀌지 않습니다)
3. 설치가 끝나면 시작 메뉴에서 **NanumPDF**를 실행합니다.

조용히 설치하려면 다음 명령을 사용합니다.

```powershell
msiexec /i NanumPDF-<버전>-win-x64.msi /qn
```

같은 이름의 이전 버전이 설치되어 있으면 새 설치 파일이 자동으로 교체합니다. x64와 ARM64 설치 파일을 바꿔 설치해도 마찬가지입니다.

## 내려받은 파일 확인

설치하기 전에 파일이 변조되지 않았는지 확인할 수 있습니다.

**1. 체크섬** — 아래 값이 같은 파일 옆의 `.sha256` 값과 같아야 합니다.

```powershell
Get-FileHash .\NanumPDF-<버전>-win-x64.msi -Algorithm SHA256
```

**2. 디지털 서명** — 파일 속성 > 디지털 서명 탭에서 서명자가 **Nanum Space Co,. Ltd**(발급자: GlobalSign GCC R45 EV CodeSigning CA 2020)인지 확인합니다.

```powershell
(Get-AuthenticodeSignature .\NanumPDF-<버전>-win-x64.msi).Status   # Valid
```

서명이 없거나 서명자가 다르면 설치하지 마세요. 새로 배포된 파일은 Windows SmartScreen이 평판을 쌓기 전까지 경고를 표시할 수 있습니다. 이 경우에도 위 두 가지가 맞으면 정상 파일입니다.

## 제거

**설정 > 앱 > 설치된 앱**에서 NanumPDF를 제거합니다. 설정과 로그(`%LocalAppData%\NanumPDF`)는 제거 후에도 남을 수 있으며 직접 삭제해도 됩니다.

## 업데이트

자동 업데이트 기능은 없습니다. 새 버전이 나오면 이 저장소의 [릴리스](https://github.com/nanumspace/NanumPDF-dist/releases)에서 새 설치 파일을 받아 설치하면 이전 버전이 교체됩니다. 변경 내용은 각 릴리스 설명에 있습니다.

## 제3자 구성 요소

설치 파일에는 DevExpress 구성 요소와 .NET 런타임 및 오픈 소스 라이브러리가 포함되어 있으며 각 구성 요소는 해당 라이선스를 따릅니다.

## 문의

문의와 오류 보고는 Nanum Space 담당자에게 전달해 주세요. 이 저장소는 이슈를 받지 않습니다.

Copyright © 2026 Nanum Space. All rights reserved.
