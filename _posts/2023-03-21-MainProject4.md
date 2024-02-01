---
layout: single
title: "[Helfit] 게시판 상세페이지 각 기능 & 조회 기능"
categories: Helfit
tags: [CRUD, Helfit]
toc: true

---

###  2023.03.21(화)

### 💡 상세페이지

상세페이지에서 내가 구현하려고 했던 기능 

* 좋아요 ( user id 당 1회 ), 조회수, 작성날짜, 댓글 기능 
* 권한: 게시글 수정 & 삭제 (작성자), 댓글 삭제 ( 작성자 ) -> 권한이 없는 사람에겐 보이지 않음 

-------

<img width="937" alt="스크린샷 2023-04-12 21 13 10" src="https://user-images.githubusercontent.com/104547038/231453690-a0a78ba5-4364-4476-9e35-fd3844fb1979.png">

#### 👨🏻‍💻 DetailP.tsx

##### 상세페이지 글 & 댓글 불러오기

useEffect를 사용해서 게시글을 불러오고 로컬 스토지리의 userid와 게시글의 userid를 비교해서 좋아요를 누른 유저라면 빨간색으로 하트표시가 누르지 않은 유저라면 빈 하트가 표시되도록 설정했다. 

```tsx
// 상세페이지 글이랑 댓글 불러오기
  useEffect(() => {
    const localUserId = JSON.parse(localStorage.UserInfo?.userId ?? 'null');
    axios
      .get(`${URL}/api/v1/board/${pageNumber}/${boardID}`)
      .then((res) => {
        const data = res.data;
        res.data.text = convertToHtml(res.data.text);
        setFetchedData(data);
        setLikeUser(
          data?.likeUserInfo
            ?.map((userInfo) => userInfo.userId)
            .filter((id) => typeof id === 'number') || []
        );
        const isLikedByUser = data?.likeUserInfo
          ?.map((userInfo) => userInfo.userId)
          .includes(Number(localUserId));
        setIsLiked(isLikedByUser);
      })
      .then(() => {
        axios
          .get(`${URL}/api/v1/board/view/${boardID}`)
          .then((res) => setViewCount(res.data.view));
      })
      .then(() => {
        axios
          .get(`${URL}/api/v1/board/likes/${boardID}`)
          .then((res) => setLikeCount(res.data));
      })
      .then(() => {
        axios
          .get(`${URL}/api/v1/comment/${boardID}`)
          .then((res) => setComments(res.data))
          .catch((err) => console.log(err));
      })
      .catch((err) => console.log(err));
  }, [boardID]); 
```

----------

##### 댓글 구현 

댓글은 엔터키를 입력했을 때, 연필 모양을 눌렀을 때 모두 작성이 완료되게 설정해두었고 마찬가지로 로컬 스토리지의 저장되어 있는 userid와 댓글을 작성한 userid를 비교해서 삭제버튼을 보이게 했다. 

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

처음에 enter키로 등록을 성공했는데 한글로 댓글을 입력하고 엔터키를 누르면 마지막에 입력한 글자도 같이 입력되는 경우가 있었다 
ex) 안녕 -> 안녕, ㅇ 이런식으로 두개가 작성되었다. 여러 레퍼런스를 찾아보고 위의 방법으로 해결했다. 

--------------

##### 좋아요 기능

좋아요 기능은 기능구현보다 오히려 하트의 색깔을 바꾸는게 좀 더 어려웠던 것 같다. ( 3.28 수정 -> 로컬에서는 기능구현이 잘 되었는데 배포 후 색깔이 변하지 않는 이슈 발생, git이 꼬인것 같은데 바로 해결 예정 )

좋아요는 로그인 한 유저만 누를 수 있기 때문에 error response를 확인해서 403에러 처리로 해결을 했고 좋아요 취소는 이미 좋아요를 누른 로그인 유저입니다로 표시를 해두었다가 좋아요 취소를 아래와 같이 구현했다. 

```tsx
const handleLikeClick = () => {
    const accessToken = localStorage.accessToken;
    axios
      .post(
        `${URL}/api/v1/board/likes/${boardID}`,
        {},
        {
          headers: {
            Authorization: `Bearer ${accessToken}`
          }
        }
      )
      .then((res) => setLikeCount(res.data))
      .then(() => setIsLiked(!isLiked))
      .then(() => router.reload())
      .catch((err) => {
        if (err.response.status === 403) {
          alert('로그인한 유저만 좋아요를 누를 수 있습니다.');
        } else if (err.response.status === 400) {
          axios
            .delete(`${URL}/api/v1/board/likes/${boardID}`, {
              headers: {
                Authorization: `Bearer ${accessToken}`
              }
            })
            //.then((res) => console.log(res))
            .then((res) => setLikeCount(res.data))
            .then(() => router.reload())
            .then(() => setIsLiked(!isLiked))
            .catch((err) => alert(err));
        } else {
          alert(err);
        }
      });
  };
```

-------------

##### 게시글 삭제 & 수정

게시글 삭제는 아래와 같이 modal로 구현을 해보았다. 

