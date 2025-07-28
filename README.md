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

[![Watch the video](https://img.youtube.com/vi/qy8u18SyypM/hqdefault.jpg)](https://www.youtube.com/watch?v=qy8u18SyypM&t=7s)

1. 글, 댓글, 좋아요, 해쉬태그 CRUD 설계 및 기능 구현
2. 대댓글 작성, 댓글과 대댓글 soft delete 구현
3. Filter를 이용해 작성글의 공개범위 설정 기능 구현
4. Json을 이용해 kakao map api 기능 구현
<hr/>

### 데이터 베이스 설계

<img width="512" height="261" alt="unnamed" src="https://github.com/user-attachments/assets/3b237117-1680-42ef-9137-5e557f416d69" />

<hr/>

### 트러블 슈팅
<details>
  <summary><strong>1. 글과 댓글 즉시 반영</strong></summary>
  • <strong>문제 상황</strong>: 글과 댓글 작성시 페이지를 수동 리다이렉트해야만 반영되는 문제가 발생 <br/>
  • <strong>원인 분석</strong>: useEffect, useCallback 등의 최적화 미흡 <br/>
  • <strong>해결 방법</strong>: useCallback과 useEffect를 사용해 리렌더링을 최소화, 최신 데이터가UI에 즉시 반영될 수 있게 수정
</details>
<details>
  <summary><strong>2. 글 목록 무한 스크롤 시 중복 데이터 로딩</strong></summary>
  • <strong>문제 상황</strong>: 글 리스트에서 데이터를 중복해서 불러오는 오류 발생 <br/>
  • <strong>원인 분석</strong>: 글 리스트를 불러올 때 기준값 누락 <br/>
  • <strong>해결 방법</strong>: 글 리스트를 불러올 때 lastId를 기준으로 불러오도록 기준값 부여
</details>
<details>
  <summary><strong>3. 지도 링크가 메인페이지에서 보이지 않는 오류</strong></summary>
  • <strong>문제 상황</strong>: 로컬스토리지에 저장된 지도 링크를 메인 페이지에서 불러올 수 없는 오류 발생 <br/>
  • <strong>원인 분석</strong>: 로컬스토리지에 저장된 링크를 사용하는 로직 누락 <br/>
  • <strong>해결 방법</strong>: localStorage.getItem(‘kakaoMapLink’) 로직 부여<br/> → setLocationLink로 상태값 연동해 사용
</details>
<details>
  <summary><strong>4. 비공개 상태인 리트윗 글 표시</strong></summary>
  • <strong>문제 상황</strong>: 비공개 상태인 리트윗된 글이 리스트에 표시되는 문제 발생 <br/>
  • <strong>원인 분석</strong>: 리트윗된 글의 공개범위가 private상태인지 확인하는 구문 누락 <br/>
  • <strong>해결 방법</strong>: 리트윗한 글의 상태를 확인하는 공개범위 검사 조건 추가
</details>
<details>
  <summary><strong>5. 비로그인 유저 좋아요 클릭</strong></summary>
  • <strong>문제 상황</strong>: 비로그인 상태의 유저가 좋아요를 클릭 가능한 문제 발생 <br/>
  • <strong>원인 분석</strong>: 좋아요를 누르는 조건에 Userid검사가 누락되어 발생 문제 <br/>
  • <strong>해결 방법</strong>: if문을 사용해 !Userid라면 좋아요를 누를 시 로그인 오류 처리
</details>
<hr/>

### 느낀 점

![느낀점](https://github.com/user-attachments/assets/ffb9fb8d-812a-4609-bed7-7f06844fa5f0)
