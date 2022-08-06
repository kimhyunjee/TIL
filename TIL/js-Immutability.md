# Javascript 불변성

자바스크립트에서 불변성이란 객체가 생성된 이후 그 상태를 변경할 수 없는 것을 의미합니다.여기서 상태를 변경할 수 있는 것과 값을 재할당하는 것은 다르다는 것을 알아야합니다.

```
let a = 10;
let b = a;
a = 20;
console.log(a,b); //20 10
```

위의 코드는 a에 10을 할당하고 b를 a가 가리키는 주소를 가리킵니다.이때 a의 값을 20으로 변경시켜줍니다.

만약 값을 직접 변경하는 것이라면 a와 b가 둘다 20을 출력해야합니다.

하지만 자바스크립트에서

```
Number
```

값은 불변성을 유지하기 때문에 새롭게 20이라는 값을 가지는 주소를 a에 할당하게 되기 때문에 위와 같은 결과가 나오게 됩니다.

![https://velog.velcdn.com/images%2Fco_mong%2Fpost%2Ff2912982-427e-4b48-b365-5d4c31188ed0%2F%EC%A0%9C%EB%AA%A9%20%EC%97%86%EC%9D%8C.png](https://velog.velcdn.com/images%2Fco_mong%2Fpost%2Ff2912982-427e-4b48-b365-5d4c31188ed0%2F%EC%A0%9C%EB%AA%A9%20%EC%97%86%EC%9D%8C.png)

## 1. immutable vs mutable

자바스크립트에서는 불변성을 유지하는 값들과 그렇지 않은 값들이 나누어져 있다.

`Boolean`, `Number`, `String`, `null`, `undefined`, `Symbol`과 같은 타입들은 불변성을 유지하는 타입들이고 `Object`타입들은 변경가능한 값들입니다.

이 말은 객체는 객체 내부의 값을 변경하면 객체를 참조하고 있는 다른 값들도 다 같이 변경된다는 의미입니다.

```
var coke = {
    name: 'coca',
    price: 2980,
}
var new_coke = coke;
coke.name = 'pepsi';
console.log(coke.name,new_coke.name);//'pepsi' 'pepsi'
```

위와 같이 coke의 name값을 변경했는데 new_coke의 name까지 한번에 변경된 것을 볼 수 있습니다.

## 2. 객체의 불변성 지키기

### 2.1 스프레드 문법 사용

```
var coke = {
    name: 'coca',
    price: 2980,
}
var new_coke = {...coke};
coke.name = 'pepsi';
console.log(coke.name,new_coke.name);//'pepsi' 'coca'
```

스프레드 문법을 사용하여 객체를 복사해야지 객체가 불변성을 유지할 수 있습니다.하지만 스프레드 문법은 1레벨 깊이에서만 유효하게 동작하기 때문에 객체 내부의 객체의 불변성까지는 유지할수 없습니다.

```
var coke = {
    name: 'coca',
    fake: {
        name: 'pepsi',
    }
}
var new_coke = {...coke};
coke.fake.name = 'coca zero';
console.log(coke.fake.name,new_coke.fake.name);
//'coca zero' 'coca zero'
```

만약 레벨2 객체까지 불변성을 유지해주려면 아래와 같이 별도의 변수에 값을 재할당하고 넣어주는 번거러운 과정을 거쳐야 합니다.

```
const coke = {
    name: 'coca',
    fake: {
        name: 'pepsi',
    }
}
const new_fake = {...coke.fake};
const new_coke = {...coke};
new_coke.fake = new_fake;
coke.fake.name = 'coca zero';
console.log(coke.fake.name,new_coke.fake.name);
//'coca zero' 'pepsi'
```

### 2.2 immer

불변성을 유지하기 위해 복잡한 과정없이 `immer`라이브러리를 사용하면 간단하게 불변성을 유지할 수 있습니다.

- 설치`npm i immer`
- import`import produce from 'immer'`
- 사용방법

```
import produce from 'immer';
const coke = {
    name: 'coca',
    fake: {
        name: 'pepsi',
    }
}

const new_coke = produce(coke, (draft) => {
    draft.name = 'pepsi';
    draft.fake.name = 'coca';
});
console.log(coke.name,coke.fake.name);
console.log(new_coke.name,new_coke.fake.name);

//"coca" "pepsi"
//"pepsi" "coca"
```

**결론 : immer 쓰자**



**참고자료**

[https://poiemaweb.com/js-immutability](https://poiemaweb.com/js-immutability)

[https://junwoo45.github.io/2019-11-04-memory_model/](https://junwoo45.github.io/2019-11-04-memory_model/)

https://github.com/immerjs/immer

[https://velog.io/@co_mong/JS-불변성Immutability](https://velog.io/@co_mong/JS-%EB%B6%88%EB%B3%80%EC%84%B1Immutability)

---

## Immer

Immer 를 사용하면 우리가 상태를 업데이트 할 때, 불변성을 신경쓰지 않으면서 업데이트를 해주면 Immer 가 불변성 관리를 대신 해줍니다.

****Immer 사용법****

우선 코드의 상단에서 immer 를 불러와주어야 합니다. 보통 `produce` 라는 이름으로 불러옵니다.

```jsx
import produce from 'immer';

```

그리고 `produce` 함수를 사용 할 때에는 첫번째 파라미터에는 수정하고 싶은 상태, 두번째 파라미터에는 어떻게 업데이트하고 싶을지 정의하는 함수를 넣어줍니다.

두번째 파라미터에 넣는 함수에서는 불변성에 대해서 신경쓰지 않고 그냥 업데이트 해주면 다 알아서 해줍니다.

```jsx
const state = {
  number: 1,
  dontChangeMe: 2
};

const nextState = produce(state, draft => {
  draft.number += 1;
});

console.log(nextState);
// { number: 2, dontChangeMe: 2 }
```

****리듀서에서 Immer 사용하기****

Immer를 사용해서 간단해지는 업데이트가 있고, 오히려 코드가 길어지는 업데이트들이 있습니다.

예를들어서 우리가 만들었던 프로젝트의 상태의 경우 `users` 배열이 객체의 깊은곳에 위치하지 않기 때문에 새 항목을 추가하거나 제거 할 때는 Immer 를 사용하는 것 보다 `concat` 과 `filter` 를 사용하는것이 더 코드가 짧고 편합니다.

참고사이트

[https://react.vlpt.us/basic/23-immer.html](https://react.vlpt.us/basic/23-immer.html)

여기서 말하는 프로젝트 상태는 여기 페이지에서 볼 수 있다.


Immer 은 분명히 정말 편한 라이브러리인것은 사실입니다. 하지만, 확실히 알아둘 점은, 성능적으로는 Immer 를 사용하지 않은 코드가 조금 더 빠르다는 점 입니다.

Immer 라이브러리는 확실히 편하기 때문에, 데이터의 구조가 복잡해져서 불변성을 유지하면서 업데이트하려면 코드가 복잡해지는 상황이 온다면, 이를 사용하는 것을 권장드립니다.

다만, 무조건 사용을 하진 마시고, 가능하면 데이터의 구조가 복잡해지게 되는 것을 방지하세요. 그리고 어쩔 수 없을 때 Immer 를 사용하는것이 좋습니다. Immer 를 사용한다고 해도, 필요한곳에만 쓰고, 간단히 처리 될 수 있는 곳에서는 그냥 일반 JavaScript 로 구현하시길 바랍니다.







