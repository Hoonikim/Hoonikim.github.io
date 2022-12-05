---
layout: single
title: "[Network] OPEN API"
categories: Network
tags: [ Network, CodeStates]
toc: true


---

### 2022.12.05

### 💡  Open API

#### 📌 Postman

> 웹 개발에서 사용하는 대표적인 클라이언트 브라우저

![스크린샷 2022-12-05 13 32 37](https://user-images.githubusercontent.com/104547038/205550161-7a8bf220-6652-4312-ae56-8d1fbc2144db.png)



#### 📌 Postman 사용하기 

주어져 있는 API서버를 이용해서 간단하게 사용해보기 

##### Get [ 데이터 받아오기 ]

```md
URL : http://3.36.72.17:3000
// 메시지 조회 
Request : GET /kimcoding/messages
// 추가적인 파라미터 
roomname | 방 이름(문자열)
Response
[
  {
    "id": 1,
    "username": "김코딩",
    "text": "안녕하세요",
    "roomname": "로비",
    "date": "2021-04-02 12:00:00"
  }
 // ...여러 개의 메시지
]
```



<img src="https://user-images.githubusercontent.com/104547038/205550704-296329e1-4379-4a17-9eff-3d6a00d08e28.png" alt="스크린샷 2022-12-05 13 37 33" style="zoom:67%;" />

##### Post [ 데이터 추가 ]

```md
Response
{
  "id": 5 (ex)
}
```

<img src="https://user-images.githubusercontent.com/104547038/205551002-7aa3699b-94fa-4e41-b3f0-b3e2f0d74fa0.png" alt="스크린샷 2022-12-05 13 40 30" style="zoom:67%;" />

![스크린샷 2022-12-05 13 42 05](https://user-images.githubusercontent.com/104547038/205551155-663c0a6a-60f6-46a2-bee9-970dc806eaed.png)



![스크린샷 2022-12-05 13 41 17](https://user-images.githubusercontent.com/104547038/205551074-3a3195f9-ad88-4304-afcb-ee74641ed005.png)

post 후 get으로 원래 데이터 확인 

#### 📌 Postman with Open API

> openweathermap.org 페이지로 이동후 회원가입, API키 발급받기 
>
> API 리스트에서 Current Weather Data 들어간 뒤 By city ID에서 URI확인하기 

```md
api.openweathermap.org/data/2.5/weather?id={city id}&appid={your api key}
서울의 city id = 1835848
내 API key = bc9e459d84fde49321504e6b3161889b
```

![스크린샷 2022-12-05 13 48 29](https://user-images.githubusercontent.com/104547038/205551824-7b9670d0-e706-4c1d-a6b2-47fc352d4c8e.png)

**Postman**

![스크린샷 2022-12-05 13 49 06](https://user-images.githubusercontent.com/104547038/205551908-e7276004-3cac-4e3f-b186-d1abd7c7506e.png)