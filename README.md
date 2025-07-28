# SSDAM
![스크린샷_27-7-2025_13223_](https://github.com/user-attachments/assets/7e10324a-9e41-4b6d-97f4-7fe313ebcca0)

## Team GitHub
- https://github.com/dpflaalee/sseudamsseudam

### 목차
- 1️⃣ [프로젝트 개요](#프로젝트-개요)
- 2️⃣ [기술 스택](#기술-스택)
- 3️⃣ [담당 기능](#담당-기능)
- 4️⃣ [데이터 베이스 설계](#데이터-베이스-설계)
- 5️⃣ [트러블 슈팅](#트러블-슈팅)
- 6️⃣ [느낀 점](#느낀-점)
<hr/>

### 프로젝트 개요
반려동물을 키우는 사람들 또는 동물을 사랑하는 사람들을 위한 **일상 공유 기반 SNS 플랫폼**입니다.
사용자들은 자신의 일상을 기록하고, 반려동물 중심의 콘텐츠를 공유하며, 서로 소통할 수 있는 기능을 제공합니다.

**"기획 배경"** <br/>
반려동물을 키우거나 동물을 좋아하는 사람들이 자신의 경험을 기록하고, 공감하고, 정보를 교류할 수 있는 SNS 플랫폼이 부족하다고 느꼈습니다.
이에 따라 일상 공유와 소셜 소통, 그리고 목표 기반 챌린지 기능을 결합한 동물 중심 SNS 플랫폼을 기획하게 되었습니다.
<hr/>

### 기술 스택

#### 🛠️ 기술 스택
<details>
  <summary><strong>📌 메인 언어 & 기본 도구</strong></summary>
  • Node.js 1.0.0 <br/>
  • React 18.3.1 <br/>
  • JavaScript
</details>
<details>
  <summary><strong>⚙️ 서버 환경 및 웹 프레임워크</strong></summary>
  • Express 5.1.0 <br/>
  • Next.js 13.4.13 <br/>
  • Nodemon 2.0.22
</details>
<details>
  <summary><strong>📁 환경 변수 관리</strong></summary>
  • dotenv 16.5.0 
</details>
<details>
  <summary><strong>🗄️ 데이터베이스 관련</strong></summary>
  • MySQL 3.14.1 <br/>
  • Sequelize 6.37.7 <br/>
  • Sequelize CLI 6.6.3 <br/>
  • Axios 1.9.0
</details>
<details>
  <summary><strong>🔒 보안 관련</strong></summary>
  • bcrypt 6.0.0 <br/>
  • passport 0.7.0 <br/>
  • passport-local 1.0.0 <br/>
  • CORS 2.8.5
</details>

#### 🧰 활용 장비 및 라이브러리
<details>
  <summary><strong>🖼️ 파일 업로드 및 이미지 처리</strong></summary>
  • Multer 2.0.1 <br/>
  • react-slick 0.30.3
</details>
<details>
  <summary><strong>🎨 UI 및 디자인</strong></summary>
  • Ant Design 4.24.16 <br/>
  • ant-design/icons 6.0.0 <br/>
  • styled-components 5.3.11 <br/>
  • react-calendar 6.0.0 <br/>
  • react-cookie 8.0.1
</details>
<details>
  <summary><strong>🔄 상태 관리 및 라우팅</strong></summary>
  • Redux 4.0.5 <br/>
  • Redux-Saga 1.1.3 <br/>
  • react-redux 8.0.5 <br/>
  • next-redux-wrapper 7.0.0 <br/>
  • react-router-dom 7.6.2
</details>
<hr/>

### 담당 기능
#### 📺 시연 영상 (이미지 클릭시 유튜브로 이동됩니다.)

[![Watch the video](https://github.com/user-attachments/assets/849e4806-7c1e-4a26-b407-a34dcc83ce01)](https://www.youtube.com/watch?v=wXk6alDPh-4)

1. 관리자 상품 CRUD 설계 및 기능 구현
2. 랜덤박스  CRUD 설계 및 기능 구현
3. 쿠폰 CRUD 설계 및 기능 구현

<hr/>

### 데이터 베이스 설계

<img width="512" height="261" alt="unnamed" src="https://github.com/user-attachments/assets/3b237117-1680-42ef-9137-5e557f416d69" />

<hr/>

### 트러블 슈팅
<details>
  <summary><strong>1. 유효기간 미체크로 만료된 랜덤박스 사용 가능 문제</strong></summary>
  • <strong>문제 상황</strong>: usedAt 또는 dueAt 필드에 대한 유효성 검증 누락으로 만료된 랜덤박스를 계속 사용할 수 있었음 <br/>
  • <strong>원인 분석</strong>: 서버 로직에서 만료 여부 확인 조건 누락, 프론트엔드 만료 알림 기능 미흡 <br/>
  • <strong>해결 방법</strong>: 백엔드: 랜덤박스 사용 API에서 dueAt 날짜를 필수 검사하도록 로직 강화 <br/>
                               프론트엔드: 만료된 박스를 ‘사용 불가’ 상태로 UI 표시 및 사용 시도 시 경고 메시지출력 <br/>
  • <strong>효과</strong>: 만료된 박스 사용 사전 방지, 사용자 혼란 최소화
</details>

<details>
  <summary><strong>2. 랜덤박스 사용 시 예외 미처리로 서버 에러 발생</strong></summary>
  • <strong>문제 상황</strong>: 존재하지 않는 issuedBoxId 또는 잘못된 사용자 ID 요청 시 서버가 500 Internal Server Error 반환, 클라이언트에 명확한 오류 안내 없음 <br/>
  • <strong>원인 분석</strong>: 입력값 검증과 권한 확인 로직 부재, 예외 처리 미흡으로 서버 예외가 터짐 <br/>
  • <strong>해결 방법</strong>: <br/>
  o 요청값 Null 체크 및 유효성 검증 로직 추가 <br/>
  o 사용자 권한 검증으로 요청자의 사용 권한 확인 <br/>
  o IllegalArgumentException 및 커스텀 예외 처리기로 명확한 오류 메시지와 HTTP 상태 코드 전달 <br/>
   • <strong>효과</strong>: 안정적 서버 운영과 명확한 에러 안내로 사용자 경험 개선
</details>

<details>
  <summary><strong>3. 동시 요청으로 하나의 박스에서 중복 아이템 발급 문제</strong></summary>
  • <strong>문제 상황</strong>: 여러 탭 또는 동시 요청 시 같은 랜덤박스에서 복수 아이템 중복 발급 현상 발생 <br/>
  • <strong>원인 분석</strong>: sedAt 체크 없이 동시 여러 트랜잭션 처리로 경쟁 상태 발생 <br/>
  • <strong>해결 방법</strong>: <br/>
  o 트랜잭션 내에서 usedAt 필드가 null인지 선점하여 체크 <br/>
  o 조건 만족 시에만 업데이트 및 아이템 발급 처리 수행 <br/>
  o 데이터베이스 락 또는 Optimistic Locking 도입 고려 <br/>
   • <strong>효과</strong>: 중복 발급 방지 및 데이터 무결성 확보
</details>
<hr/>

### 느낀 점

![느낀점](https://github.com/user-attachments/assets/050ba167-c3e6-4008-b79a-27c8ed9c0735)
