---
layout: single
title: "[Project] 메인프로젝트 게시판 CRUD1 "
categories: Project
tags: [배포, Helfit]
toc: true
published : false


---

###  2023.03.20(월)



회원 유저 관리를 모두 완료하고 게시판 CRUD작업으로 넘어왔다 

유저관리는 리덕스 툴킷과 react-useContext를 사용해서 전역에서 관리하려 하였으나 새로고침을 하게되면 값이 날아가서 사용하기 무척 어려웠다. 분명 다른 방법이 있겠지만 프로젝트 남은 기간이 부족하기 때문에 로컬스토리지에 저장하고 게시판 작업으로 넘어갔다. 

이전 프리때와 다른점은 확실히 진행이 빠르다는 점이다. 지난 프리때는 2주라는 기간 동안 로그인/회원가입 유저관리에 쩔쩔매고있었는데 이번에는 일주일도 안되서 모두 해결했다. 전역에서 유저정보를 관리하는 리덕스와 useContext때문에 시간을 많이 허비한 것을 생각하더라도 시간이 매우 많이 단축되었다. 

프리때 게시판 작업을 많이 돕긴했지만 내가 직접한 것이 아니라서 굉장히 걱정이 많았다. 

지금까지 작업한건 게시글 작성과 조회이다. 

1. 게시글 작성

![스크린샷 2023-03-20 23.11.59](..assets/images/2023-03-20-MainProject2/스크린샷 2023-03-20 23.11.59.png)

이 페이지를 작성하면서 react-quill때문에 고생을 많이했다.. 지금도 계속 조금씩 에러를 발생시키는중.. 
여기서 가장 힘들었던 점은 카테고리, 테그 부분이였다. 카테고리 쪽은 별도로 semantic-ui-react를 사용했는데 다루기 정...말 까다로웠다... 

axios쪽은  사진을 다른 api로 전송해야 된다는 점에서 조금 해맸던 것 같다. 

```tsx
...
// 먼저 options로 각 갤러리별 key와 value(백엔드에서 주는)를 설정했다. 
const options: Option[] = [
  { key: 'health', text: '헬스 갤러리', value: '1' },
  { key: 'crossfit', text: '크로스핏 갤러리', value: '2' },
  { key: 'pilates', text: '필라테스 갤러리', value: '4' },
  { key: 'oww', text: '오운완 갤러리', value: '5' },
  { key: 'diet', text: '식단 갤러리', value: '6' }
];
...
const handlePostButtonClick = () => {
    const titleError = validateTitle(title);
    const userID = JSON.parse(localStorage.UserInfo).userId;
    if (titleError) {
      setTitleError(titleError);
      return;
    }
    const accessToken = localStorage.accessToken;
    axios
      .post(
        `${URL}/api/v1/board/${category}/${userID}`,
        {
          title: title,
          text: editorInput,
          boardTags: tags.map((tag) => ({ tagName: tag }))
        },
        {
          headers: {
            Authorization: `Bearer ${accessToken}`
          }
        }
      )
      // .then(() => {
      //   const accessToken = localStorage.accessToken;
      //   const formData = new FormData();
      //   formData.append('multipartFile', selectedFile);
      //   axios.post(`${URL}/api/v1/file/upload`, formData, {
      //     headers: {
      //       'content-type': 'multipart/form-data',
      //       Authorization: `Bearer ${accessToken}`
      //     }
      //   });
      // })
      .then(() => alert(`userid: ${userID}  게시글 등록 성공`))
      .then(() => router.push('/community'))
      .catch((err) => {
        alert(err);
      });
  };
```

담긴 데이터를 보내는 방법이나 유효성을 검사하는 방법은 멘토님께서 추천해주신 react-hook-form을 사용해봤는데 정말 편하게 구현했다. 

카테고리 쪽은 react hook form이 아니라 유효성 검사를 아직 구현하지 못했다.....

```tsx
			{/* 카테고리 */}

        <div className={style.category}>
          <div className={style.titleMessage}>
            <div className={style.Text}>카테고리</div>
            <div className={style.Subtext}>
              카테고리는 반드시 설정해주어야 합니다.
            </div>
          </div>
          <DropdownC options={options} onChange={handleDropdownChange} />
        </div>

        {/* 태그 */}

        <div className={style.tag}>
          <div className={style.titleMessage}>
            <div className={style.Text}>태그</div>
            <div className={style.Subtext}>
              태그는 최대 5개까지 추가할 수 있습니다.
            </div>
          </div>
          <Tag onTagAdd={handleTagAdd} />
        </div>

        {/* 제목 */}

        <div className={style.title}>
          <div className={style.titleMessage}>
            <div className={style.Text}>Title</div>
            <div
              className={style.Subtext}
              style={{ color: titleError ? 'red' : 'var(--text_5)' }}
            >
              {titleError || '제목은 반드시 입력해야 합니다.'}
            </div>
          </div>
          <div className={style.TitleInput}>
            <input
              type='text'
              placeholder='Write your Title...'
              className={style.TitleInput}
              value={title}
              onChange={handleTitleInputChange}
              onBlur={() => setTitleError(validateTitle(title))}
            />
          </div>
        </div>
```





2. 카테고리별 게시글 조회 

