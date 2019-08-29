#DOM 

1. DOM(Documented Object Model)이란?
2. Interacting with the DOM
3. Get Elements By ...
4. Changing Text & HTML Content



## DOM이란?

HTML 문서는 트리 구조로 되어있다. 트리 안의 HTML 요소들을 순회하며 원하는 동작을 할 수 있다.



## Interacting with the DOM

1. HTML 요소를 수정하거나 삭제할 수 있다.

2. CSS 스타일을 수정하거나 추가할 수 있다.

3. HTML 요소의 속성(Attribute)를 읽고 수정할 수 있다.

4. 새로운 HTML 요소를 생성하여 기존 DOM 에 삽입할 수 있다.

5. 이벤트 리스너를 장착할 수 있다.



## Get Elements By...

#### document.getElementById('HTML 요소의 ID 값')

document 객체가 갖고 있는 함수이며 원하는 HTML 요소(document 의 자식)를 ID 값으로 갖고온다.

갖고 온 객체를 변수에 할당할 수 있다.

```javascript
var banner = document.getElementById('page-banner');
var bookList = document.getElementById('book-list');
```



####document.getElementsByClassName('HTML 요소의 Class 명') & document.getElementsByTagName('HTML 요소의 태그명') 

반환하는 값이 배열(Array)처럼 보일 수 있지만 유사 배열 객체인 ```HTML Collection```이다.

```javascript
var titles = getElementByClassName('titles');
console.log(Array.isArray(titles); // false
```

 ```forEach``` 와 같은 배열이 갖고 있는 고차 함수를 사용하려면 배열로 변환 시켜줘야 한다.

```javascript
console.log(Array.isArray(Array.from(titles))); // true
```

> **Array.from()** 메서드는 유사 배열 객체(array-like object)나반복 가능한 객체(iterable object)를 얕게 복사해 새로운Array 객체를 만듭니다. (MDN)
>
> **Array.isArray()** 메서드는 인자가 Array인지 판별한다. (MDN)



####document.querySelector() & document.querySelectorAll()

`document.querySelector(selector)` 

선택자와 일치하는 document 내 **첫번 째** HTML 요소를 반환한다.

`document.querySelectorAll(selector)` 

~~선택자와 일치하는 document 내 HTML 요소들을 유사 배열 객체인 ```HTML Collection``` 으로 반환한다. 반복문으로 요소들을 순회하고 싶을 시 변환을 해주어야 한다.~~

선택자와 일치하는 document 내 HTML 요소들의 `NodeList` 를 반환한다. (반복 가능한 객체이다)

*일치하는 요소가 단 **한 개** 뿐이여도 `[]` 안에  `NodeList`로 반환된다*.



## Changing Text & HTML Content

#### Changing Text

```javascript
// 기존 HTML 요소의 컨텐트에 내용 추가(append) 하기
var books = document.querySelectorAll('#book-list li .name');

books.forEach(function(book){
  book.textContent += '';
});

// 기존 HTML 요소를 바꾸기
```

#### Changing HTML Content

```javascript
const bookList = document.querySelector('#book-list');

bookList.innerHTML = '<h2>Books and more books...</h2>';
bookList.innerHTML += '<p>This is how you add HTML</p>';
```

위 코드를 실행 시 `#bookList`는 다음과 같아진다.

```HTML
<h2>Books and more books...</h2>
<p>This is how you add HTML</p>
```









> Main Resoure: [The Net Ninja - Javascript Tutorial](https://www.youtube.com/playlist?list=PL4cUxeGkcC9gfoKa5la9dsdCNpuey2s-V) 