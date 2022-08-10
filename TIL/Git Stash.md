브랜치를 check out 해야 할 때가 생겼다.

그런데 지금 작업하고 있는 내용이 다 날아갈건데 커밋하긴 애매하고 저장은 해두고싶을 때

### STASH

를 사용하면 좋다.

나는 source tree 를 애용한다.

### 1. 현재 브랜치에서 stash 하기

![img](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4467e511-b536-4155-8257-14f68053a78e/Untitled.png)

스태시를 누르면 메세지를 입력할 수 있는 창이 나온다.

여기에 어떤 작업인지 커밋 메세지처럼 간략하게 적어준다.

### 2. 다른 브랜치로 check out 해서 작업하기

### 3. 작업 종료 후, 기존 브랜치로 check out 해서 돌아오기

### 4. Stash 해뒀던 작업 빼내기

소스트리에서 터미널 버튼을 클릭해서 터미널을 열어준다 (상단 오른쪽에 있다)

![img](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e49aefdd-8b62-435e-98d2-4ef95d02e17e/Untitled.png)

```jsx
git stash list
```

내가 stash한 목록들을 볼 수 있다.

```jsx
git stash apply
```

가장 최근에 넣은 stash가 적용된다.

-끝 -

참고사이트 : 

[https://americanopeople.tistory.com/12](https://americanopeople.tistory.com/12)
