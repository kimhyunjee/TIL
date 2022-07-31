component !
컴포넌트는 웹사이트를 구성하는 조각이다 !

 

예시

<header/>

<container/>

<imagebanner/>

<contents1/>

<footer/>

 

컴포넌트에서 데이터를 관리하는 법 ?
 

state

state는 Component가 가지고 있는 데이터입니다.

state는 한 컴포넌트에서만 사용하는 정보를 주로 넣어놓고 생성, 수정하는 데이터입니다.
생성도 수정도 오직 해당 컴포넌트 내에서만 이루어집니다. 해당 컴포넌트의 것이니 그 컴포넌트 안에서는 수정이 자유롭다 !
props

props는 자식 컴포넌트가 부모 컴포넌트로부터 받아온 데이터입니다.

고로, 자식 컴포넌트로서는 부모의 컴포넌트 데이터를 바꿀 수 없습니다 ! (props는 본인 데이터가 아니라서  ! )

 

 

setState()

는 컴포넌트의 state 객체에 대한 업데이트를 실행합니다. state가 변경되면, 컴포넌트는 리렌더링됩니다.

 

state와 props의 차이점 !
props (“properties”의 줄임말) 와 state 는 일반 JavaScript 객체입니다. 두 객체 모두 렌더링 결과물에 영향을 주는 정보를 갖고 있는데, 한 가지 중요한 방식에서 차이가 있습니다. props는 (함수 매개변수처럼) 컴포넌트에 전달되는 반면 state는 (함수 내에 선언된 변수처럼) 컴포넌트 안에서 관리됩니다.

출처: https://ko.reactjs.org/docs/faq-state.html

 

rendering이란?

사용자가 화면에 view를 보여 주는 것을 렌더링이라고 한다.

 

 re-rendering이란?

사용자 화면에 view를 다시 새롭게 보여준다는 의미이다.

 
rerendering 의 발생조건
1. State가 변경될 때 ( 자신의 상태변경 )

State 업데이트가 일어나면 리렌더링을 한다.

리액트에서 State 값이 변경되면 관련 컴포넌트들을 전부 리렌더링 한다.
리액트는 변화를 바로바로 감지하여 화면에 변경사항을 보여주기 때문이다.

 

2. 전달받은 Props가 변경될 때

Props 업데이트가 일어나면 리렌더링을 한다.
Props가 변경되는 건 부모 컴포넌트의 State도 변경이 일어난다는 의미이다.

부모 컴포넌트의 State 변경이 발생하면 Props도 업데이트 되고,
모든 하위 컴포넌트에 대해 리렌더링이 발생한다.

 

3. 부모 Component가 렌더링 될 때

부모 컴포넌트가 렌더링을 하면 그 자식 컴포넌트들은 모두 리렌더링 한다.

 

4. forceUpdate 함수가 실행될 때 ( 강제리렌더링)

 

 

https://miracleground.tistory.com/entry

https://velog.io/@pioneerraccoon
