먼저 일반 업데이트 방식으로 onClick안에서 `setNumber(number + 1)` 를 3번 호출했습니다. **number가 1씩 증가하는군요.**

```jsx
// src/App.js

import { useState } from "react";

const App = () => {
  const [number, setNumber] = useState(0);
  return (
    <div>
			{/* 버튼을 누르면 1씩 플러스된다. */}
      <div>{number}</div> 
      <button
        onClick={() => {
          setNumber(number + 1); // 첫번째 줄 
          setNumber(number + 1); // 두번쨰 줄
          setNumber(number + 1); // 세번째 줄
        }}
      >
        버튼
      </button>
    </div>
  );
}

export default App;
```

이번에는 함수형 업데이트 방식으로 동일하게 작동시켜보겠습니다. **number가 3씩 증가하네요.**

```jsx
// src/App.js

import { useState } from "react";

const App = () => {
  const [number, setNumber] = useState(0);
  return (
    <div>
			{/* 버튼을 누르면 3씩 플러스 된다. */}
      <div>{number}</div>
      <button
        onClick={() => {
          setNumber((previousState) => previousState + 1);
          setNumber((previousState) => previousState + 1);
          setNumber((previousState) => previousState + 1);
        }}
      >
        버튼
      </button>
    </div>
  );
}

export default App;
```

- **왜  다르게 동작할까요?**
    
    **일반 업데이트 방식**은 버튼을 클릭했을 때 첫번째 줄 ~ 세번째 줄의 있는 setNumber가 각각 실행되는 것이 아니라, 배치(batch)로 처리합니다. **즉 우리가 onClick을 했을 때 setNumber 라는 명령을 세번 내리지만, 리액트는 그 명령을 하나로 모아 최종적으로 한번만 실행**을 시킵니다. 그래서 setNumber을 3번 명령하던, 100번 명령하던 1번만 실행됩니다. 
    
    반면에 **함수형 업데이트 방식**은 **3번을 동시에 명령을 내리면, 그 명령을 모아 순차적으로 각각 1번씩 실행**시킵니다.  0에 1더하고, 그 다음 1에 1을 더하고, 2에 1을 더해서 3이라는 결과가 우리 눈에 보이는 것이죠. 
    

## 3. 정리

- useState의 업데이트 방식은 2가지 방식이 있으며, 각각 다르게 동작한다.
- useState 로 원시데이터가 아닌 데이터를 변경할때는 불변성을 유지해야 한다.

## 4. 더 알아보면 좋은 키워드

### 왜 리액트팀은 useState가 위 방식으로 동작하도록 만들었을까?

- 이는 seState의 비동기적 특성 때문이다.
- 리액트가 효율적으로 렌더링하기 위해 여러 개의 상태 값 변경 요청을 batch(일괄 처리) 처리하기 때문이다.
- batch 처리의 이유는 당연히 성능 이슈 때문이다. -> 리렌더링을 발생하는 setState가 일어날 때마다 리렌더링이 일어난다면 얼마나 많은 렌더링이 일어나겠는가? 그렇다면 setState를 사용하기가 두려워질 수도 있을 듯하다.

→ setState를 동기적으로 사용하려고 ! 함수형 업데이트 사용

setState에 값을 그대로 전달하는 것이 아니라 함수를 전달하는 것이다.

### useState 작동방식
useState ,setState 오해한 점 잘 설명되어있음 !!

[https://velog.io/@jjunyjjuny/React-useState는-어떻게-동작할까](https://velog.io/@jjunyjjuny/React-useState%EB%8A%94-%EC%96%B4%EB%96%BB%EA%B2%8C-%EB%8F%99%EC%9E%91%ED%95%A0%EA%B9%8C)

**[React] useState 비동기 처리와 함수형 업데이트**

[https://dududweb.tistory.com/m/34](https://dududweb.tistory.com/m/34)

hook 공식문서의 개요

[https://ko.reactjs.org/docs/hooks-overview.html](https://ko.reactjs.org/docs/hooks-overview.html)
