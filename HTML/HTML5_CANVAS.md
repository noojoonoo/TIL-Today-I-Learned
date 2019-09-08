## `<canvas>`

`width` 와 `height` 두 속성만 있다.

```javascript
var canvas = document.querySelector('canvas');
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;
```



## ` getContext()`

캔버스에 무언가를 그리기 위해서는, 어떤 스크립트가 *렌더링 컨텍스트*에 접근해야 한다.

캔버스 요소는 `getContext(contextType)` 메서드를 이용하여 *렌더링 컨텍스트* 에 접근한다.

**contextType**

- `2d`
- `webgl`
- `webgl2`
- `bitmaprenderer`

```javascript
var canvas = document.querySelector('canvas');
canvas.getContext()
```



## Rectangle

`fillRect(x, y, width, height)` : 색칠된 직사각형

`strokeRect(x, y , width, height)` : 직사각형 윤곽선을 그린다.

`clearRect(x, y, width, height)` : 특정 부분을 비우는 직사각형이다.

```javascript

```



## Path

`Path` 는 점들의 집합이다.

선을 그리는 과정은 

1. 선을 연다. `beginPath()`
2. 선을 그린다. `stroke()`
3. 선을 닫는다. `closePath()`

`beginPath()` :  `Path` 를 만들기 위한 첫번 째 단계. 도형을 처음으로 여는 과정.

`closePath()` : 도형을 닫는다. 이미 닫혀 있다면 아무런 동작도 하지 않는다.

`stroke()` : 윤곽선을 이용하여 도형을 그린다.

`fill()` : 경로의 내부를 채워서 내부가 채워진 도형을 그린다. **호출 시에 열린 도형은 자동으로 닫힌다.(`stroke` 와의 차별되는 지점)**



## `moveTo()`

`moveTo()` : 어떤 것도 그리지 않지만 펜만 이동한다. `beginPath()` 메소드 호출 후, *특정 시작점을 설정하기 위해* `moveTo()` 를 사용하는 것이 좋다.



##`lineTo()` 

`lineTo()` : 현재의 드로잉 위치에서 x와 y로 지정된 위치까지 선을 그린다.



## `Arc()`

#### `arc(x, y, radius, startAngle, endAngle, anticlockwise)`

`x`, `y` : 호의 원점

`radius` : 호의 반지름

`startAngle` , `endAngle` : 라디안 값을 사용한다. 각도를 라디안으로 바꾸려면 `radians = (Math.PI / 180) * degrees`

`anticlockwise` 는 `boolean` 값이다. `true` 일 경우 반 시계 방향으로 호를 그린다.



#### `arcTo(x1, y1, x2, y2, radius)`



## `requestAnimationFrame()`

