# HTML
- Hyper Text Markup Language, 웹페이지를 만들기 위한 언어로 웹브라우저 위에서 동작하는 언어다.
- Hyper Text : 문서와 문서가 링크로 연결되어 있다.
- Markup : 태그로 이루어져 있다.

## 태그
- tag 
- 태그란 정보를 정의 하는 형식

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