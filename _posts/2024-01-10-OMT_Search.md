---
title: "[OMT] Route로 느낀 동기와 비동기"
categories: OMT
tags: [Route, OMT]
toc: true
layout: archive
author_profile: true
types: posts
docs: OMT

---

###  2023.01.10(수)

<br/>

OMT 프로젝트를 체크해보다 Search 페이지에서 예상치 못한 오류를 경험하게 되었다. 

검색을 진행한 뒤 Search 페이지로 넘어가고 그 Search 페이지에서 검색을 다시 할 경우 검색어가 제대로 입력되지 않고 검색결과가 제대로 도출되지 않는 현상이 있었다. 



#### 💡원래 코드 

```tsx
 const handleClickSearch = (id: string) => {
    localStorage.removeItem('검색어');
    localStorage.setItem('검색어', id);

    router.push('/search');
  };

```

이렇게 진행했을 때의 문제점은 아래와 같다. 

<img width="1489" alt="블로그1" src="https://github.com/OMT-OnMyTicket/OMT/assets/104547038/c2df9545-5290-4e4e-b838-8ad5547d3d18">



##### ❌ 문제점

이미 path가 /search로 잡혀있기 때문에 LocalStorage에 검색어 관련 부분만 계속해서 추가되고 페이지를 reload 하지 않는 이상 검색한 부분을 찾아오지 않았다. 



#### 💡해결 방법

``` tsx
const handleClickSearch = (id: string) => {
    localStorage.removeItem('검색어');
    localStorage.setItem('검색어', id);

    if (pathname === '/search') {
      location.reload();
    } else {
      router.push('/search');
    }
  };
```



조건문을 걸고 코드를 위와같이 짜게 되면 path가 Search일 때 페이지를 리로드 하고 그렇지 않을 때는 원래처럼 Search 페이지로 push한다. 

#### 📌 해결 결과 

<img width="1442" alt="블로2" src="https://github.com/OMT-OnMyTicket/OMT/assets/104547038/402c9612-6ac0-4337-a41a-9996cd46027a">

위와 같이 페이지가 정상적으로 검색어를 변경하면서 결과를 가져온다. 



#### 💡 여기서 드는 의문점 

```tsx
const handleClickSearch = (id: string) => {
    localStorage.removeItem('검색어');
    localStorage.setItem('검색어', id);
    router.push('/search');
      location.reload();
  };
```

코드는 위에서 순서대로 적용이 되는데 push 하고 reload 시키면 되는거 아닌가 ? 

##### ‼️그 결과 

<img width="1445" alt="블로그3" src="https://github.com/OMT-OnMyTicket/OMT/assets/104547038/d8bb439f-e0cc-481a-8982-5800f65d0c1f">

검색페이지로 넘어가지 않고 Home화면에서 머물게 된다. 

 pathname이 /search 페이지로 넘어가야지 왜 home으로 되는가? 에 대한 궁금증이 생겼다.



##### 💡 공부를 통해 정확히 알게된 점 

`  router.push 메서드는 비동기식으로 이루어져있고 탐색이 완료되면 확인되는 promise를 반환한다고 한다. `

즉 나처럼 코드를 작성할 경우 router.push('/search')는 '/search' 페이지로의 탐색을 트리거하지만 탐색이 완료될 때까지 즉시 기다리지 않고 다음 코드 줄 location.reload()로 이동한다. search 컴포넌트가 있는 Home화면서에서 위와같이 코드를 실행하면 router.push('/search')가 시작되고 이후 location.reload()가 즉시 호출되고 이 시점에서는 탐색이 아직 완료되지 않았을 수 있으므로 location.reload()는 '/search' 탐색이 완료되기를 기다리는 대신 효과적으로 현재 페이지(홈 화면)를 다시 로드하기 때문이였다.

Next.js에서 라우팅의 비동기 특성을 처리하고 탐색 다음의 모든 작업이 콜백에 배치되도록 하거나 필요한 경우 router.push 메서드와 함께 await를 사용해야 하는지 확인하는 것이 중요하다고 한다... 



그동안 router.push를 정말 많이 사용해왔지만 내가 사용하는 메서드 마다 동작하는 원리를 모르고 사용했던 경우가 태반이었던 거 같다. 동기와 비동기에 대한 직접적인 경험은 처음이라 더 많은 공부가 된 것 같다. 