---
layout: single
title: "[회고] 프리 프로젝트 "
categories: 회고
tags: [회고, StackOverFlow]
toc: true

---

###  2023.03.02(금)

## Stack Over Flow 클론코딩

: stackoverflow 페이지를 정해진 기간 내에 똑같이 구현해내는 프로젝트 

<img alt="github logo" src="https://techstack-generator.vercel.app/github-icon.svg" width="65" height="65">[작업 GitHub](https://github.com/codestates-seb/seb42_pre_015)

<br/>

<div  align="center">
  <img width="80%" src="https://content.presspage.com/uploads/2658/c1920_logo-stackoverflow-banner.jpg?64224" alt="roobits">
</div>





- **`팀 명` :**  🐶 언더독 
- **`프로젝트 명` :** Stackoverflow
- **`프로젝트 기간` :** 2023.02.16 - 2023.03.02
- **`한줄 소개` :** Stackoverflow !  개발자간의 질의응답 커뮤니티입니다.
- **`팀원` :** 임희연(팀장), 한승완, 김세훈, 조영롱(부팀장), 이승배, 박의진
- **`배포 링크` :** [🌐 stackoverflowClone.Underdog](http://underdog15.s3-website.ap-northeast-2.amazonaws.com/)
- **`사용자 요구사항 정의서`:** [사용자요구사항 정의서](https://www.notion.so/codestates/4d8e708d11314d9c8e6ee04674e18907?pvs=4)

<br/>

### 💼 Team


|                     임희연<br>(FE, 팀장)                     |                        한승완<br>(FE)                        |                        김세훈<br>(FE)                        |                    조영롱<br>(BE,부팀장)                     |                        이승배<br>(BE)                        |                       박의진 <br>(BE)                        |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
| <img alt="임희연" src="https://cdn.discordapp.com/attachments/1073469469743128606/1080757691250651176/my_profile_pic.png" height="100" width="100"> | <img alt="한승완" src="https://cdn.discordapp.com/attachments/1074547492793897000/1080758041072369744/KakaoTalk_20230213_151839143.jpg" height="100" width="100"> | <img alt="김세훈" src="https://user-images.githubusercontent.com/104547038/222361813-b9748fa3-5754-43d5-8654-e16aadbfb08a.jpeg" height="100" width="100"> | <img alt="조영롱" src="https://cdn.discordapp.com/attachments/1074549201322659940/1080781411763634266/20220809_213109.jpg" height="100" width="100"> | <img alt="이승배" src="https://cdn.discordapp.com/attachments/1074548651763957801/1080759164084682892/KakaoTalk_20230213_150507142.jpg" height="100" width="100"> | <img alt="박의진" src="https://cdn.discordapp.com/attachments/1080750095684861962/1080759867268153445/KakaoTalk_20230302_165313193.jpg" height="100" width="100"> |
| - **Pages**<br/>-  Question detail page<br/>- Ask question page <br/>**Components**<br/>-  Navigation <br/>- Tag <br/>- Editor <br/>**Features**<br/>-  Question CRD<br/>- Answer CRD <br/> - Comment CRD  <br/>- Vote CD <br/> | - **Pages**<br/>-  Main page<br/>- Edit Question page<br/>- Edit Answer page<br/>**Components**<br/>-  Header <br/>- Side navigation <br/>**Features**<br/>-  Question RU<br/>- Answer U <br/> - Search by <br/>keywords, tags <br/>and username  <br/> | - **Pages**<br/>-  Signup page<br/>- Login page <br/>**Components**<br/>-  Buttons <br/>- Footer <br/>**Features**<br/>-  Email signup<br/>-  Email login<br/> logout <br/> - Manage access <br/>and refresh token  <br/>Readme  <br/> | -회원가입 기능<br/>(회원가입시 이메일 발송)<br/>\- 스프링 시큐리티<br/>(인증, 인가, JWT)<br/>(검색 기능)<br/>\- 배포 환경 구축<br/>(AWS 배포)<br/> | -CRUD<br/>-답변,댓글<br/>예외 처리<br/> 기능 구현<br/>답변 투표 실행<br/>- 취소 기능<br/> | -질문,댓글<br/>-TAG 등록 구현 <br/>-검색 기능 구현<br/>-투표 기능 구현<br/>-배포 환경 구성 <br/> |

<br/>

### <span style=""> ⚙️ **Tools** </span>

|                            Github                            |                           Discord                            |                            Notion                            |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
| <img alt="github logo" src="https://techstack-generator.vercel.app/github-icon.svg" width="65" height="65"> | <img alt="Discord logo" src="https://assets-global.website-files.com/6257adef93867e50d84d30e2/62595384e89d1d54d704ece7_3437c10597c1526c3dbd98c737c2bcae.svg" height="65" width="65"> | <img alt="Notion logo" src="https://www.notion.so/cdn-cgi/image/format=auto,width=640,quality=100/front-static/shared/icons/notion-app-icon-3d.png" height="65" width="65"> |

<br/>

### <span style=""> 🖥 **Front-end** </span>

|                             Html                             |                             CSS                              |                          JavaScript                          |                            React                             |                    Styled-<br>Components                     |                            axios                             |                           Prittier                           |                            esLint                            |                         React-Quill                          |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
| <img alt="Html" src ="https://upload.wikimedia.org/wikipedia/commons/thumb/6/61/HTML5_logo_and_wordmark.svg/440px-HTML5_logo_and_wordmark.svg.png" width="65" height="65" /> | <img src="https://user-images.githubusercontent.com/111227745/210204643-4c3d065c-59ec-481d-ac13-cea795730835.png" alt="CSS" width="50" height="65" /> | <img src="https://techstack-generator.vercel.app/js-icon.svg" alt="icon" width="75" height="75" /> | <img src="https://techstack-generator.vercel.app/react-icon.svg" alt="icon" width="65" height="65" /> | <img src="https://styled-components.com/logo.png" alt="styled-components icon" width="65" height="65" /> | <img src="https://axios-http.com/assets/logo.svg" width="65" height="65"/> | <img src="https://user-images.githubusercontent.com/81786662/210203759-1bd2d0ea-86b3-43c0-8e30-44436d73bb9f.png" width="65" height="65"/> | <img src="https://user-images.githubusercontent.com/81786662/210204062-cb572e61-2027-4a9b-a52c-0eac83bcf703.jpeg" width="100" height="65"/> | <img src="https://user-images.githubusercontent.com/81786662/210204172-8fc62516-4ee9-410d-859a-17a0da1e76f9.png" width="100" height="65"/> |

<br/>

### 🔒  **Back-end** 

|                             Java                             |                             AWS                              |                            mySQL                             |                             JWT                              |                            Spring                            |                        Spring<br>Boot                        |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
| <img src="https://techstack-generator.vercel.app/java-icon.svg" alt="icon" width="65" height="65" /> | <img src="https://techstack-generator.vercel.app/aws-icon.svg" alt="icon" width="65" height="65" /> | <img src="https://techstack-generator.vercel.app/mysql-icon.svg" alt="icon" width="65" height="65" /> | <img alt="spring-boot logo" src="https://play-lh.googleusercontent.com/3C-hB-KWoyWzZjUnRsXUPu-bqB3HUHARMLjUe9OmPoHa6dQdtJNW30VrvwQ1m7Pln3A" width="65" height="65" > | <img alt="spring logo" src="https://www.vectorlogo.zone/logos/springio/springio-icon.svg" height="50" width="50" > | <img alt="spring-boot logo" src="https://t1.daumcdn.net/cfile/tistory/27034D4F58E660F616" width="65" height="65" > |

<br/>

### 🌟 Pages & Features

|                                                              |                                                              |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
|                  **메인 페이지(검색,정렬)**                  |                 **로그인 / 회원가입 페이지**                 |
| <img width="100%" src="https://user-images.githubusercontent.com/104547038/222377949-97f367bb-cc29-4315-b559-871e75a1f828.gif"/> | <img width="100%" src="https://user-images.githubusercontent.com/104547038/222377978-7a4b1444-8c5c-4f66-81eb-d613b3e4dda4.gif"/> |
|                     **질문 게시글 작성**                     |                     **질문 게시글 삭제**                     |
| <img width="100%" src="https://user-images.githubusercontent.com/104547038/222381715-b6bd5bb2-e57a-4436-b62d-c7c3a17eac46.gif"/> | <img width="100%" src="https://user-images.githubusercontent.com/104547038/222381726-d322a447-e171-409b-a8f8-d54b20a35b7c.gif"/> |
|                    **게시글, 답변 수정**                     |                 **좋아요 & 답변 등록-삭제**                  |
| <img width="100%" src="https://user-images.githubusercontent.com/104547038/222378036-3c552bd3-2b15-4b5c-844b-92b172a1aebe.gif"/> | <img width="100%" src="https://user-images.githubusercontent.com/104547038/222381701-bcfd02f0-7d6b-40fd-b1bb-dd504410f6dd.gif"/> |

<br/>

## 나의 첫 프로젝트 시작 

------------

팀원분들은 스터디나 다른 활동들을 통해 이미 프로젝트 경험이 한 두번 정도는 있는 분들이셨다.  시작 전 개발방식에 대해 토론을 하는데 모르는 부분이 너무 많아서 작아지는 기분이 계속 들었다. 나는 모든게 처음이였기에 시작 전부터 배워가는 점이 너무 많아서 좋았다. 모르는 부분은 적극적으로 물어봤고 팀원분들은 너무 감사하게도 이해해주시며 세세하게 알려주셨다. 

드디어 시작된 프론트 개발 임무 분담, 크게 나누자면 게시판 CRUD, 재사용컴포넌트, 인증/보안 이렇게 나뉘어졌다. 다들 인증/보안쪽은 맡기 싫어하셔서 내가 맡기로 하고 꼭 팀원분들에게 멋지게 보여드리고 싶었다 

그렇게  로그인, 회원가입, OAuth, Button컴포넌트, Footer컴포넌트, Readme작성을  담당하게 되었다. JWT를 생각보다 깊이 있게 알고있지 못했고 쿠키나 로컬스토리지도 실제로 다뤄본적이 없어서 걱정이 많이 되었지만 꼼꼼하게 다시 복습하고 공부하면 잘해낼 수 있을 것이라고 자신했다. 



### KPT

------------------------

##### ✅ Keep

**JWT에 대한 이해**

 OAuth와 JWT중에 우리는 JWT에 좀 더 중점을 두기로 했었기 때문에 OAuth는 버튼 컴포넌트만 만들어 놓고 회원가입 로그인 구현을 먼저 진행했다. 정말 수많은 레퍼런스를 찾아보고 이전에 공부했던 복습도 하면서 거의 밤새가며 코드를 짯던 것 같다. 쿠키와 로컬스토리지 사용으로 백엔드와 조금의 이해충돌이 있었지만 로컬스토리지 저장으로 빠르게 문제를 해결했다. 

**아침 / 저녁 회의를 통한 F&B 진행상황 공유**

우리는 매일 아침 9시 오후5시 미팅을 진행했는데 오후미팅은 진행상황에 이슈가 있거나 프론트 or 백엔드 요청이 있을 경우에 진행했다. 미팅을 자주 진행하는 것이 나는 굉장히 좋았다. 백엔드와 진행상황 공유가 잘 이루어져서 작업의 속도를 잘 맞출 수 있었다. 

**팀원들 작업 서포트하기**

내 작업이 다른 팀원분들에 비해 하루정도 일찍 끝났다. 프로젝트는 나만 끝난다고 되는게 아니기 때문에 게시판 파트 권한부여나 Header 수정작업 등 남는 기간에도 열심히 팀원들을 도왔다



##### ✅ Problem

**OAuth2 실패**

 나와 백엔드분은 OAuth 구현이 처음이라 소통을 제대로 하지 않고 진행했던 문제가 컸다. 백엔드분은 서버방식의 OAuth2를 구현, 나는 클라이언트 방식 OAuth2를 구현하고 중간에서 발생하는 Cors에러에 굉장히 애를 먹었다. 정해진 시간이 있었기에 결국 해결하지 못하고 OAuth2에 실패했다. 지금 생각해보면 충분히 공부를 하지 않고 레퍼런스 코드를 뜯어보면서 코드만 작성하려 했던 것이 패착요인이였던 것 같다. 

**기록의 부재**

프로젝트를 하면서 발생했던 오류들이나 작업했던 기록을 블로그로 남기지 않았던게 너무 아쉬웠다. 

##### ✅ Try

**Grid의 사용**

레이아웃을 잡을 때 Flex로만 잡아봤던 나는 팀장님이 Grid를 사용하자고 했을 때 오 새로운거다 한번 해봐요 ! 공부해올게요 라고 이야기했었다. 
팀장님은 큰 틀만 Grid로 잡자고 한거였는데 나는 하룻밤새 Grid를 공부하면서 로그인페이지 하나를 다 Grid로 짰다. 다음날 팀원분들이 하루만에 Grid 장인이 되어 왔다며..칭찬아닌 칭찬을 해주셔서 엄청 웃으며..마무리 되었다.. 

**기획단계의 중요성 파악**

팀장님께서 매우 꼼꼼하셨던 분이라 기획단계에서 시간을 정말 많이 쏟았는데 이게 개발하면서 굉장히 편하게 느껴졌다. 기획이 굉장히 중요하단 걸 많이 느꼈다. 

**Git issues, Milestone, Project 활용**

매일 회의를 통해 진행상황을 잘 공유하긴 했지만 Git issues, Milestone, Project도 사용해보면서 팀프로젝트 관리를 더 세세하게 해보았다. 

**프로젝트 Readme 중요성**

깃허브로 블로그를 작성하는게 나뿐이여서 markdown 작업을 내가 진행했다. 프로젝트를 잘 관리한 다른 팀들을 보면 보통 ReadMe가 굉장히 잘 작성되어있는걸 보고 열심히 작업해서 우리팀도 나름 자랑할만한 ReadMe 파일 가지게 되었다. 



### 첫 프로젝트를 마치며 

-----------

2주동안 정말 너무 재밌게 했던 것 같다. 몸은 힘들었지만 나는 진짜 프로젝트 전에 비해서 정말 많이 성장했고 개발도 너무너무너무 재밌었다. 신나게 개발을 하고 시간을 보면 3~4시간씩 지나있고 단 한번도 지루하다고 생각했던 적은 없었던 것 같다. 너무 재미있었고 프로젝트를 해야 실력이 크게 향상된다고 많이 느꼇던 것 같다. 

이제 프리프로젝트에서 경험했던 것을 바탕으로 메인 프로젝트는 더 잘할수 있을거라고 확신한다. 분명 메인 프로젝트 때는 프리프로젝트보다 훨씬 어렵고 복잡한 로직, 다양한 이슈들이 많이 있을 것이다. 그래서 오히려 더 기대되고 메인 프로젝트가 끝나고 더 성장해있는 나를 상상하면 기분이 너무 좋아진다. 메인프로젝트도 화이팅 !!!





#### 🐶 팀원들 리뷰 

-----------------------

🐶 FE 승완님 리뷰

![스크린샷 2023-04-12 00 01 02](https://user-images.githubusercontent.com/104547038/231204568-b37d3b87-ef93-4bb1-bc15-586947fb5c49.png)

🐶 FE 희연님 리뷰

![스크린샷 2023-04-12 00 01 23](https://user-images.githubusercontent.com/104547038/231204698-344059ce-879d-4514-aee4-708af5fd8d55.png)

🐶 BE 영롱님 리뷰

![스크린샷 2023-04-12 00 01 41](https://user-images.githubusercontent.com/104547038/231204792-05d2d84d-970d-4e7b-bc47-eef4f432a368.png)
