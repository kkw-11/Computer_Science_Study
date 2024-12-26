# form 태그 사용 방법과 동작 방식 활용

## form 태그 기본 형식
```HTML
    <form action = "/login" method="POST">
        <label for="username">Username:</label>
        <input type = "text" id = "username" name = "username" requried>
        <label for="password">Passwrod:</label>
        <input type="password" id="password" name="password" required>

        <button type="submit">Submit </button>
    </form>
```


## form 태그 서브밋 기본 동작 방식

## form 태그 응용 예시


## form 태그 활용 방식
1. HTML의 form 태그 만을 이용해서 서버로 데이터 전송

2. 서버와의 통신 없이 클라이언트에서만 form 태그를 이용해서 데이터 조작 with Javascript

3. 비동기 통신으로 페이지 리로드 없이 사용자 경험을 증가시키면서, form 태그 활용하기 with Javascript AJAX