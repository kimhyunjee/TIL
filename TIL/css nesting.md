****CSS Nesting Module -**** 이 모듈은 내부 규칙의 선택자가 외부 규칙과 일치하는 요소를 참조할 수 있도록 다른 스타일 규칙 내에 스타일 규칙을 중첩하는 지원을 설명합니다.

이 기능을 사용하면 관련 스타일을 CSS 문서 내의 단일 구조로 집계하여 가독성과 유지 관리성을 향상시킬 수 있습니다.

nav안에 있는 ul, li, a를 [CSS]에서는 이렇게 썼다. nav를 세 번 쓰고 후손셀렉터를 일일이 써 주었다.

```jsx
nav ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
nav li {
  display: inline-block;
}
nav a {
  display: block;
  padding: 6px 12px;
  text-decoration: none;
}
```

SCSS or Sass는 네스팅 방식에 따라서부모 셀렉터를 한번 써주고 그 안에 {} 중괄호를 넣어서구조를 (부모 자식관계) 구분시켜 써주면 된다.

[SCSS]

```jsx
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li { display: inline-block; }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}[SASS]nav
  ul
    margin: 0
    padding: 0
    list-style: none

  li
    display: inline-block

  a
    display: block
    padding: 6px 12px
    text-decoration: none
```

Ampersand(상위 선택자 참조) : &부모 요소를 참조하는 셀렉터만약 부모 요소의 참조가 필요한 경우 &을 이용해서 그 부모의 하위 { }에 써주면 된다.:hover ::before, ::after 등이 그 예이다.css에서는 요소 옆에 :hover를 써주면 되지만SCSS에선 &를 사용한다. 이후에는 동일하다.

[SCSS]

```jsx
@mixin button-base() {
  @include typography(button);
  @include ripple-surface;
  @include ripple-radius-bounded;

  display: inline-flex;
  position: relative;
  height: $button-height;
  border: none;
  vertical-align: middle;

  &:hover { cursor: pointer; }

  &:disabled {
    color: $mdc-button-disabled-ink-color;
    cursor: default;
    pointer-events: none;
  }
}
```

출처:

[https://ljtaek2.tistory.com/101](https://ljtaek2.tistory.com/101)

[https://www.w3.org/TR/css-nesting-1/#intro](https://www.w3.org/TR/css-nesting-1/#intro)

[https://bokartstudio.tistory.com/47](https://bokartstudio.tistory.com/47)
