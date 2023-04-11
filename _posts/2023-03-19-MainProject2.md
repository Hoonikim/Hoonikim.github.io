---
layout: single
title: "[Project] 메인프로젝트 컴포넌트 "
categories: Project
tags: [배포, Helfit]
toc: true
published : false



---

###  2023.03.19(일)



이건 내가 유용?하게 사용했던 컴포넌트들의 모음이다. 

![스크린샷 2023-03-20 23.24.20](..assets/images/2023-03-19-MainProject2/스크린샷 2023-03-20 23.24.20.png)

category.tsx

```tsx
import React, { useState } from 'react';
import { Menu, MenuItemProps } from 'semantic-ui-react';
import styles from '../../styles/Community/C_Community.module.css';
import { useRouter } from 'next/router';

const menuItems = [
  { name: 'home', path: '/community' },
  { name: '헬스 갤러리', path: '/community/health' },
  { name: '크로스핏 갤러리', path: '/community/crossfit' },
  { name: '필라테스 갤러리', path: '/community/pilates' },
  { name: '오운완 갤러리', path: '/community/oww' },
  { name: '식단 갤러리', path: '/community/diet' }
];

const Category = () => {
  const router = useRouter();
  const [activeItem, setActiveItem] = useState<string>(
    menuItems.find((item) => item.path === router.pathname)?.name || 'home'
  );

  const handleItemClick = (
    event: React.MouseEvent<HTMLAnchorElement>,
    data: MenuItemProps
  ) => {
    const name = data.name as string;
    const path = menuItems.find((item) => item.name === name)?.path || '';
    setActiveItem(name);
    event.preventDefault();
    router.push(path);
  };

  return (
    <div>
      <Menu pointing secondary className={styles.Menubar}>
        {menuItems.map((item) => (
          <Menu.Item
            key={item.name}
            name={item.name}
            active={router.pathname === item.path}
            onClick={handleItemClick}
            className={
              activeItem === item.name ? styles.activeItem : styles.menuItem
            }
          />
        ))}
      </Menu>
    </div>
  );
};

export default Category;
```

Tag.tsx

![스크린샷 2023-03-20 23.25.25](..assets/images/2023-03-19-MainProject2/스크린샷 2023-03-20 23.25.25.png)

```tsx
import { useState } from 'react';
import style from '../../../styles/Community/C_Tag.module.css';

export interface TagProps {
  onTagAdd: (newTags: string[]) => void;
}

const Tag: React.FC<TagProps> = ({ onTagAdd }) => {
  const [tags, setTags] = useState<string[]>([]);
  const [tag, setTag] = useState<string>('');

  const removeTag = (i: number) => {
    const newTags = [...tags];
    newTags.splice(i, 1);
    setTags(newTags);
    onTagAdd(newTags);
  };

  const addTag = (e: React.ChangeEvent<HTMLInputElement>) => {
    const newTag = e.target.value.trim();
    if (newTag.length > 10 || tags.length >= 5) {
      return;
    }
    setTag(newTag);
  };

  const handleKeyPress = (e: React.KeyboardEvent<HTMLInputElement>) => {
    if (e.key === 'Enter') {
      handleClick();
    }
  };

  const handleClick = () => {
    if (tags.length >= 5) {
      return alert('tag는 최대 5개까지 추가할 수 있습니다.');
    }
    const newTags = [...tags, tag];
    setTags(newTags);
    setTag('');
    onTagAdd(newTags);
  };

  return (
    <div>
      <div className={style.TagContainer}>
        <input
          className={style.InputBox}
          placeholder='Press enter to add tags ...'
          onChange={(e) => addTag(e)}
          onKeyPress={(e) => handleKeyPress(e)}
          value={tag}
        />
        {tags.map((e, i) => (
          <div className={style.Hash} key={i}>
            <div className={style.HashName}>{e}</div>
            <div className={style.HashBtn} onClick={() => removeTag(i)}>
              x
            </div>
          </div>
        ))}
      </div>
    </div>
  );
};

export default Tag;
```

물론 이거 이외에도 처리해야할 코드들이 있겠지만 나름 열심히 만든 컴포넌트 코드들이라 블로그에 올려보았다. 