![스크린샷 2023-03-20 23.00.42](..assets/images/2023-03-20-MainProject2/스크린샷 2023-03-20 23.00.42.png)

여기서 가장 어려웠던 점은 하나의 파일로 각 갤러리를 처리하려고 했는데 실패하고 우선 pages폴더 아래에 각 갤러리 폴더를 만들고 index와 [id] 를 별도로 생성해서 해결했다. 



```tsx
// 전체 코드가 아닌 나름 고생했던? 핵심? 코드들만 불러와 보면 아래와 같다. 
interface Post {
  boardId: number;
  boardImageUrl: string | null;
  createdAt: string;
  modifiedAt: string;
  tags: { tagId: number; tagName: string }[];
  text: string;
  title: string;
}
type Props = {
  posts: Post[];
};
// 여기서 부터 데이터를 가져오는 코드 
const HealthPost: React.FC = () => {
  const [fetchedPosts, setFetchedPosts] = useState<Post[]>([]);

  useEffect(() => {
    axios
      .get(`${URL}/api/v1/board/2?page=1`)
      .then((res) => setFetchedPosts(res.data))
      .catch((err) => console.log(err));
  }, []);

  const PostCard: React.FC<{ post: Post; order: number }> = ({ post, order }) => {
    const { title, tags, createdAt } = post;

    const createdAtString = new Date(createdAt)
      .toLocaleDateString('en-KR', {
        year: '2-digit',
        month: '2-digit',
        day: '2-digit'
      })
      .split('/')
      .join('.');

    return (
      <div>
        <li className={style.ListItem}>
          <div className={style.No}>{order}.</div>
          <div className={style.title}>{title}</div>
          <div className={style.nickName}>닉네임</div>
          <div className={style.date}>{createdAtString}</div>
          <div className={style.tag}>
            {tags.map((tag) => (
              <span className={style.tagItem}>{tag.tagName}</span>
            ))}
          </div>
          <div className={style.views}>조회수</div>
        </li>
      </div>
    );
  };
  .....
  return(
  ....
   <div className={style.ListBody}>
          <ul>
            {fetchedPosts.map((post, index) => (
              <li key={post.boardId}>
                <Link href={`/community/crossfit/${post.boardId}`}>
                  <PostCard post={post} order={index + 1} />
                </Link>
              </li>
            ))}
          </ul>
        </div>
.....
```

그 뒤에는 내가 이전에 짜놓았던 레이아웃에 위와같이 뿌려주었다. 

3. 상세페이지 

이부분은 상당히 골머리를 쌓았다. 내가 작업한 방식이 좀 특이한 것 같고 주먹구구 식으로 진행한 것 같아 멘토님께 조만간 코드리뷰를 부탁드려놓았다. 

![스크린샷 2023-03-20 23.05.48](..assets/images/2023-03-20-MainProject2/스크린샷 2023-03-20 23.05.48.png)

게시글 작성 에디터를 프리때 사용했던 react quill을 가져와 사용했는데 위 처럼 좀 이상하게..들어간다.. 수정할 예정

여기서는 next.js를 사용하는 가장 큰 이유를 찾았던 것 같다. boardID를 추출하는데에 시간을 많이 쏟긴 했지만 페이지 url 이동이나 구성 자체는 굉장히 쉽게 구현했다. 

**[id].tsx** 최고다 정말 👏🏻

```tsx
// 상세페이지는 코드를 불러오는데에 상당히 애를 먹었다. 
// 백엔드 쪽에서 받아오는 정보에 userId나 boardId를 조회하는 방법에 대해 고민하다가 내가 boardId로 params를 구성한 것을 깨닫고 
// url에서 boardId와 카테고리를 가져와 사용하였고 향수 userID를 비교해서 일치할 경우에만 게시글 삭제,수정 버튼을 보이게 수정할 것이다. 
interface BoardData {
  boardId: number;
  title: string;
  text: string;
  boardImageUrl: string | null;
  tags: {
    tagId: number;
    tagName: string;
  }[];
  createdAt: string;
  modifiedAt: string;
}
......
const router = useRouter();
  const { id } = router.query;
  const boardID = id ? parseInt(id[id.length - 1]) : null;
  const currentPage = router.asPath.split('/')[2];
  let categoryname: string;
  let pageNumber: Number;
  switch (currentPage) {
    case 'health':
      pageNumber = 1;
      categoryname = '헬스 갤러리';
      break;
    case 'crossfit':
      pageNumber = 2;
      categoryname = '크로스핏 갤러리';
      break;
    case 'pilates':
      pageNumber = 4;
      categoryname = '필라테스 갤러리';
      break;
    default:
      pageNumber = null;
  }

  useEffect(() => {
    const userID: number = JSON.parse(localStorage.UserInfo).userId;
    axios
      .get(`${URL}/api/v1/board/${pageNumber}/${userID}/${boardID}`)
      .then((res) => setFetchedData(res.data))
      .catch((err) => console.log(err));
  }, [boardID]);

// 이런식으로 데이터를 가져와서 내가 만든 레이아웃에 뿌려주었다. 
```

분명 잘 진행중이긴 하지만 조금 찝찝한 부분이 많다. 기간이 이주가 조금 안되게 남아있기 때문에 시간이 남을 것 같은데 전체 코드 리펙토링을 꼭 진행하고 싶다. 

