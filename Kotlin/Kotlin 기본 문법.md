> 작성일 2022/10/02 ~ 2022/10/03

<br>

# Kotiln 기본 문법

## 기본 형태

~~~
fun main(){

}
~~~

위에 형태가 Kotlin을 사용하는 기본 형태다.

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

# 입출력

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

next와 비슷한 함수로는 readln()처럼 개행 기준으로 입력을 받는 nextLine()과 next뒤에 자료형을 적어 해당 형태로 받는 

ex)Int형으로 받는 nextInt(), Byte형으로 받는 nexyByte(), Double형으로 받는 nextDouble() 등등이 존재한다

## 문자열 템플릿

코틀린에는 문자열 안에서 외부에 있는 변수를 가져올 수 있는 방법인 문자열 템플릿이 있다 + 를 이용하여 더 하는 방식이 아닌

~~~
fun main(){

    val name = "Kotlin"

    println("내 이름은 $name 이다")
}
~~~

$ 기호 뒤에 변수명을 사용하여 한 문자열 내에서 처리하는 방식이다

그런데 만약 Kotlin뒤에 이다를 띄어쓰지 않고 붙여서 출력하고 싶다면

~~~
fun main(){

    val name = "Kotlin"

    println("내 이름은 ${name}이다")
}
~~~
괄호로 묶어 정확히 구분 시켜주면 된다

또한 뒤에서 나올 if문 등과 같은 식을 넣을 수도 있다

코드
~~~
fun main(){
    val args = "Kotlin"
    println("Hello, ${if (args.length > 3) args[0] else "someone"}!")
}
~~~

출력

~~~
Hello, K!
~~~

그런데 만약 문자 $ 자체를 출력하고 싶다면 

코드
~~~
fun main(){
    print("\$달러")
}
~~~

출력

~~~
$달러
~~~

이렇게 \를 붙여주면 된다

# 변수

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

## 변수 타입



코틀린에서는 변수에 타입을 명시하지 않아도 변수가 선언될 때 할당된 값의 형태로 어떤 자료형을 가지는지 추론한다

하지만 타입 명시가 필요한 경우에는 따로 타입을 명시할 수 있다

코드
~~~
fun main(){

    val byte : Byte = 123
    val short : Short = 12345
    val int : Int = 1234567890
    val long : Long = 1234567890123456789

    val float : Float = 1.23F
    val double : Double = 1.23
    val any : Any
}
~~~

타입에 따라 저장 가능한 크기도 다르다 또한 실수형 타입을 사용할 때
Flaot 타입은 뒤에 F를 적어 Float타입임을 명시해 줘야 한다 또한
any타입은 어떠한 값이든 될 수 있는 타입을 말한다

코드
~~~
fun main(){

    val bool : Boolean = true
    val char : Char = 'a'
    val string : String = "abc"

}
~~~

숫자형 타입들 이외에도 참 거짓을 나타내는 Boolean 타입 글자 하나를 저장하는 Char 타입 여러 Char 타입을 저장하는 String 타입이 있다

참고로 String 타입은 string[0]과 같이 []안에 숫자를 적어 해당 차례에 요소에 접근이 가능하다 

코드
~~~
fun main(){

    val string : String = "abc"

    print(string[0])
}
~~~
출력
~~~
a
~~~

## 연산자

### 산술 연산자
산술 연산자란 사칙연산을 다루는 기본적이면서도 가장 많이 사용되는 연산자를 뜻하며 그 종류로는 +, -, *, /, %가 있다

### 대입 연산자

대입 연산자는 변수에 값을 대입할 때 사용하는 이항 연산자이다 종류로는 = 과
산술 연산자와 결합한 +=,-=,*=,/=,%가 있다

코드
~~~

fun main() {

    var a = 6
    var b = 3

    println("a + b 값은 : ${a+b}")

    println("a - b 값은 : ${a-b}")

    println("a * b 값은 : ${a*b}")

    println("a / b 값은 : ${a/b}")

    println("a % b 값은 : ${a%b}")

    a+=b
    println("a + b 대입 값은 : $a")

    a-=b
    println("a - b 대입 값은 : $a")

    a*=b
    println("a * b 대입 값은 : $a")

    a/=b
    println("a / b 대입 값은 : $a")

    a%=b
    println("a % b 대입 값은 : $a")

}

