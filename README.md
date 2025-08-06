# Assemble Pro Web

Next.js 기반의 Assemble Pro 웹 애플리케이션입니다.

## 기술 스택

- **Framework**: Next.js 15.4.5 (App Router)
- **Language**: TypeScript 5 (엄격 모드)
- **Styling**: Tailwind CSS 4
- **Package Manager**: Yarn Berry 4.3.1 (PnP 모드)
- **Node Version**: 22.5.0+ (2025년 LTS)

## 🚀 빠른 시작

### 1단계: 사전 요구사항 확인

다음 소프트웨어가 설치되어 있는지 확인하세요:

```bash
# Node.js 22.0.0 이상 설치 확인
node --version  # v22.5.0 이상이어야 함

# nvm 사용 시 (권장)
nvm install 22.5.0
nvm use 22.5.0
```

### 2단계: 저장소 클론

```bash
git clone [repository-url]
cd assemble-pro-web

# 자동으로 올바른 Node 버전 사용 (nvm 설치 시)
nvm use
```

### 3단계: 의존성 설치

```bash
# Yarn Berry로 의존성 설치 (최초 실행 시 시간이 걸릴 수 있음)
yarn install

# 설치 완료 후 PnP 파일 생성 확인
ls -la .pnp.cjs  # 파일이 있으면 정상
```

### 4단계: 환경 변수 설정

```bash
# 환경 변수 템플릿 복사
cp .env.example .env

# .env 파일을 열어서 필요한 값들을 설정
# 현재는 기본값으로도 실행 가능
```

### 5단계: 개발 서버 실행

```bash
# 개발 서버 시작
yarn dev

# 브라우저에서 확인
# http://localhost:3000
```

## 📝 주요 스크립트

```bash
# 개발 서버 실행
yarn dev

# 프로덕션 빌드
yarn build

# 프로덕션 서버 실행
yarn start

# 코드 린트 검사
yarn lint

# 코드 포맷팅
yarn format

# 포맷팅 검사만 (수정하지 않음)
yarn format:check
```

## 🔧 개발 환경 설정

### VSCode 설정 (권장)

프로젝트를 열면 자동으로 다음이 설정됩니다:

- TypeScript SDK: Yarn PnP용 TypeScript 사용
- ESLint: Yarn PnP용 ESLint 사용
- Prettier: Yarn PnP용 Prettier 사용

**초기 설정 시 VSCode에서 다음을 수행하세요:**

1. `Cmd/Ctrl + Shift + P` → `TypeScript: Select TypeScript Version`
2. `Use Workspace Version` 선택

### Git 훅 설정

프로젝트는 Husky를 사용하여 커밋 전 자동 검사를 수행합니다:

- 커밋 시 자동으로 ESLint + Prettier 실행
- 코드 품질 문제가 있으면 커밋 차단

## 🏗️ 프로젝트 구조

```
assemble-pro-web/
├── .yarn/                 # Yarn Berry 설정 파일들
│   ├── releases/          # Yarn 실행 파일
│   ├── sdks/             # IDE 통합을 위한 SDK
│   └── ...
├── .vscode/              # VSCode 설정
│   └── settings.json     # PnP용 IDE 설정
├── src/
│   └── app/              # Next.js App Router
│       ├── layout.tsx    # 루트 레이아웃
│       ├── page.tsx      # 홈 페이지
│       └── globals.css   # 전역 스타일
├── public/               # 정적 파일
├── .env.example          # 환경 변수 템플릿
├── .nvmrc               # Node 버전 지정
├── .pnp.cjs             # Yarn PnP 매니페스트
├── .yarnrc.yml          # Yarn 설정
├── package.json         # 프로젝트 메타데이터
└── yarn.lock            # 의존성 잠금 파일
```

## 🔍 문제 해결

### 자주 발생하는 문제들

#### 1. `Module not found` 오류

```bash
# PnP 캐시 정리 후 재설치
yarn cache clean
yarn install
```

#### 2. TypeScript/ESLint가 제대로 작동하지 않음

```bash
# VSCode에서 TypeScript 워크스페이스 버전 선택
# Cmd/Ctrl + Shift + P → "TypeScript: Select TypeScript Version" → "Use Workspace Version"

# SDK 재생성
yarn dlx @yarnpkg/sdks vscode
```

#### 3. 새 패키지 설치 후 타입 오류

```bash
# SDK 업데이트
yarn dlx @yarnpkg/sdks vscode
```

#### 4. Husky 훅이 실행되지 않음

```bash
# 훅 권한 설정
chmod +x .husky/pre-commit
```

### Yarn Berry와 npm/yarn v1 차이점

- **node_modules 없음**: PnP 방식으로 의존성 관리
- **Zip 파일로 저장**: 의존성이 `.yarn/cache`에 압축 저장
- **빠른 설치**: 링크 기반으로 설치 속도 향상
- **엄격한 의존성**: 선언하지 않은 의존성 사용 불가

## 🎯 개발 가이드라인

### 브랜치 전략

- `main`: 프로덕션 브랜치
- `develop`: 개발 브랜치
- `feature/*`: 기능 개발 브랜치
- `fix/*`: 버그 수정 브랜치

### 커밋 메시지 규칙

```
타입: 간단한 설명

예시:
feat: 사용자 로그인 기능 추가
fix: 로그인 시 세션 만료 오류 수정
docs: README 설치 가이드 업데이트
style: 코드 포맷팅 적용
refactor: 사용자 인증 로직 리팩토링
test: 로그인 컴포넌트 테스트 추가
chore: 의존성 업데이트
```

### 새 패키지 추가

```bash
# 프로덕션 의존성
yarn add package-name

# 개발 의존성
yarn add -D package-name

# 설치 후 SDK 업데이트 (VSCode 사용 시)
yarn dlx @yarnpkg/sdks vscode
```

## 🤝 기여하기

1. 이 저장소를 포크합니다
2. 피처 브랜치를 생성합니다 (`git checkout -b feature/amazing-feature`)
3. 변경사항을 커밋합니다 (`git commit -m 'feat: Add amazing feature'`)
4. 브랜치에 푸시합니다 (`git push origin feature/amazing-feature`)
5. Pull Request를 생성합니다

## 📞 도움이 필요한 경우

- **Yarn Berry 관련**: [공식 문서](https://yarnpkg.com/getting-started)
- **Next.js 관련**: [Next.js 문서](https://nextjs.org/docs)
- **프로젝트 이슈**: [GitHub Issues](링크)

---

**참고**: 이 프로젝트는 Yarn Berry PnP 모드를 사용합니다. 기존 npm/yarn v1과 다른 방식으로 작동하므로 위 가이드를 정확히 따라주세요.
