> 작성일 2022/10/02 ~ 2022/10/03

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

## 주석

코드
~~~
fun main(){
    // 한 줄 주석

    /*여러 줄
    주석*/
}
~~~

코틀린에서 한 줄 주석은 // 두개를 사용하여 적을 수 있고 여러 줄은 /**/로 사용하면 된다

주석이란 코멘트로 자신의 코드에 대해 설명을 해주는 것 컴퓨터에는 아무런 도움이 되지 않는 것이므로 컴파일러는 이 주석을 완전히 무시해 버린다 


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

## 입력

코틀린에서 입력을 받을 땐 readln 함수와 자바에서 가져온 next 함수 이렇게 크게 두가지 방법이 있다 입력을 Kotlin으로 했을 시 두 가지 방법 예제를 보면

코드
~~~
fun main(){
    val name = readln()

    println("나는 "+name+"+을 좋아해")
}
~~~

출력
~~~
나는 Kotlin을 좋아해
~~~

위 방법은 개행 문자를 기준으로 받는다 또한 어떤 것을 받던 String?형으로 받아 형 변환을 해줘야 하는 단점이 있다 그러니 형 변환시에는 !!로 null이 아님을 써줘야 한다


코드

~~~
fun main(){
    val sc = Scanner(System.`in`)
    val name = sc.next()
    println("나는 "+name+"을 좋아해")
}
~~~

출력
~~~
나는 Kotlin을 좋아해
~~~

위 방법은 코틀린이 자바와 호환된다는 점을 이용하여 Scanner 객체를 만들어 입력받은 것이다 next() 또한 String 타입 형태로 값을 받고

next와 비슷한 함수로는 readln()처럼 개행 기준으로 입력을 받는 nextLine()과 next뒤에 자료형을 적어 해당 형태로 받는 ex)Int형으로 받는 nextInt() 등이 존재한다

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

