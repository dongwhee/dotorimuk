# dotorim 소개 사이트

[dotorim](https://dotorim.uk) iOS 앱들의 소개 페이지와 개인정보처리방침을 담은 정적 사이트입니다. GitHub Pages로 호스팅합니다.

## 구조

```
.
├── index.html              # 브랜드 랜딩 + 앱 목록
├── support.html            # 공통 지원·문의
├── styles.css              # 공통 스타일
├── .nojekyll               # Jekyll 처리 비활성화 (순수 정적)
└── apps/
    ├── mikiboard/
    │   ├── index.html      # 소개
    │   └── privacy.html    # 개인정보처리방침
    ├── misoviewer/
    │   ├── index.html
    │   └── privacy.html
    └── kkomaledger/
        ├── index.html
        └── privacy.html
```

모든 링크는 상대 경로라서 프로젝트 페이지(`user.github.io/dotorimuk/`)와 커스텀 도메인(`dotorim.uk`) 양쪽에서 그대로 동작합니다.

## App Store Connect 입력용 URL

> 아래 `<BASE>`는 실제 배포 주소(`https://dotorim.uk` 또는 `https://<user>.github.io/dotorimuk`)로 바꿔 입력하세요.

| 앱 | Support URL | Privacy Policy URL | Marketing URL |
|----|-------------|--------------------|---------------|
| Mikiboard | `<BASE>/support.html` | `<BASE>/apps/mikiboard/privacy.html` | `<BASE>/apps/mikiboard/` |
| MisoViewer | `<BASE>/support.html` | `<BASE>/apps/misoviewer/privacy.html` | `<BASE>/apps/misoviewer/` |
| KkomaLedger | `<BASE>/support.html` | `<BASE>/apps/kkomaledger/privacy.html` | `<BASE>/apps/kkomaledger/` |

## GitHub Pages 배포

1. 이 디렉토리를 GitHub 저장소로 푸시합니다.
2. 저장소 **Settings → Pages** 에서 Source를 `Deploy from a branch`, 브랜치를 `main` / 폴더 `/ (root)` 로 설정합니다.
3. 잠시 후 `https://<user>.github.io/<repo>/` 에서 사이트가 열립니다.

### 커스텀 도메인(dotorim.uk)을 쓰려면

1. Settings → Pages → Custom domain 에 `dotorim.uk` 를 입력합니다 (저장소 루트에 `CNAME` 파일이 자동 생성됨).
2. 도메인 DNS에 GitHub Pages 레코드를 추가합니다:
   - Apex(`dotorim.uk`): A 레코드 `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - 또는 `www`: CNAME `<user>.github.io`
3. Enforce HTTPS 를 체크합니다.

## 로컬 미리보기

```sh
python3 -m http.server 8000
# http://localhost:8000 접속
```

## 수정 시 확인할 점

- 지원 이메일은 `dotorim.uk@icloud.com` 로 작성되어 있습니다. 실제 수신 가능한 주소로 맞춰 주세요. (`support.html`, 각 `privacy.html`)
- 개인정보처리방침 본문은 현재 앱 동작(외부 전송 없음, KkomaLedger는 iCloud 사용)을 기준으로 작성했습니다. 앱에 분석·광고·서버 통신을 추가하면 방침도 함께 갱신해야 합니다.