~~~

출력

~~~
a + b 값은 : 9
a - b 값은 : 3
a * b 값은 : 18
a / b 값은 : 2
a % b 값은 : 0
a + b 대입 값은 : 9
a - b 대입 값은 : 6
a * b 대입 값은 : 18
a / b 대입 값은 : 6
a % b 대입 값은 : 0
~~~

예시

* a = 10 a에 10을 넣는다
* b = 5 b에 5를 넣는다 
* a + b a와 b를 더한다
* a - b a와 b를 뺀다
* a * b a와 b를 곱한다
* a / b a와 b를 나눈다
* a % b a와 b를 나눈 값에 나머지를 구한다

앞에서 미리 설명한 대입연산자에서 복한 연산자에 의미를 보면

* a += b 는 a = a + b와 같다 
* a -= b 는 a = a - b와 같다 
* a *= b 는 a = a * b와 같다 
* a /= b 는 a = a / b와 같다
* a %= b 는 a = a % b와 같다

### 증감연산자
a++,++a,a--,--a와 같은 것을 증감연산자라고 하며 의미는 ++a는 a에 1을 더한 후 반환
a++는 a를 반환 후 1을 더함
 
### 비교 연산자
비교 연산자는 왼쪽의 피연산자와 오른쪽의 피연산자를 비교하여 상대적인 크기를 판단하는 연산자를 말한다

* ㅤ== 왼쪽의 피연산자와 오른쪽의 피연산자가 같으면 참을 반환
* ㅤ!= 왼쪽의 피연산자와 오른쪽의 피연산자가 같지 않으면 참을 반환
* ㅤ> 	왼쪽의 피연산자가 오른쪽의 피연산자보다 크면 참을 반환
* ㅤ>= 왼쪽의 피연산자가 오른쪽의 피연산자보다 크거나 같으면 참을 반환
* ㅤ< 왼쪽의 피연산자가 오른쪽의 피연산자보다 작으면 참을 반환
* ㅤ<= 왼쪽의 피연산자가 오른쪽의 피연산자보다 작거나 같으면 참을 반환

### 논리 연산자

논리 연산자는 주어진 논리식을 판단하여, 참(true)과 거짓(false)을 결정하는 연산자를 말한다

* && AND 논리식이 모두 참이면 참을 반환
* || OR 논리식 중에서 하나라도 참이면 참을 반환
* ! NOT 논리식의 결과가 참이면 거짓을, 거짓이면 참을 반환
---

## 조건문 

조건문이란 주어진 조건식의 결과에 따라 별도의 명령을 수행하도록 제어하는 명령문이다

### if문 

if 문은 조건식의 결과가 참(true)이면 주어진 명령문을 실행하고 거짓(false)이면 아무것도 실행하지 않는 조건문을 말한다

코드
~~~

fun main() {

    val apple = 4

    if(apple>5){
        println("사과가 5개보다 많습니다");
    }
    else if (apple>3){
        println("사과가 3개보다 많습니다");
    }
    else {
        println("사과가 3개보다 적습니다");
    }

}

~~~

출력

~~~
사과가 3개보다 많습니다
~~~

이것이 if문에 형태이다 차근차근 뜯어보면

~~~
if(apple>5){
        println("사과가 5개보다 많습니다")
    }
~~~

if를 적고 괄호 안에 조건을 적는다 여기서
만약 조건이 참이라면 중괄호에 적은 코드를 실행시킨다

~~~
else if (apple>3){
    println("사과가 3개보다 많습니다");
}
~~~
else if는 if문이 거짓일 때 실행된다
if랑 마찬가지로 괄호 안에 조건을 적고 여기서
만약 조건이 참이라면 중괄호에 적은 코드를 실행 시킨다

앞에서 apple을 4로 선언했으니
해당 조건 참이 되어 중괄호 안 코드인 println("사과가 3개보다 많습니다")가 실행되어 "사과가 3개보다 많습니다"라는 문장이 출력되게 된다

~~~
else {
    println("사과가 3개보다 적습니다")
}
~~~

여기서 else는 위에 적은 조건들이 모두 거짓일 때 실행되는 곳이다

