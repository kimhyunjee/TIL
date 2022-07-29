# 정리

- `useEffect`는 화면에 컴포넌트가 mount 또는 unmount 됐을 때 실행하고자 하는 함수를 제어하게 해주는 훅이다.
- **의존성 배열을 통해 함수의 실행 조건을 제어**할 수 있다.
- `useEffect` 에서 함수를 1번만 실행시키고자 할때는 **의존성 배열을 빈 배열**로 둔다.

# 더 알아보면 좋은 키워드

## `Strict mode`란 무엇일까?

가끔 엄격하지 않은 기본값을 "**[느슨한 모드](https://developer.mozilla.org/ko/docs/Glossary/Sloppy_mode)**(sloppy mode)"라고 부르기도 합니다. 공식적인 용어는 아니지만 혹시 모르니 알아두세요.

[ECMAScript 5](https://www.ecma-international.org/publications/standards/Ecma-262.htm) 에서 소개된 JavaScript 의 엄격모드는 JavaScript 의 제한된 버전을 선택하여 암묵적인 "**[느슨한 모드](https://developer.mozilla.org/ko/docs/Glossary/Sloppy_mode)**(sloppy mode)" 를 해제하기 위한 방법입니다. 엄격 모드는 단지 부분적인 것이 아니며, 이것은 *고의적으로* 일반 코드와 다른 시멘틱을 가지고 있습니다. 엄격모드를 지원하지 않는 브라우저에서는 엄격 모드의 코드가 다른 방식으로 동작할 것입니다, 그 때문에 엄격 모드가 적절하게 적용된 피쳐 테스트 없이 엄격 모드에 의존하면 안됩니다. 엄격 모드의 코드와 비-엄격 모드의 코드는 공존할 수 있으며, 때문에 스크립트의 엄격 모드를 취사 선택하는 것이 점진적으로 가능하게 되었습니다.

엄격 모드는 평범한 JavaScript 시멘틱스에 몇가지 변경이 일어나게 합니다.

1. 기존에는 조용히 무시되던 에러들을 throwing합니다.
2. JavaScript 엔진의 최적화 작업을 어렵게 만드는 실수들을 바로잡습니다. 가끔씩 엄격 모드의 코드는 비-엄격 모드의 동일한 코드보다 더 빨리 작동하도록 만들어집니다.
3. 엄격 모드는 ECMAScript의 차기 버전들에서 정의 될 문법을 금지합니다.

코드를 JavaScript의 변형이 제한된 환경에서 동작하도록 하고 싶다면, 엄격 모드로의 변환([transitioning to strict mode](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode/Transitioning_to_strict_mode))을 참고하세요.

→ES5부터 적용된 엄격모드- 다소무시되던 문법들을 (실수)들을 당장 문제가 없어도 에러로 표시해서 즉각 고치게 한다.

strict mode와 비슷한 기능을 하는게 eslint같은 확장프로그램이다.

출처:[https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Strict_mode](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Strict_mode)

추가로 읽어본 페이지 :[https://poiemaweb.com/js-strict-mode](https://poiemaweb.com/js-strict-mode)

## React 라이프 사이클이란 무엇일까?

컴포넌트는 생성(mounting) -> 업데이트(updating) -> 제거(unmounting)의 생명주기를 갖습니다.

리액트의 클래스 컴포넌트는 라이프 사이클 메서드를 사용하고, 함수형 컴포넌트는 Hook을 사용합니다.

컴포넌트가 실행되거나 업데이트되거나 제거될 때, 특정한 이벤트들이 발생합니다.

### **Class Componet 생명주기**

### 👀 마운트(mount)

컴포넌트가 생성 될때 발생하는 생명주기들을 알아봅시다.

### ☑️ constructor

컴포넌트 생성자 메서드, 컴포넌트가 생성되면 가장 먼저 실행되는 메서드this.props, this.state에 접근이 가능하고 리액트 요소를 반환합니다.

### ☑️ getDerivedStateFromProps

props로부터 파생된 state를 가져옵니다. 즉 props로 받아온 것을 state에 넣어주고 싶을때 사용합니다.

### ☑️ render

컴포넌트를 렌더링하는 메서드입니다.

### ☑️ componentDidMount

컴포넌트가 마운트 됨, 즉 컴포넌트의 첫번째 렌더링이 마치면 호출되는 메서드 입니다.이 메서드가 호출되는 시점에는 화면에 컴포넌트가 나타난 상태입니다.여기서는 주로 DOM을 사용해야 하는 외부 라이브러리 연동, 해당 컴포넌트에서 필요로하는 데이터를 ajax로 요청, 등의 행위를 합니다.

```
useEffect(()=>{
	console.log("componentDidMount");
},[])
```

### 👀 업데이트(updating)

컴포넌트가 업데이트되는 시점에 어떤 생명주기 메서드들이 호출되는지 알아봅니다.

### ☑️ getDerivedStateFromProps

컴포넌트의 props나 state가 바뀌었을때도 이 메서드가 호출됩니다.

### ☑️ shouldComponentUpdate

컴포넌트가 리렌더링 할지 말지를 결정하는 메서드입니다.

- `React.memo`와 유사함, boolean 반환으로 결정

### ☑️ componentDidUpdate

컴포넌트가 업데이트 되고 난 후 발생합니다.

- 의존성 배열이 변할때만 useEffect가 실행하는 것과 같음

```
useEffect(() => {
	console.log("count or exampleProp changed");
},[count, exampleProp]);
```

### 👀 언마운트(unmount)

언마운트라는 것은 컴포넌트가 화면에서 사라지는 것을 의미합니다. 언마운트에 관련된 생명주기 메서드는 `componentWillUnmount` 하나입니다.

### ☑️ componentWillUnmount

컴포넌트가 화면에서 사라지기 직전에 호출됩니다.여기서 주로 DOM에 직접 등록했었던 이벤트를 제거하고, 만약에 `setTimeout`을 걸은 것이 있다면 `clearTimeout`을 통하여 제거를 합니다.추가적으로, 외부 라이브러리를 사용한게 있고 해당 라이브러리에 dispose기능이 있다면 여기서 호출해주시면 됩니다.

```
useEffect(()=>{
	console.log("");
    return(() => exampleAPI.unsubscribe());
})
```

출처:[https://velog.io/@minbr0ther/React.js-리액트-라이프사이클life-cycle-순서-역할](https://velog.io/@minbr0ther/React.js-%EB%A6%AC%EC%95%A1%ED%8A%B8-%EB%9D%BC%EC%9D%B4%ED%94%84%EC%82%AC%EC%9D%B4%ED%81%B4life-cycle-%EC%88%9C%EC%84%9C-%EC%97%AD%ED%95%A0)

### React에서 말하는 mount와 unmount란 무엇일까?

mount란? 컴포넌트가 화면에 나타나는것, unmount란 컴포넌트가 화면에서 사라지는 것을 뜻한다.
