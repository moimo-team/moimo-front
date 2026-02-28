# 🌐 Moimo Frontend (모이모 프론트엔드)

모이모(Moimo)는 관심사 기반 모임 모집 및 관리 서비스의 프론트엔드 애플리케이션입니다.  
React 19와 TypeScript를 기반으로 구축되었으며, 최신 프론트엔드 기술 스택을 활용하여 최적의 UX를 제공합니다.

### **📅 개발 일정**

| 단계                  | 기간                                |
| :-------------------- | :---------------------------------- |
| **총 개발 소요 시간** | 4주 (25.12.19 ~ 26.01.20)           |
| **기획 단계**         | 2025년 12월 19일 ~ 2025년 12월 21일 |
| **개발 단계**         | 2025년 12월 22일 ~ 2026년 1월 16일  |
| **테스트 단계**       | 2026년 1월 17일 ~ 2026년 1월 18일   |
| **배포 단계**         | 2026년 1월 19일 ~ 2026년 1월 20일   |

## 🚀 배포 주소

- https://moimo.vercel.app

## 🎯 주요 기능

### 1. 사용자 인증 (User Authentication)

- 이메일 기반 회원가입/로그인 및 Google OAuth(Auth Code Flow) 지원

### 2. 사용자 프로필 (User Profile)

- 관심사 기반의 상세 프로필 설정 및 닉네임 인라인 수정 기능

### 3. 모임 관리 (Meeting Management)

- 모임 개설, 필터링 조회, 참여 신청 및 승인/거절 시스템

### 4. 참여자 관리 (Participant Management)

- 호스트를 위한 참여 신청자 관리(일괄 승인, 낙관적 업데이트 기반 상태 변경 등)

### 5. 마이페이지 (My Page)

- 내가 주최한 모임 및 참여한 모임의 상태별(모집 중, 종료 등) 관리

### 6. 실시간 채팅 (Real-time Chat)

- 모임에 참여한 사용자들이 실시간으로 메시지를 주고받는 기능

## 🛠 기술 스택 (Tech Stack)

### Core

- **Framework**: `React 19`
- **Language**: `TypeScript`
- **Build Tool**: `Vite`
- **Routing**: `React Router Dom v7`

### State Management

- **Server State**: `TanStack Query v5` (React Query)
- **Client State**: `Zustand`
- **Form State**: `React Hook Form` & `Zod` (Valdiation)

### UI & Styling

- **Styling**: `Tailwind CSS v4`
- **Components**: `shadcn/ui` (Radix UI 기반)
- **Icons**: `Lucide React`, `React Icons`
- **Animations**: `tailwindcss-animate`
- **Toast**: `Sonner`

### Documentation & Development

- **API Mocking**: `MSW (Mock Service Worker)`
- **Data Generation**: `Faker.js`
- **Formatting**: `ESLint`, `Prettier`

---

## 📁 프로젝트 구조 (Project Structure)

```text
src/
├── api/              # API 호출 함수 정의 (Axios 인터셉터, 도메인별 API)
├── assets/           # 정적 파일 (이미지, 아이콘 등)
├── components/
│   ├── ui/           # shadcn/ui 기반 공용 UI 컴포넌트
│   ├── common/       # 프로젝트 전반에서 사용되는 공통 컴포넌트 (Button, Input 등)
│   ├── layout/       # 페이지 레이아웃 컴포넌트 (Header, Sidebar, Shell)
│   └── features/     # 도메인별 핵심 기능 컴포넌트
│       ├── auth/     # 인증 관련 (로그인, 회원가입 폼)
│       ├── meetings/ # 모임 관련 (모임 카드, 개설 모달)
│       ├── chat/     # 채팅 관련 (말풍선, 입력창)
│       └── mypage/   # 마이페이지 관련 (참여자 관리 카드 등)
├── constants/        # 상수 값 관리 (관심사 카테고리, API 엔드포인트 등)
├── hooks/            # 커스텀 훅 (useAuth, useMeetingMutations 등)
├── lib/              # 외부 라이브러리 설정 (QueryClient, Axios 인스턴스)
├── mock/             # MSW 핸들러 및 모의 데이터 생성 (faker-js)
├── models/           # TypeScript 타입 및 인터페이스 정의
├── pages/            # 라우트별 페이지 컴포넌트
│   ├── user/         # 로그인, 회원가입, 비밀번호 재설정
│   ├── meetings/     # 모임 목록, 상세, 개설
│   ├── chat/         # 채팅 목록 및 대화창
│   └── mypage/       # 가입 정보, 내 모임, 참여 모임 관리
├── routes/           # 라우팅 설정
├── store/            # Zustand 전역 상태 저장소
├── utils/            # 유틸리티 함수
├── App.tsx           # 메인 애플리케이션 컴포넌트
├── main.tsx          # 엔트리 포인트
└── index.css         # 글로벌 스타일 (Tailwind CSS)
```

---

## 💡 개발 및 코딩 컨벤션

### 1. 상태 관리 전략

- **Server State**: 서버 데이터는 `React Query`를 통해 관리하며, 브로드캐스팅 및 낙관적 업데이트(Optimistic Updates)를 적극 활용합니다.
- **Client State**: UI의 일시적인 상태나 소규모 전역 데이터는 `Zustand`로 가볍게 관리합니다.

### 2. 컴포넌트 구조

- `components/ui`의 원자(Atomic) 컴포넌트를 조합하여 `features` 단위의 복합 컴포넌트를 구성합니다.
- 비즈니스 로직은 최대한 `hooks`로 추출하여 컴포넌트의 가독성을 유지합니다.

### 3. API 모킹

- 백엔드 API가 준비되지 않은 개발 단계에서는 `MSW`와 `Faker.js`를 사용하여 로컬에서 원활한 개발이 가능하도록 구성되어 있습니다.

---

## ⚙️ 시작하기 (Getting Started)

1. **패키지 설치**

   ```bash
   npm install
   ```

2. **개발 서버 실행**

   ```bash
   npm run dev
   ```

3. **빌드**

   ```bash
   npm run build
   ```

4. **린트 체크**
   ```bash
   npm run lint
   ```