참고로 if문은 첫 번째 문장이 참이여서 실행된다면 else if 로 밑에 조건이 참이여도 실행되지 않고 종료된다

### 논리 연산자

논리 연산자인 &&와 ||를 사용하면 if문에 조건을 추가할 수 있는데 

코드
~~~
fun main() {

    val apple = 4
    val banana = 5

    if (apple > 5 && banana > 4) {
        println("과일이 매우 많습니다")
    }
    else if (apple > 5 || banana > 4) {
        println("과일이 많습니다")
    }
    else {
        println("과일이 적습니다")
    }

}
~~~

출력
~~~
과일이 많습니다
~~~

차근 차근 코드를 뜯어보자
~~~
if (apple > 5 && banana > 4) {
    println("과일이 매우 많습니다")
}
~~~
우선 apple>5 && banana>4은 apple이 5보다 크다 와 banana가 4보다 크다는 조건을 모두 만족해야만 참이 된다

~~~
else if (apple > 5 || banana > 4) {
    println("과일이 많습니다")
}
~~~
apple>5 || banana>4는 apple이 5보다 크다 와 banana가 4보다 크다는 조건 중 하나만 만족해도 참이 된다 그러니 "과일이 많습니다"라는 문장이 출력 된 것이다

참고로 

~~~
fun main() {

    val apple = 3

    if (apple > 4)
        println("과일이 많습니다")
    else
        println("과일이 별로 없습니다")

}
~~~
위와 같이 괄호 없이도 간추려 사용할 수 있다

### 변수에 if문 사용

코드
~~~
fun main() {
    val apple = 3

    val box = if (apple>3){
        "사과가 많이 들어있음"
    }
    else {
        "사과가 적게 들어있음"
    }

    println(box)
}
~~~
출력
~~~
사과가 적게 들어있음
~~~
위와 같이 변수에 값을 if문을 사용하여 넣는 것이 가능하다

### 조건문에서 자주 쓰는 조건 연산자

1. ㅤ>= : 좌변이 우변보다 같거나 크면 참이 된다
2. ㅤ> : 좌변이 우변보다 크면 참이 된다
3. ㅤ<= : 좌변이 우변보다 작거나 같으면 참이 된다
4. ㅤ< : 좌변이 우변보다 작으면 참이 된다
5. ㅤ== : 좌변과 우변이 같으면 참이 된다
6. ㅤ!= : 좌변과 우변이 다르면 참이 된다

### when문

when문 if문과 같은 조건 제어문으로 if랑 달리 <,>,<=,>=등과 같은 범위를 사용할 수 없고 if문은 조건식이 true일 경우에 실행된다고 하면 
when문 비교할 변수가 어떤값을 가지냐에 따라 실행문을 선택되는 방식이다
==만 사용하는 if이라고 생각하면 편하다

코드
~~~
fun main() {
    val age = 20
    when(age){
        in 1..7 -> println("어린이 클럽")
        in 8..19 -> println("학생 클럽")
        in 20..32 -> println("클럽")
        else -> println("나이트 클럽")
    }
}
~~~

출력
~~~
클럽
~~~

위 코드를 뜯어보면 

~~~
in 1..7 -> println("어린이 클럽")
~~~
이 부분은 age에 값이 1~7사이로 들어오면 어린이 클럽을 출력한다는 의미이고 그럼 자연스럽게 밑에 값들도 해당 범위에 값이 들어오면 알맞은 문구를 출력하게 된다는 걸 알 수 있다

또한 is라는 것도 사용할 수 있는데

코드
~~~
fun main() {
    val x : Any = 312.23F
    when(x){
        is Int -> println("이것은 Int입니다")
        !is Int -> println("이것은 Int가 아닙니다")
    }
}
~~~
출력
~~~
이것은 Int가 아닙니다
~~~

해당 코드를 뜯어보면 

~~~
is Int -> println("이것은 Int입니다")
~~~
이 부분은 값이 Int이면 이것은 Int입니다를 출력하고
~~~
!is Int -> println("이것은 Int가 아닙니다")
~~~
이 부분은 값이 Int가 아니면 이것은 Int가 아닙니다를 출력하라는 코드이다

