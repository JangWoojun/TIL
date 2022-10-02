> 작성일 2022/10/02 ~ 2022/10/02

<br>

# Kotiln 기본 문법

## 기본 형태

~~~
fun main(){

}
~~~

위에 형태가 C를 사용하는 기본 형태다.

차근 차근 뜯어보자

여기서 fun main(){} 이 부분을 메인 함수라고 부르며 메인 함수는 코드에 시작점을 알려주는 부분이다 {}안 즉 함수 바디안에 코드를 적어 코드를 실행한다

참고로 자바와 같은 객체지향 언어는 프로그램을 실행할 때 최소한 한 개의 Class와 메인 함수가 있어야 되지만 그냥 실행되는 까닭은 코틀린 코드가 JVM로 실행될 때 자바 클래스가 자동으로 만들어지기 때문이다

## 출력 

코틀린에서 출력할 때 사용하는 내장 함수는 크게 두 가지가 있다

print와 println이다 둘 다 사용 법은 같다 ()안에 출력할 것을 적으면 출력이 된다 참고로 문자열은 ""로 묶어줘야 한다 예제와 함께 두 함수에 차이를 보면

코드
~~~
fun main(){
    print("Hello World")
}
~~~

출력
~~~
Hello World
~~~

코드
~~~
fun main(){
    println("Hello World")
}
~~~

출력
~~~
Hello World
~~~

한 문장만 출력했을 때는 두 함수 모두 동일해 보인다 하지만 두 문장을 출력하면 차이를 알 수 있다

코드
~~~
fun main(){
    print("Hello World")
    print("Hello World")
}
~~~

출력
~~~
Hello WorldHello World
~~~

코드
~~~
fun main(){
    println("Hello World")
    println("Hello World")
}
~~~

출력
~~~
Hello World
Hello World
~~~

이와 같이 print와 println는 출력 후 줄 바꿈을 하느냐 안 하느냐로 갈린다

## val VS var

val 과 var은 코틀린에서 변수를 선언하는 법이다
사용법은 동일하다 val나 var뒤에 변수명을 적어 선언할 수 있다

예제와 함께 차이를 보면

코드
~~~
fun main(){
    val name = "Kotlin"
    println("Hi "+name)
}
~~~

출력
~~~
Hi Kotlin
~~~

코드
~~~
fun main(){
    var name = "Kotlin"
    println("Hi "+name)
}
~~~

출력
~~~
Hi Kotlin
~~~

이것만 봤을 때 val과 var는 동일해 보인다 하지만 변경하려고 할 때 차이가 들어난다

코드
~~~
fun main(){
    var name = "Kotlin"
    name = "Java"
    println("Hi "+name)
}
~~~

출력
~~~
Hi Java
~~~

코드
~~~
fun main(){
    val name = "Kotlin"
    name = "Java"
    println("Hi "+name)
}
~~~

출력
~~~
Error
~~~

위와 같이 var는 값을 변경할 수 있으나 val는 변경하려고 하면 오류가 뜨는 것을 볼 수 있다

