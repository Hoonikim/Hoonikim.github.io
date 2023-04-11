---
layout: single
title: "[Project] 메인프로젝트 게시판 CRUD 2"
categories: Project
tags: [배포, Helfit]
toc: true
published : false



---

###  2023.03.21(화)



이전 포스팅에서 게시글을 post 하게 되면 &nspb 처럼 출력이 되었던 원인을 발견했다. 

분명 post요청을 보낼 때는 정상적으로 보내지는데 이게 서버로 들어가게 되면 위와 같이 읽혀져서 get요청시 그대로 출력되는 것 같았다.
다양한 해결 방법을 찾아보았고 이것 저것 많이 해봤지만 내가 선택한 방법은 두가지였다. 

1. dangerouslySetInnerHTML

```tsx
				<div className={style.Content_Text}>
            <div
              className='ql-editor'
              dangerouslySetInnerHTML={{
                __html: fetchedData?.text
              }}
            />
          </div>
```

사실 이 방법은 그다지 좋은 방법은 아니다. 
dangerouslySetInnerHTML은 브라우저 DOM에서 innerHTML을 사용하기 위한 React의 대체 방법이다.
일반적으로 코드에서 HTML을 설정하는 것은 사이트 간 스크립팅 공격에 쉽게 노출될 수 있기 때문에 위험하다.
따라서 React에서 직접 HTML을 설정할 수는 있지만, 위험하다는 것을 상기시키기 위해 **dangerouslySetInnerHTML을 작성하고 __html 키로 객체를 전달**해야 한다. 

이 방법을 사용한다고 해도 100프로 해결되는게 아니였다. 다만 &nspb 이렇게 나오던 말들이 `<p> 안녕하세요 </p>` 이렇게 출력될 뿐이였다.
아래의 방법까지 사용해서 p태그까지 없앨 수 있었다. 

2. 직접 자르기 

```tsx
  const escapeMap = {
    '&lt;': '<',
    '&#12296;': '<',
    '&gt;': '>',
    '&#12297;': '>',
    '&amp;': '&',
    '&quot;': '"',
    '&#x27;': "'"
  };
  const pattern = /&(lt|gt|amp|quot|#x27|#12296|#12297);/g;
  const convertToHtml = (text) =>
    text.replace(pattern, (match, entity) => escapeMap[`&${entity};`] || match);


useEffect(() => {
    const localUserId = JSON.parse(localStorage.UserInfo?.userId ?? 'null');
    axios
      .get(`${URL}/api/v1/board/${pageNumber}/${boardID}`)
      .then((res) => {
        const data = res.data;
        res.data.text = convertToHtml(res.data.text);
        setFetchedData(data);
      ...
```

이 방법은 같은 팀원이였던 지원님께서 추천해주신 방식으로 1번과 2번 방법을 모두 사용해서 해결했던 것 같다. 

#### 댓글 구현 

```tsx
// 댓글 작성
  const handleSubmit = (e: React.KeyboardEvent) => {
    if (typeof localStorage.accessToken !== 'undefined') {
      const userInfo: UserInfo = JSON.parse(localStorage.UserInfo);
      axios
        .post(
          `${URL}/api/v1/comment/${userInfo.userId}/${fetchedData.boardId}`,
          {
            commentBody: writeCommnet
          }
        )
        .then(() => {
          axios
            .get(`${URL}/api/v1/comment/${boardID}`)
            .then((res) => setComments(res.data))
            .catch((err) => console.log(err));
        })
        .then((res) => console.log(res));

      setWriteCommnet('');
    } else {
      alert('로그인 한 유저만 댓글을 작성할 수 있습니다.');
    }
  };

  // 댓글 삭제 commentId
  const handleDeleteComment = (commentId) => {
    const userInfo: UserInfo = JSON.parse(localStorage.UserInfo);
    axios
      .delete(
        `${URL}/api/v1/comment/${userInfo.userId}/${boardID}/${commentId}`
      )
      .then(() => {
        axios
          .get(`${URL}/api/v1/comment/${boardID}`)
          .then((res) => setComments(res.data))
          .catch((err) => console.log(err));
      })
      .then((res) => console.log(res))
      .catch((err) => console.log(err));
  };

// 엔터키로 댓글 등록 
const pressEnter: React.KeyboardEventHandler<HTMLInputElement> = (e) => {
    if (e.nativeEvent.isComposing) {
      return;
    }

    if (e.key === 'Enter' && e.shiftKey) {
      return;
    } else if (e.key === 'Enter') {
      e.preventDefault();
      handleSubmit(e);
    }
  };
  const handleClick = (e: React.MouseEvent<HTMLImageElement>) => {
    const keyboardEvent = e as unknown as React.KeyboardEvent;
    handleSubmit(keyboardEvent);
  };
```

댓글 부분은 수정기능은 넣지 않았고 삭제 기능만 넣어주었다. 로컬스토리지에 있는 userid와 댓글을 작성한 userid 를 비교해서 일치했을 경우에만 삭제버튼이 보이게 코드를 작성했다. 

<img width="1512" alt="스크린샷 2023-04-04 23 28 33" src="https://user-images.githubusercontent.com/104547038/229825133-e6eaa263-aedb-4751-be16-39e20b4736e0.png">

이것들 이외에도 다양한 기능들을 구현했다
 예를들어 1. 게시글 수정, 삭제 권한부여  2. 오운완 갤러리나 식단갤러리는 사진 필수  3. 좋아요, 댓글, 게시글 작성은 로그인한 유저만 등 대부분이 권한 부여에 관련된 것들이라 굵직한 것들 위주로만 작성해보았다. 