<img width="931" alt="스크린샷 2023-04-12 21 27 46" src="https://user-images.githubusercontent.com/104547038/231456777-8fe83541-5ff1-476d-992d-1b4f7839e26f.png">

```tsx
....
// 게시글 삭제
  const handleDeletePost = () => {
    const accessToken = localStorage.accessToken;
    axios
      .delete(`${URL}/api/v1/board/${pageNumber}/${boardID}`, {
        headers: {
          Authorization: `Bearer ${accessToken}`
        }
      })
      .then(() => {
        alert('성공적으로 삭제되었습니다.');
        router.push(`/community/${currentPage}`);
      })
      .catch((err) => {
        alert(err);
      });
  };				

				<div className={style.Buttons}>
            {fetchedData?.userId ===
              (typeof localStorage !== 'undefined' &&
                JSON.parse(localStorage.getItem('UserInfo') ?? '{}')
                  ?.userId) && (
              <Btn
                text='게시글 삭제'
                type='submit'
                className={style.ButtonD}
                onClick={handleDeletePostClick}
              />
            )}
            {isModalOpen && (
              <Modal
                isOpen={isModalOpen}
                onClose={() => setIsModalOpen(false)}
                onDelete={handleDeletePost}
              />
            )}
            {fetchedData?.userId ===
              (typeof localStorage !== 'undefined' &&
                JSON.parse(localStorage.getItem('UserInfo') ?? '{}')
                  ?.userId) && (
              <Btn
                text='게시글 수정'
                type='submit'
                className={style.ButtonU}
                onClick={handlePatch}
              />
            )}
          </div>
.....
```

------------

#### 👨🏻‍💻 PatchPost.tsx

수정 페이지에서 내가 원했던 기능은 오직 이거였다. 

* 카테고리는 변경이 불가능하며 나머지는 입력된 상태로 들어가게 하는 것 

<img width="1245" alt="스크린샷 2023-04-12 21 31 30" src="https://user-images.githubusercontent.com/104547038/231457808-9ace621b-432e-43e1-99ea-ca089d1ccdd9.png">

위 사진을 보면 카테고리, 제목, 내용은 잘 들어와져 있는 것을 확인할 수 있다. 하지만 태그나 사진은 아직 해결하지 못했다. 사진은 이전 포스트에서 말했듯이 구조가 조금 복잡하게 되어있기 때문에 어떻게 받아와야할지 생각을 좀 더 해봐야할 것 같다. 태그는 현재 해결중이다. 

```tsx
// 상세페이지 글불러오기
  useEffect(() => {
    axios
      .get(`${URL}/api/v1/board/${pageNumber}/${boardID}`)
      .then((res) => {
        const data = res.data;
        res.data.text = convertToHtml(res.data.text);
        setFetchedData(data);
        setTitle(res.data.title);
        setEditorInput(res.data.text);
        setSelectedFile(res.data.boardImageUrl);
      })
      .catch((err) => console.log(err));
  }, [boardID]);

....

 const handlePostButtonClick = () => {
    const titleError = validateTitle(title);
    const userID = JSON.parse(localStorage.UserInfo).userId;
    if (titleError) {
      setTitleError(titleError);
      return;
    }
    const accessToken = localStorage.accessToken;
    if (selectedFile) {
      const formData = new FormData();
      formData.append('multipartFile', selectedFile);
      return axios
        .post(`${URL}/api/v1/file/upload`, formData, {
          headers: {
            'content-type': 'multipart/form-data',
            Authorization: `Bearer ${accessToken}`
          }
        })
        .then((res) => {
          const boardImageUrl = res.data.body.resource;
          axios
            .patch(
              `${URL}/api/v1/board/${pageNumber}/${boardID}`,
              {
                title: title,
                text: editorInput,
                boardTags: tags,
                boardImageUrl: boardImageUrl
              },
              {
                headers: {
                  Authorization: `Bearer ${accessToken}`
                }
              }
            )
            .then(() => alert('게시글이 성공적으로 수정되었습니다.'))
            .then(() => router.push('/community'))
            .catch((err) => {
              alert('올바른 전송이 아닙니다.');
              console.log(err);
            });
        })
        .catch((err) => {
          alert('올바른 전송이 아닙니다.');
          console.log(err);
        });
    } else {
      axios
        .patch(
          `${URL}/api/v1/board/${pageNumber}/${boardID}`,
          {
            title: title,
            text: editorInput,
            boardTags: tags,
            boardImageUrl: selectedFile
          },
          {
            headers: {
              Authorization: `Bearer ${accessToken}`
            }
          }
        )
        .then(() => alert('게시글이 성공적으로 수정되었습니다.'))
        .then(() => router.push('/community'))
        .catch((err) => {
          alert('올바른 전송이 아닙니다.');
          console.log(err);
        });
    }
  };

```

우선 기능적인 부분에서는 다 구현을 했지만 디테일한 부분까지는 잡지 못했던 것 같다. 추후 리펙토링을 통해 디테일한 부분까지 다 잡아서 포스팅 할 예정이다. 

