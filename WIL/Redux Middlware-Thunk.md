**리덕스**를 사용하는 어플리케이션에서 **비동기 작업**을 처리 할 때 가장 기본적인 방법으로는 redux-thunk 라는 미들웨어를 사용하는것입니다.

리덕스에서 dispatch를 하면 action 이 리듀서로 전달이 되고, 리듀서는 새로운 state를 반환합니다.

근데 미들웨어를 사용하면 이 과정 사이에 하고 싶은 작업들을 넣어서 할 수 있습니다.

thunk를 사용하면 우리가 dispatch를 할때 **객체가 아닌 함수를 dispatch** 할 수 있게 해준다.

즉, dispatch(객체) 가 아니라 dispatch(함수)를 할 수 있게 되는 것

그래서 중간에 우리가 하고자 하는 작업을 함수를 통해 넣을 수 있고, 그것이 중간에 실행이 되는 것입니다.

> thunk란, 특정 작업을 나중에 하도록 미루기 위해서 함수형태로 감싼 것을 칭합니다.
> 

```
dispatch(함수) → 함수실행 → 함수안에서 dispatch(객체)
```

이 함수를 **thunk 함수** 라고 부릅니다.

참고사이트

[https://teamsparta.notion.site/04-Thunk-part-1-5eb463c026074c6cb90b23ddfa9fe6f2](https://www.notion.so/5eb463c026074c6cb90b23ddfa9fe6f2)

[https://redux-advanced.vlpt.us/2/01.html](https://redux-advanced.vlpt.us/2/01.html)
