---
title: "[회고] On My Ticket"
categories: OMT
tags: [회고, OMT]
toc: true
layout: archive
author_profile: true
types: posts
docs: OMT

---

###  2024.01.29(월)

<br/>

<div  align="center">
  <img width="80%" src="https://github.com/Hoonikim/Hoonikim.github.io/assets/104547038/42b8a22b-1b1d-4282-b19c-e02453d974f8" alt="OMT">
</div>



- **`프로젝트 명` :** OnMyTicket [ OMT ]

- **`프로젝트 기간` :** 2023.09.02 - 2024.01.26

- **`한줄 소개` :** OnMyTicket  -  대표 영화관 3사의 예매기능의 통합, 나만의 티켓을 통한 유저의 컬렉션을 모을 수 있는 웹 페이지

- **`팀원` :** 김세훈 (팀장), 김지열

- **`배포 링크` :** [🌐 OnMYTicket ](https://omt-onmyticket.vercel.app/)

- **`작업 깃허브 링크` :**<img alt="github logo" src="https://techstack-generator.vercel.app/github-icon.svg" width="65" height="65"> [ OMT ](https://github.com/OMT-OnMyTicket/OMT)

- **`사용자 요구사항 정의서`:** [사용자요구사항 정의서](https://docs.google.com/spreadsheets/d/1VlqhETC1om6duJ2IAhafjqzjnjXuem83h4loEhI-Uqc/edit#gid=0)

- **`테이블 명세서`:** [테이블 명세서](https://docs.google.com/spreadsheets/d/1ERTUD86rGCYTPDTLLCHrb4GBEBrCmKRUJdhToXBn89I/edit#gid=0)

- **`API 명세서`:** [API 명세서](https://documenter.getpostman.com/view/24688585/2s9YJXZk52#29253473-b2f2-4ddc-be3a-f04c66b51ca2)

  

<br/>

### 💼 Team


|                       김세훈<br/>(FE)                        |                        김지열<br>(BE)                        |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| <img alt="김세훈" src="https://user-images.githubusercontent.com/104547038/228111580-6ec31d43-8cca-4df9-8646-397f0fa6eebd.jpg" height="100" width="100"> | <img alt="김지열" src="https://user-images.githubusercontent.com/104547038/228111594-faa75c09-7693-4d17-974c-f294df7c74f9.jpg" height="100" width="100"> |
| - **Front의 모든 파트**<br/><br />- **Introduction Page**<br />- AOS & CSS 적극 활용<br /><br />- **Main Page**<br />- 검색 ,영화 예고편 , 무비차트, 각종 정보등<br /> 다양한 기능 제공<br />- Youtube, KMDB, KOPIC등 API 적극 활용<br /><br />- **Ticketing Page**<br />- 빠른 예매와 직접 예매<br />- **빠른예매 Page**<br />- KaKao Map Api 활용<br />- 유저 선택지 최소화<br />- Loding을 이용한 데이터 선별<br />- **직접예매 Page**<br />- 실제 예매와 같은 좌석, 시간 선택<br />- 유저의 모든 선택 권한제공<br />- **결제 Page**<br />- TossPayments Api 활용<br /><br />- **Search Page**<br />- 키워드 연관 단어, 자동완성<br />- 영화 정보 제공<br />- 나만의 티켓 추가 기능 제공<br /><br />- **My ticket Page**<br />- 나만의 티켓 제공 (오리지널 티켓)<br />- 함께 시청한 사람, 나만의 리뷰, 별점 기능<br />- 나만의 영화 순위 기능 <br /> |                 - **Back의 모든 파트**<br/>                  |



 

<br/>

### <span style=""> ⚙️ **Tools** </span>

|                            Github                            |                           Discord                            |                            Notion                            |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
| <img alt="github logo" src="https://techstack-generator.vercel.app/github-icon.svg" width="65" height="65"> | <img alt="Discord logo" src="https://assets-global.website-files.com/6257adef93867e50d84d30e2/62595384e89d1d54d704ece7_3437c10597c1526c3dbd98c737c2bcae.svg" height="65" width="65"> | <img alt="Notion logo" src="https://www.notion.so/cdn-cgi/image/format=auto,width=640,quality=100/front-static/shared/icons/notion-app-icon-3d.png" height="65" width="65"> |

<br/>

#### 🖥 **Front-end** 

Main Stack / Sub Stack

|                             Html                             |                             CSS                              |                          TypeScript                          |                            NextJS                            |                            Figma                             |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
| <img alt="Html" src ="https://upload.wikimedia.org/wikipedia/commons/thumb/6/61/HTML5_logo_and_wordmark.svg/440px-HTML5_logo_and_wordmark.svg.png" width="100vh"  /> | <img src="https://user-images.githubusercontent.com/111227745/210204643-4c3d065c-59ec-481d-ac13-cea795730835.png" alt="CSS" width="100vh" /> | <img src="https://techstack-generator.vercel.app/ts-icon.svg" alt="icon" width="100vh" /> | <img src="https://noticon-static.tammolo.com/dgggcrkxq/image/upload/v1566879300/noticon/fvty9lnsbjol5lq9u3by.svg" alt="icon" width="100vh"  /> | <img src="https://noticon-static.tammolo.com/dgggcrkxq/image/upload/v1640982247/noticon/tpvr26zp02angin4t0jv.png" alt="icon" width="100vh" /> |

|                          KaKao Map                           |                            axios                             |                           Prittier                           |                            esLint                            |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
| <img src="https://play-lh.googleusercontent.com/Nvrf8Z89_3S8H6YnOLgyAbe-PSSeCZnJDA8zv7LY04hEvi8atTgp_fmQ5RZ591Qpxh5G=w600-h300-pc0xffffff-pd" width="100vh"/> | <img src="https://axios-http.com/assets/logo.svg" width="100vh" /> | <img src="https://noticon-static.tammolo.com/dgggcrkxq/image/upload/v1566918959/noticon/fvlo9g4lxojigdn72l8i.png" width="100vh"/> | <img src="https://noticon-static.tammolo.com/dgggcrkxq/image/upload/v1599890132/noticon/c9dgkhp3m5rxmzn3fnp9.png" width="100vh"/> |

<br/>

#### 🔒  **Back-end** 



|                             Java                             |                             AWS                              |                            mySQL                             |                             JWT                              |                            Spring                            |                         Spring Boot                          |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
| <img src="https://techstack-generator.vercel.app/java-icon.svg" alt="icon" width="100vh" /> | <img src="https://techstack-generator.vercel.app/aws-icon.svg" alt="icon" width="100vh" /> | <img src="https://techstack-generator.vercel.app/mysql-icon.svg" alt="icon" width="100vh" /> | <img alt="spring-boot logo" src="https://play-lh.googleusercontent.com/3C-hB-KWoyWzZjUnRsXUPu-bqB3HUHARMLjUe9OmPoHa6dQdtJNW30VrvwQ1m7Pln3A" width="100vh" > | <img alt="spring logo" src="https://www.vectorlogo.zone/logos/springio/springio-icon.svg" width="100vh" > | <img alt="spring-boot logo" src="https://t1.daumcdn.net/cfile/tistory/27034D4F58E660F616" width="100vh" > |

<br/>

<br/>

#### 🌟 Pages & Features

|                          소개페이지                          |                          메인페이지                          |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| <img width="100%" src="https://github.com/OMT-OnMyTicket/OMT/assets/104547038/fcec50d9-919b-4585-aea5-b3cda80e09ec"/> | <img width="100%" src="https://github.com/OMT-OnMyTicket/OMT/assets/104547038/6290d663-f545-49fa-914f-c2b4b9c640f2"/> |
|                         **예매Home**                         |                        **직접 예매**                         |
| <img width="100%" src="https://github.com/OMT-OnMyTicket/OMT/assets/104547038/a4e0fe1d-7e79-4db2-b412-70dbb138d261"/> | <img width="100%" src="https://github.com/OMT-OnMyTicket/OMT/assets/104547038/58a667c6-5a1d-471c-8d60-bf4a8398f441"/> |
|                        **빠른 예매**                         |                       **검색 페이지**                        |
| <img width="100%" src="https://github.com/OMT-OnMyTicket/OMT/assets/104547038/8821a4fd-abc2-4e32-ac71-e400cbfba43b"/> | <img width="100%" src="https://github.com/OMT-OnMyTicket/OMT/assets/104547038/e24dda17-d0aa-4734-ad64-311f72834831"/> |
|                      **MyTicket Intro**                      |                       **Ranked Movie**                       |
| <img width="100%" src="https://github.com/OMT-OnMyTicket/OMT/assets/104547038/9a913e30-5dcd-4a97-ab67-f9af95da6c49"/> | <img width="100%" src="https://github.com/OMT-OnMyTicket/OMT/assets/104547038/27bf7c64-50bd-4599-9816-068bb0a3722d"/> |
|                       **TicketRoom **                        |                      **Ticket Review**                       |
| <img width="100%" src="https://github.com/OMT-OnMyTicket/OMT/assets/104547038/a05d2aad-f17d-4c26-a8c4-0c2a60d538d8"/> | <img width="100%" src="https://github.com/OMT-OnMyTicket/OMT/assets/104547038/f36aefbd-ac33-4f8a-a0ad-566825d18a48"/> |

-----------------





#### 🙆‍♂️ 회고

### KPT

------------------------

##### ✅ Keep

**다양한 API의 활용**

솔로 프로젝트로 기획했기 때문에 내가 활용할 수 있는 API를 사전에 찾아두는 것이 굉장히 중요했다. KMDB, KOPIC 같은 대 용량의 데이터는 관리해본적이 처음이라 많이 당황스러웠지만 필요한 데이터만 추출해서 잘 해결한 것 같다. 

이전 프로젝트인 헬핏에서 지도 관련 API를 내가 해보고 싶었지만 기회가 되지 않아 못했었고 당시 담당하셨던 분께서 굉장히 어려워하셨어서 이번 프로젝트에 지도 API를 꼭 넣고싶었다. 생각보다 굉장히 간단하게 끝냈고 마커 부분과 서치 결과 추출 부분만 좀 더 공부해보면 더 좋은 결과물을 낼 수 있을 것 같다. 

**추가 편의기능에 대한 고찰**

프로젝트를 진행하면서 더 좋은 편의기능에 대해 생각했던 것 같다. 항상 내가 유저라면? 으로 접근했고 ' 이렇게 하면 더 편하겠다. ' 라는 생각으로 추가적인 기능들을 넣어뒀던 것 같다. 중간중간 더 욕심났던 부분들도 있지만 적절한 타협점을 찾아서 잘 추가해준 것 같다. 

**다양한 CSS 시도**

css는 매번 어렵다... 이번엔 나 혼자 모든걸 결정해야 했기에 최대한 멋지게 만들어내고 싶었다. 애니메이션 효과를 적극 활용했고 이전엔 몰랐던 상투적인 방식을 좀 더 매끄럽게 만들어냈다. ( 예를들어 Hover시 크기가 커지게 하는걸 width로 조정하는 것이 아닌 scale을 통해 조정 )

**두 가지 배포 방식 시도**

초반에 Vercel로도 배포를 진행해보고 AWS로도 배포를 해보았다. 우선 내가 느끼기엔 두 가지 방식 중 배포시간이 훨씬 빠르고 배포방식이 몹시 간단한건 Vercel인 것 같다. Vercel로 처음 배포했을 땐 30분 정도만에 끝냈는데 AWS로 배포할 땐 3시간이 넘게 걸렸다.. 물론 둘다 통달했다는 아니지만 아직까진 Vercel을 통한 배포가 내겐 접근성이 좋다. 

**책임감**

당연하다. 내가 하기로 한 프로젝트이고 이 프로젝트가 곧 내 실력을 보여주는 것이기에 항상 내 기준 최선의 방법을 탐색하고 진행하려 했다. 

**Next에 대한 이해**

이번에 Next.js13으로 프로젝트를 진행했는데 이전 Helfit 프로젝트 때 버전과 파일트리나 라우팅 방법이 달라져서 처음에 굉장히 혼란스러웠다. 역시 프론트는 빠르게 변화하는구나를 느꼈고 다시 공부했다. 

Next.js 13 버전은 정보가 턱없이 부족했고 이전 버전에서 구동되던 코드들 중 안되는 코드들도 정말 많았기에 공식 홈페이지를 통해 많은 공부를 했다 



**메모의 습관화**

이번 프로젝트에서는 아이디어가 생각날 때마다 메모장에 메모를 해왔다. 형식에 구애받지 않고 자유롭게 메모를 진행했고 이게 진짜 큰 도움이 많이 됐다. 

다만 단점이 조금 있었다면 너무 자유로워서 해당 내용을 찾지 못하고 다시 새로운 아이디어로 진행했던 적도 있었다. 특정 파트, 어느 부분 정도는 대제목으로 구분을 해놔야겠다. 



##### ✅ Problem

**커뮤니케이션**

지열님께 원하는 목적을 명확하게 전달하지 못했던 것 같다. 각자 개발을 진행하고 나서 회의를 진행하면 내가 원했던 결과물과 많이 달랐다. 유저가 어떤식으로 접근하는지, 데이터를 어떻게 보낼건지, 어떤 페이지에서 이 데이터를 받을지, 받은 데이터는 어떻게 사용되는지 등등 나름 정리하고 말한다고 생각했는데 역시 내가 명확하지 않으면 상대방도 무슨 소리인지 모른다. 내가 원하는 바를 확실하게 정리하고 상대방의 이해를 묻는 행동이 더욱이 필요했다. ( 함께 만들어 나가는 것이기에 꼭 필요한 부탁은 잘못된 게 아니다.. 모든걸 알아서 하려고 하지말자...  )

**프로젝트 스케줄 관리**

스케줄 관리를 잘 못했다. 이전 프로젝트에서는 협업이기 때문에 매일 아침에 모여 각자의 스케줄을 정리하고 끝낸 일, 진행할 일을 정리했는데 이번 프로젝트는 혼자라서 이 부분을 안일하게 생각했던 것 같다. 처음엔 스케줄 관리를 했지만 이후엔 점점 안하게 되었다. 지금 생각해보면 이 스케줄 관리만 잘했어도 프로젝트 완성 기간을 대폭 단축할 수 있었을 것 같다... 

**명확한 기간 설정**

프로젝트 기간을 명시하지 않았다. 때문에 여유를 너무 부렸던 것 같다. 취업준비를 하면서 공부하는 느낌으로 진행한 프로젝트라고 해도 기간을 여유롭게라도 명시했어야 했다. 

**반응형 웹**

위의 두 문제점으로 이 결과를 나타냈다. 우선 모든 기능과 디자인을 구현해냈고 지열님도 개발을 마치기 위해 프로젝트를 끝냈다. 반응형 웹은 필수라고 생각한다. 모바일 버전을 기반으로 코드를 만들었어야 했는데 이번에도 마찬가지로 웹버전을 기준으로 신나게 코딩을 진행해버렸다. 

3월내로 모바일 버전까지 끝내놓자... 



##### ✅ Try

**원하는 바를 확실하게 말하기**

**메모의 활용 -> 프로젝트 스케줄 공유**

**3월 내로 모바일 버전 개발완성**



### 첫 프로젝트를 마치며 

-----------

내가 만들고 싶었던 웹 페이지를 만들어보고 싶었고 내 한계에 부딪혀보고 싶었다. 그래서 서버리스한 솔로 프로젝트로 기획을 했었고 정 필요하다면 자체 서버 개발이 가능한 **Next.js**를 통해 개발을 하니 공부를 통해서 필요한 부분만 서버를 만들어 나가며 프로젝트를 진행하려고 했다. 

프로젝트를 시작한 지 한 달 정도 지났을까? 전에 함께 프로젝트를 진행했던 백엔드 지열님께서 혹시 같이 해도 되냐는 의견을 보내주셨고 지열님이 계신다면 로그인 관리나 필요하다고 생각되는 서버 부분은 맡길 수 있어서 함께 진행하기로 했다.  



사실 혼자 진행하려했던 프로젝트여서 체계가 확립되어 있지는 않았다. 요구사항 정의서도 만들지 않았고 내가 필요한 기능을 정리해놓은 메모장? 정도였다. 
부랴부랴 함께 회의를 하면서 요구사항 정의서도 만들어보고 체크리스트도 만들고 노션도 만들고 정신이 없었다. 지열님도 그렇고 나도 그렇고 서로 취업준비를 하면서 진행했기 때문에 이전 프로젝트처럼 명확하게 시간을 정해놓고 개발을 진행하지 않았다. 정해놓은 것은 매일 7~8시 사이에 회의를 진행한다는거 ? 이 마저도 시간이 지나면서 일주일에 2~3회로 줄어들었다. 

내가 만들고싶은 웹 페이지를 만들어보는 것이기 때문에 빠른예매나 나만의 티켓처럼 아이디어가 생기면 즉각 적용이 가능했고 그렇기에 최대한 서버에 부담을 주지 않으려 노력했다. 처음 기획도 그러했었고 그렇기에 찾아놓았던 api들이 많았다. 이번 프로젝트에서 **KMDB, Toss, Kakao map, KOPIC** 등 정말 다양한 api들을 사용했다. 특히 KMDB를 사용하면서 데이터를 거르는데 시간을 많이 쏟았던 것 같다. 영화라는게 워낙 방대한 양의 데이터를 가지고 있고 그 데이터를 필요할 때마다 다 불러들일 수 는 없기 때문에 나름 최대한의 거름망(코드)을 만드려고 했던 것 같다. 

영화 포스터를 받아오지 못한다던지 겹치는 영화제목일 때 다른 영화의 정보를 가져온다던지 api가 내 뜻대로 되지 않는 경우가 많았다. 그럴땐 api를 제공했던 페이지를 찾아가 더 필터링 할 수 있는 코드가 있는지 주의깊게 찾아보고 postman을 통해 계속해서 테스트했다. 

CSS에서도 정말 고생을 많이 했는데 프론트 작업을 혼자했더라도 정말 멋진 웹페이지를 만들고 싶어서 이전엔 한번도 해보지 않았던 디자인적인 도전을 많이했다.  그래도 이번엔 레이아웃 짜는거에 고통 받지는 않았고 새로운 디자인 작업에서 많이 힘들었다. 

이 외에도 많은 힘듦이 있었지만 나 혼자서 어디까지 할 수 있는지 그리고 더 성장하고 싶은 마음에 이 프로젝트를 시작했고 정말 오롯이 내 프로젝트다 생각하니 즐거운 마음이 더 컸었던 것 같다. 

그리고 실제로 많이 배웠고 많이 성장했다. 

