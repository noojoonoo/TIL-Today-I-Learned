# DOM 

1. DOM(Documented Object Model)이란?
2. Interacting with the DOM
3. Get Elements By ...
4. Changing Text & HTML Content
5. DOM Nodes
6. Traversing the DOM
7. Events
8. Event Bubbling
9. Interacting with Forms
10. Creating Elements
11. Styles & Classes
12. Attributes
13. Checkboxes & Change Events
14. Keyup Event (Search Filter)
15. data-
16. DomContentLoaded Event



>  Main Resoure: [The Net Ninja - Javascript Tutorial](https://www.youtube.com/playlist?list=PL4cUxeGkcC9gfoKa5la9dsdCNpuey2s-V) 

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



#### document.getElementsByClassName('HTML 요소의 Class 명') & document.getElementsByTagName('HTML 요소의 태그명') 

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



#### document.querySelector() & document.querySelectorAll()

`document.querySelector(selector)` 

선택자와 일치하는 document 내 **첫번 째** HTML 요소를 반환한다.

`document.querySelectorAll(selector)` 

~~선택자와 일치하는 document 내 HTML 요소들을 유사 배열 객체인 ```HTML Collection``` 으로 반환한다. 반복문으로 요소들을 순회하고 싶을 시 변환을 해주어야 한다.~~

선택자와 일치하는 document 내 HTML 요소들의 `NodeList` 를 반환한다. (반복 가능한 객체이다)

**일치하는 요소가 단 *한 개* 뿐이여도 `[]` 안에  `NodeList`로 반환된다**.



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



## DOM Nodes

Node 의 종류는 정수 값으로 표시된다. 각 정수 값이 의미하는 바는 [참고](https://www.w3schools.com/jsref/prop_node_nodetype.asp)

> 3번 타입인 Text 는 HTML 문서 내의 linebreak 도 포함한다.

#### Node.nodeType

`Node.nodeType` 속성을 통해 노드 타입을 알 수 있다.

```javascript
const banner = document.querySelector('#page-banner');
console.log('#page-banner node type is:', banner.nodeType) // node type is: 1
// 1 은 Element 를 의미함
```



#### Node.nodeName

`Node.nodeName` 속성을 통해 노드의 이름을 알 수 있다.

```javascript
const banner = document.querySelector('#page-banner');
console.log('#page-banner node name is:', banner.nodeName) // node name is: DIV
```



#### Node.hasChildNodes()

`Node.hasChildNodes()` 함수를 통해 자식 노드를 갖고 있는지 알 수 있다. 

```javascript
const banner = document.querySelector('#page-banner');
console.log('#page-banner has child nodes:', banner.hasChildNodes()); 
```



#### Node.cloneNode(Boolean)

`Node.cloneNode(Boolean)` 

`True` 는 자식 노드까지 모두 복제

`False` 일 경우 해당 노드 자체만 복제



## Traversing the DOM

#### Node.parentNode & Node.parentElement

부모 노드 혹은 요소를 반환. 둘의 차이점은 다음과 같다.

```javascript
// Node
console.log('the parent Node is:', document.childNodes[0].parentNode); // Docuemnt
// Element
console.log('the parent element is', document.childNodes[0].parentElement); // Null
```

*부모 관계에 있는 것이 HTML Element 이 아닐 수도 있다.*



#### Node.childNodes & Node.children

`Node.childNodes` : `linebreak` 와 같은 노드들도 포함한 `NodeList` 가 반환된다. 

`Node.children` : *HTML Element* `HTML Collection` 으로 반환된다. 



#### Node.nextSibling & Node.nextElementSibling

현재 노드의 다음 형제 노드를 확인할 수 있다.

```javascript
const bookList = document.querySelector('#book-list');

console.log('book-list next sibling is:', bookList.nextSibling);
// text (3번 타입의 노드 lineBreak)
console.log('book-list next element sibling is:', bookList.nextElementSibling);
```



#### Node.PreviousSibling & Node.PreviousElementSibling

현재 노드의 그 전 형제 노드를 확인할 수 있다.

```javascript
const bookList = document.querySelector('#book-list');

console.log('book-list previous sibling is:', bookList.previousSibling);
// text (3번 타입의 노드 lineBreak)
console.log('book-list previous element sibling is:', bookList.previousElementSibling);
```



## Event

[이벤트의 종류들](https://www.w3schools.com/jsref/dom_obj_event.asp)

버튼을 누르거나 `<form>` 의 `<input />` 에 글을 쓰거나, 혹은 클릭 할 때 등 발생하는 이벤트들을 어떻게 캐치하고 반응하도록 할 것인가?
*이벤트를 캐치할 수 있는 event listener 생성한다. 해당 이벤트에 동작이 일어나도록 콜백 함수를 선언한다.*

```javascript
var h2 = document.querySelector('#book-list h2');

h2.addEventListener('click', function(e){
  console.log(e.target); // HTML 형식으로 반환
  console.log(e); // 이벤트의 정보가 담긴 객체 반환
});
```

예제 코드

```javascript
var btns = document.querySelectorAll('#book-list .delete'); // NodeList 반환

// 반복문을 사용하여 모든 버튼에 이벤트를 설정해준다.
// 추후에 li 새로 추가 되면 새로 생성된 li 는 이벤트 리스너가 없다.
// 때문에 효율적인 방법은 아니다.
btns.forEach(function(btn) {
	btn.addEventListener('click', function(e){
		
		const li = e.target.parentElement;

		li.parentNode.removeChild(li);
		// li.parentElement.removeChild(li); // 왜 두개 다 똑같이 작동
	});
});

const link = document.querySelector('#page-banner a');

link.addEventListener('click', function(e) {
	e.preventDefault(); // 기존 이벤트의 발생을 막는다
	console.log('navigation to', e.target.textContent, ' was prevented.');
});
```



## Event Bubbling

이벤트 버블링은 인위적으로 이를 막아주지 않는 이상 항상 일어난다.

이벤트 버블링은 특정 요소에서 이벤트가 발생했을 때, 해당 이벤트가 상위 요소들로 순차적으로 올라가며 전달된다.

예를들어 `<li>` 태그를 클릭하여 이벤트가 발생했을 시, 상위 태그인 `<ul>` 태그로 이벤트가 전달된다. 계속하여 상위 요소로 전달된다.



예제 코드

자식 요소에서 발생하는 이벤트에 동작을 일으키기 위해, 콜백 함수를 부모 요소의 이벤트 리스너에 선언 해준다.

```javascript
const list = document.querySelector('#book-list ul');

list.addEventListener('click', function(e){
  if(e.target.className == 'delete') {
    const li = e.target.parentElement;
    list.removeChild(li);
  }
});
```



## Interacting with Forms

`document.forms['id 명']` : HTML 문서 내의 모든 form 요소를 `HTML Collection` 으로 반환한다. 



예제 코드

`form` 의 `submit` 이벤트 발생을 인위적으로 막는다. 그리고 `input` 에 들어가 있던 value 들을 콘솔에 출력한다.

여기서 `input` 은 당연하게도 `form` 의 자식이다.

```javascript
const addForm = document.forms['add-book'];

addForm.addEventListener('submit', function(e){
	e.preventDefault();
  const value = e.target.querySelector('input[type="text"]').value; // 선택자 주의깊게 보기
  console.log(value);
});
```



## Creating Elements

`document.createElement(태그명)` : HTML 요소를 만들어 반환한다.

`Node.appendChild(노드)` : 자식 노드로 구성된 리스트 마지막에 주어진 노드를 추가한다.

```javascript
const list = document.querySelector('#book-list ul');

const li = document.createElement('li');
li.textContent = 'noo';

list.appendChild(li);
```



## Styles & Classes

`Node.style.color` :  특정 노드의 스타일을 접근하여 수정할 수 있다. (CSS 속성인 margin-top 과 같은 속성일 경우 marginTop 으로 접근한다)

`Node.className` : 특정 노드에 클래스 값을 가져오거나 설정할 수 있다.

`Node.classList.add('클래스명')` : 지정한 클래스명을 추가한다. (이미 해당 클래스명이 있을 시 무시한다)

`Node.classList.remove('클래스명')` : 지정한 클래스명을 제거한다.

```javascript
const li = document.createElement('li');

li.style.color = red;
li.className = 'list-element';
li.classList.add('className');
li.classList.remove('className');
```



## Attributes

`Node.getAttribute('속성명')` : 노드의 특정 속성 값을 반환한다. 해당 속성을 갖고 있지 않을 경우 `null` 을 반환한다.

`Node.setAttribute('속성명', 속성 값')` : 노드의 속성을 설정할 수 있다.

`Node.hasAttribute('속성명')` : 노드가 해당 속성을 갖고 있는지 판별할 수 있다.

`Node.removeAttribute('속성명')` : 노드에서 해당 속성을 삭제한다.



## Checkboxes & Change Events

`<input type='checkbox' />` 요소는 `checked` 라는 `state` 를 갖는다.

```javascript
const list = document.querySelector('#book-list ul');

const hideBox = document.querySelector('#hide'); // <input type="checkbox" id="hide"/>
hideBox.addEventListener('change', function(e){
  if(hideBox.checked) {
    list.style.display = 'none';
  } else {
    list.style.display = 'initial';
  }
});
```

>  'change' 라는 이벤트는 언제나 발생하는 이벤트가 아니다. [참고](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/change_event)



## Keyup Event (Search Filter)

`HTMLElement.firstElementChild` :  HTML 요소의 가장 첫번 째 자식 요소를 반환한다.

`String.indexOf('string')` : 문자열 내에 인자로 받게된 문자열이 있는지 확인한다. 있을 경우 해당 문자열의 위치를 반환한다. 없을 경우 `-1` 을 반환한다.

```javascript
// 서치 바에 텍스트를 입력한다.
// 입력되는 텍스트를 매번 받아 리스트의 책들 제목과 비교한다.
// 제목을 비교할 때는 검색어와 책 제목을 둘 다 소문자로 바꾼다.
// 제목이 같으면 보이고 아니면 숨긴다.

const searchBar = document.form['search-books'].querySelector('input');
searchBar.addEventListener('keyup', function(e){
  const term = e.target.value.toLowerCase();
  const books = list.getElementsByTagName('li');
  Array.from(books).forEach(function(book){
    const title = book.firstChildElement.textContent;
    
    if(title.toLowerCase().indexOf(term) != -1) {
      book.style.display = 'block';
    } else {
      book.style.display = 'none';
    }
  });
});
```



## data-

HTML5에서는 HTML 요소에 `data-정보이름` 속성을 이용하여 정보를 저장할 수 있다.

```html
<div data-age="23" id="noo">
   junWooKim
</div>
```

`javascript` 에서 `data-` 값 참조하기.

```javascript
var mySelf = document.getElementById('noo');
mySelf.data.age // 23
```



## DOMContentLoaded Event

HTML DOM 을 참고하거나 조작하는 스크립트가  `<head>` 내에서, 혹은 HTML 문서의 상단에서 불러와질 경우 문제가 발생할 수 있다. HTML DOM 이 모두 불러와지기 전에 스크립트가 실행되기 때문이다. 

해당 경우에는 `DomContentLoaded` 이벤트를 핸들링하며 해결한다.

 `DomContentLoaded` 는 최초 HTML 문서가 완전히 로드 및 파싱되었을 때 발생한다. 스타일시트나 이미지 및 서브프레임 로드가 끝나기를 기다리지 않습니다. (MDN)

> `load` 이벤트는 리소스와 그것에 의존하는 리소스들이 모두 로딩 완료될 경우 발생한다.

```javascript
document.addEventListener('DOMContentLoaded', function(e){
  // DOM 과 관련된 스크립트 삽입
})
```

