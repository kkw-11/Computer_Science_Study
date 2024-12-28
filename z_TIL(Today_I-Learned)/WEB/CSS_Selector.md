## CSS 자손 선택자.
- 특정 태그에 속한 모든 태그를 선택하는 방법.
- 문법 : 태그와 태그를 공백으로 구분하여 선택
```CSS
div h1 {
    background-color : gray;
}
```
- div 태그 내에 h1 자손 모두 배경화면 gray 바꾸기


## CSS 자식 선택자
- 특정 태그에 바로 하위에 속한 자식을 선택하는 방법
- 문법 : 태그와 태그를 '>'로 하용하여 선택
```CSS
div > h1 {
    background-color : gray
}
```
- div 태그 바로 하위에 있는 h1 태그의 배경을