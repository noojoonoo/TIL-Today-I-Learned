# CSS Variables

`CSS Variable` 은 특정 값을 재사용할 수 있도록 선언할 수 있는 변수이다.

변수명 앞에 `--` 을 붙여 `--navbar-color: black;` 의 형태로 변수를 선언하며 대소문자 구분에 유의해야한다.

`var(변수명)` 함수를 통해 변수에 접근할 수 있다.

```css
/* 전역에 변수를 선언하고 싶다면 root 나 body 에 선언할 것을 권장. */

:root {
  --main--color: black;
}
body {
  --main-container-padding: 20px;
}

.container {
  padding: var(--main-container-padding)
}
```

`var(변수명, fallback 값)` 일 경우 해당 변수가 정의되지 않았을 때 사용할 값을 정할 수 있다. *특정 선택자 내에서 변수가 정의될 경우, 해당 선택자가 적용되는 요소와 그 하위 요소들이 접근할 수 있다.*  (Much like Cascading)

