# HTML
- Hyper Text Markup Language, 웹페이지를 만들기 위한 언어로 웹브라우저 위에서 동작하는 언어다.
- Hyper Text : 문서와 문서가 링크로 연결되어 있다.
- Markup : 태그로 이루어져 있다.

## 태그
- tag 
- 태그란 정보를 정의 하는 형식

## 태그의 형식
- <태그명 속성명1="속성값1" 속성명2="속성값2"> 컨텐츠 </태그명>
- 태그는 컨텐츠를 감싸서 그 정보의 성격과 의미를 정의 한다.
- <a href="http://opentutorials.org">생활코딩</a>
    - '생활코딩'이라는 컨텐츠가 링크라는 성격을 정의한다.


##  HTML table tag
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <table border="1">
        <tr>
            <th>Table Data</th>
            <th>Table Data</th>
        </tr>

        <tr>
            <td>Table Data</td>
            <td rowspan="2">Table Data</td>
            <td>Table Data</td>
        </tr>
        
        <tr>
            <td>Table Data</td>
            <td>Table Data</td>
        </tr>
    </table>
</body>
</html>
```

reference - 생활코딩