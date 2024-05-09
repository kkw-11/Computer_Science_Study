# Java
자바는 운영체제에 독립적인 객체지향 프로그래밍 언어
자바로 작성된 프로그램은 운영체제의 종류에 관계없이 실행이 가능하기 때문에, 다양한 기종의 컴퓨터와 운영체제가 공전하는 인터넷환경에 적합한 언어로써 인터넷의 발전과 함께 성장했다.
자바는 많은 양의 클래스 라이브러리(Java API)를 통해 프로그래밍에 필요한 요소들을 기본적으로 제공한다.

1995년에 썬 마이크로시스템즈에서 개발한 언어 현재 썬 마이크로시스템즈는 오라클에 인수가 된 상태
자바의 특징
쉬운 언어이다.
C와 C++언어의 문법을 기본으로 차용하여 개발된 언어
C와 C++ 이 가진 어려운 문법인 포인터와 다중 상속 제거
C와 C++에 비해 쉬운 언어이다.
플랫폼에 독립적이다.
자바는 JVM() 만 있으면 윈도우, 리눅스, 맥등 어떤 플랫폼에서도 실행이 가능
객체지향 언어이다.
메모리 관리를 자동으로 해준다.



# Java로 프로그램 개발 하기
1. 소스 작성
    * 메모장 등의 text editor를 통해 자바 소스를 작성한다. 나중에 이클립스나 인텔리제이 같은 IDE는 통합 개발환경으로 text editor가 내장되어 있다.
2. 작성한 소스 컴파일
    * 자바 소스 코드 컴파일 명령어 -  javac [파일명]
    * 위 명령어를 실행하면 자바컴파일러(javac.exe)를 사용해서 소스파일(HelloWorld.java)로 부터 클래스 파일(HelloWorld.class)을 생성한다. \
    * IDE를 사용하면 저장시에 자동으로 컴파일이 된다.
3. 실행
    * java [클래스파일명] or java.exe [클래스파일명]
    * 위 명령어를 실행하면 java.exe가 main 메서드를 호출하여 Java 애플리케이션을 실행한다.






# 실습 
    * .java라는 확장자로 파일을 하나 생성한 후 자바 소스를 작성한다. 아래는 화면에 HelloWorld를 출력하는 자바 소스코드이다.
    
    ```
    public class HelloWorld{
        public static void main(String args[]){
            System.out.println("Hello World");
        }
    }

    ```

 ![image](https://user-images.githubusercontent.com/76929823/153330545-491c134d-42db-4af4-baed-32eab5f703b2.png)

![image](https://user-images.githubusercontent.com/76929823/153330611-7260bb15-2b82-4f9b-ab2e-1af0ec193670.png)

![image](https://user-images.githubusercontent.com/76929823/153330640-a13925ce-fbdf-4b32-98a4-cbd0b11b59d4.png)

    


출처: 프로그래머스 Java 강의, Java의 정석
