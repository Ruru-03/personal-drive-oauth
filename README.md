# Personal Drive OAuth

Windows와 Linux에서 AI 작업 결과물을 Google Drive로 교환하기 위한 개인용 연동 앱의 한국어 안내 페이지입니다. 이 저장소에는 OAuth 클라이언트, 인증 정보 또는 파일 교환 프로그램이 들어 있지 않습니다.

## 파일

- `index.html`: 앱 소개
- `privacy.html`: 개인정보처리방침
- `styles.css`: 두 페이지의 공통 디자인
- `.nojekyll`: 정적 파일을 그대로 게시하기 위한 설정

## Google OAuth 브랜딩 입력

GitHub Pages 배포 후 다음 주소가 로그인 없이 열리는지 확인합니다.

| 항목 | 입력 값 |
| --- | --- |
| 앱 이름 | `Personal Drive OAuth` — 홈페이지와 Google 동의 화면의 이름을 일치시킵니다. |
| 사용자 지원 이메일 | Google Cloud에서 선택 가능한 운영자 본인의 실제 이메일 |
| 앱 홈페이지 | https://ruru-03.github.io/personal-drive-oauth/ |
| 개인정보처리방침 | https://ruru-03.github.io/personal-drive-oauth/privacy.html |
| 개발자 연락처 | 운영자 본인의 실제 이메일 |
| 승인된 도메인 입력 후보 | `ruru-03.github.io` — 프로토콜과 경로는 제외하며, 실제 콘솔 수락 여부를 확인합니다. |

위 홈페이지·정책 주소는 OAuth 리디렉션 URI가 아닙니다. OAuth 클라이언트 유형과 리디렉션 URI는 실제 Windows/Linux 연동 도구가 요구하는 설정을 따릅니다. 이 홈페이지에는 인증 콜백 기능이 없습니다.

이 페이지를 게시했다고 Google의 앱 검증이나 도메인 검증이 완료되는 것은 아닙니다. [Google 브랜딩 요구사항](https://support.google.com/cloud/answer/15549049?hl=en)

## GitHub Pages 배포와 수정

저장소 **Settings → Pages → Build and deployment**에서 다음과 같이 설정합니다.

1. Source: **Deploy from a branch**
2. Branch: **main**
3. Folder: **/(root)**
4. **Save**

이후 `main`에 페이지 수정을 커밋하면 다시 배포됩니다. 배포 상태는 저장소 Actions의 Pages 실행에서 확인합니다. 기본 Pages 주소는 HTTPS를 지원합니다. [GitHub 배포 안내](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)

## 무료 Pages 주소와 도메인 소유권 검증의 차이

- **페이지 게시:** 무료 GitHub Pages 주소로 홈페이지와 개인정보처리방침을 제공할 수 있습니다.
- **Search Console URL-prefix 확인:** `https://ruru-03.github.io/personal-drive-oauth/` 속성은 Google이 제공한 HTML 확인 파일 또는 meta 태그를 배포해 확인할 수 있습니다. 이 방식은 해당 URL 경로의 관리 권한을 확인합니다. [Search Console 확인 방법](https://support.google.com/webmasters/answer/9008080?hl=en)
- **OAuth 정식 도메인 검증:** 현재 Google 안내는 URL-prefix 대신 DNS 수준의 **Domain Property** 검증을 요구합니다. 무료 `ruru-03.github.io`의 DNS를 운영자가 직접 관리할 수 없으므로, HTML 확인 파일만으로 이 요건을 충족한다고 볼 수 없습니다. 정식 심사에서 도메인 검증을 요구하면 직접 DNS를 관리하는 커스텀 도메인이 필요합니다. [Google OAuth Domain Verification](https://support.google.com/cloud/answer/13804266?hl=en)

`ruru-03.github.io`는 승인된 도메인의 입력 후보일 뿐이며, Google 콘솔의 수락이나 검증 성공을 보장하지 않습니다. 콘솔이 거부하면 소유하지 않은 `github.io`로 바꾸어 우회하지 않습니다. 커스텀 도메인을 사용하면 홈페이지와 정책 URL도 해당 도메인으로 갱신합니다.

## 개인용 앱과 게시 상태

본인 등 100명 미만이 사용하는 개인용 앱은 Google이 안내하는 OAuth 검증 예외에 해당할 수 있습니다. 미검증 경고와 사용자 수 제한은 남을 수 있으며, 브랜딩 입력 화면의 필수 항목까지 자동으로 면제된다는 뜻은 아닙니다. [Google 개인용 앱 예외](https://support.google.com/cloud/answer/13464323?hl=en)

External 앱이 **Testing** 상태이고 Drive 권한을 요청하면 refresh token에는 7일 만료 규칙이 적용됩니다. **In production**은 이 Testing 규칙을 벗어나지만, 토큰이 영구 유효하다는 의미는 아닙니다. [Google 토큰 만료 규칙](https://developers.google.com/identity/protocols/oauth2#expiration)

External **In production**은 본인 계정만 허용하는 접근 제한 설정이 아닙니다. 다른 계정의 접근을 막으려면 실제 연동 도구의 계정 제한을 확인합니다. [Google Audience 설정](https://support.google.com/cloud/answer/15549945?hl=en)

## 실제 구현 확인 후 갱신할 내용

현재 확인된 목적은 운영자 본인의 Windows/Linux 환경에서 AI 작업 결과물을 교환하는 것입니다. 프로그램 이름, 요청 OAuth scope, 파일·토큰의 저장 위치와 보호 방식, 보관 기간, 외부 AI 서비스로의 전송 여부는 확인되지 않았습니다. 개인정보처리방침은 이 한계를 명시합니다. 정식 검증을 신청하기 전에는 실제 구현과 설정을 확인하여 구체적인 데이터 접근·사용·보관·공유 내용을 반영해야 합니다.

정적 페이지에는 입력 양식, JavaScript, 외부 글꼴, 분석 도구가 없습니다. 다만 GitHub Pages는 보안 목적으로 방문자의 IP를 기록·보관합니다. [GitHub Pages 데이터 수집](https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages#data-collection)

문의: [GitHub Issues](https://github.com/Ruru-03/personal-drive-oauth/issues). 공개 저장소나 이슈에 토큰, 인증 코드, 비밀번호, 비공개 작업 결과물을 올리지 않습니다.
