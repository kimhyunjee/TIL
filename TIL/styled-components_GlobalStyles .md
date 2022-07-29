## 컴포넌트 레벨 스타일링

React와 Styled Components로 웹 개발을 하다보면 대부분의 경우 컴포넌트 레벨에서 스타일을 하게 됩니다. React가 컴포넌트 기반 자바스크립트 라이브러리라는 것을 감안해보면 너무나 자연스러운 현상일 것입니다.

Styled Components는 이렇게 컴포넌트 단위로 적용한 스타일을 외부와 완전히 격리시켜 해당 컴포넌트 내부에서만 유효하도록 해줍니다.

### 예시

```jsx
// BlogPost.js

import styled from "styled-components";

function BlogPost({ title, children }) {
  return (
    <Wrapper>
      <Title>{title}</Title>
      <Content>{children}</Content>
    </Wrapper>);
}

const Title = styled.h2`
  font-family: "Helvetica", "Arial", sans-serif;
  line-height: 1.5;
  font-size: 1.5rem;
  margin: 0;
  margin-bottom: 8px;
`;

const Content = styled.p`
  margin: 0;
  font-family: "Helvetica", "Arial", sans-serif;
  line-height: 1.5;
  font-size: 1rem;
`;

const Wrapper = styled.article`
  border: 1px solid;
  border-radius: 8px;
  padding: 16px;
  margin: 16px auto;
  max-width: 400px;
`;

export default BlogPost;
```

## 애플리케이션 레벨 스타일링

하지만 규모가 있는 웹 애플리케이션을 개발할 때는 개별 컴포넌트가 아닌 모든 컴포넌트에 동일한 스타일을 적용하는 편이 유리한 경우가 있습니다. 대표적인 예로 `font-family` CSS 속성을 들 수 있는데, 여러 컴포넌트에 걸쳐 통일된 글꼴을 사용하고 싶은 경우가 대부분이기 때문입니다. CSS에서 글꼴 관련 속성은 부모 엘리먼트에서 자식 엘리먼트로 상속(inherit)되기 때문에 `<body>` 엘리먼트를 대상으로 정의해주면 좋을 것 같습니다.

또 다른 예로, 브라우저에 상관없이 일괄적인 스타일을 적용하기 위해서 사용하는 CSS 정규화(normalize)나 CSS 초기화(reset)를 들 수 있습니다. 이러 종류의 전역 CSS 스타일도 애플리케이션 레벨에서 일괄적으로 적용해주는 것이 이상적일 것입니다.

애플리케이션 레벨 스타일을 지원하기 위해서 Styled Components는 `createGlobalStyle()`라는 함수를 제공하고 있습니다.

### 예시

```jsx
// GlobalStyle.jsx

import { createGlobalStyle } from "styled-components";

const GlobalStyle = createGlobalStyle`
  *, *::before, *::after {
    box-sizing: border-box;
  }

  body {
    font-family: "Helvetica", "Arial", sans-serif;
    line-height: 1.5;
  }
`;

export default GlobalStyle;
```

이렇게 `createGlobalStyle()`
 함수로 생성한 전역 스타일 컴포넌트를 애플리케이션의 최상위 컴포넌트에 추가해주면 하위 모든 컴포넌트에 해당 스타일이 일괄 적용됩니다.

### 예시

```jsx
// App.jsx

import GlobalStyle from "./GlobalStyle";
import BlogPost from "./BlogPost";

function App() {
  return (
    <>
      <GlobalStyle />
      <BlogPost title="Styled Components 전역 스타일링">
        이번 포스팅에서는 Styled Components로 전역 스타일을 정의하는 방법에
        대해서 알아보겠습니다.
      </BlogPost>
    </>
  );
}

export default App;
```

## 엘리먼트 기본 스타일링

빈번하게 사용되는 엘리먼트에 대해서는 애플리케이션 레벨에서 기본 스타일을 정의해주면 편리한 경우가 있습니다.

### 예시) `h2>`와 `<p>`엘리먼트에 대한 전역 스타일을 추가

```jsx
// GlobalStyle.jsx

import { createGlobalStyle } from "styled-components";

const GlobalStyle = createGlobalStyle`
  *, *::before, *::after {
    box-sizing: border-box;
  }

  body {
    font-family: "Helvetica", "Arial", sans-serif;
    line-height: 1.5;
  }

  h2, p {
    margin: 0;
  }

  h2 {
    font-size: 1.5rem;
  }

  p {
    font-size: 1rem;
  }
`;

export default GlobalStyle;
```

이렇게 해주면 컴포넌트 레벨에서 스타일해줄 부분이 줄어들 게 되어, 여러 컴포넌트에 동일한 스타일을 반복해서 정의할 일이 적어집니다. 뿐만 아니라 전역 스타일을 변경없이 그대로 사용할 경우에는 아예 해당 엘리먼트에 대한 스타일을 생략할 수도 있습니다.

### 예시
```jsx
// BlogPost.jsx

import styled from "styled-components";

function BlogPost({ title, children }) {
  return (
    <Wrapper>
      <Title>{title}</Title>
      <p>{children}</p>
    </Wrapper>
  );
}

const Title = styled.h2`
  margin-bottom: 8px;
`;

const Wrapper = styled.article`
  border: 1px solid;
  border-radius: 8px;
  padding: 16px;
  margin: 16px auto;
  max-width: 400px;
`;

export default BlogPost;
```

출처: https://www.daleseo.com/styled-components-global-style/
