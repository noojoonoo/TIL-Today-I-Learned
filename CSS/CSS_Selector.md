# CSS Selector

### Class & id

| Selector        | Example                                                 | Example description                                          |
| :-------------- | ------------------------------------------------------- | ------------------------------------------------------------ |
| .class          | .intro                                                  | `class="intro"` 를 가진 모든 요소 선택                       |
| .class1.class2  | `<div class="name1 name2">...</div>`                    | `name1` `name2` 클래스명을 *모두* 가진 요소 선택             |
| .class1 .class2 | `<div class="name1"><div class="name2">...</div></div>` | `name1` 클래스명을 가진 요소 내에  `name2` 요소들을 *모두* 선택 (*자식 아닌 후손*) |
| `#id`           | `#firstname`                                            | `id=firstname` 인 요소를 선택                                |



### Element

| Selector        | Example | Example description                                         |
| :-------------- | ------- | ----------------------------------------------------------- |
| element         | `<p>`   | 문서내 `<p>` 요소들 모두 선택                               |
| element,element | div, p  | 모든 `<div>`  와 모든 `<p>` 선택                            |
| element element | div p   | `<div>` 내에 있는 `<p>` 선택                                |
| element>element | div > p | 부모 요소가 `<div>` 인  `<p>` 요소 모두 선택                |
| element+element | div + p | `<div>` *바로 다음에* 오는 `<p>` 요소를 선택 (next Sibling) |
| element~element | p ~ ul  | `<p>` 이후에 오는 모든 `ul` 들을 선택                       |



### Attribute

| Selector | Example | Example description |
| :------- | ------- | ------------------- |
|          |         |                     |
|          |         |                     |
|          |         |                     |
|          |         |                     |
|          |         |                     |
|          |         |                     |



