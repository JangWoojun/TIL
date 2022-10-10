> 작성일 2022/10/02 ~ 2022/10/10

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

## 반복문 

반복문이란 프로그램 내에서 똑같은 명령을 일정 횟수만큼 반복하여 수행하도록 제어하는 명령문을 말한다

대표적으로 코틀린에서 많이 쓰이는 반복문은 while문,do-while문,for문이 존재한다

### while문 

코드
~~~
fun main() {
    var a = 10
    while (a>0){
        println(a)
        a-=1
    }
}
~~~

출력
~~~
10
9
8
7
6
5
4
3
2
1
~~~

while문에 구조를 뜯어보면 while 옆에 괄호에 조건식을 적고 중괄호에 실행시킬 코드가 있는 간단한 형태로 되어있다

조건식이 참이라면 계속해서 while문을 돌아
코드를 실행시키는 구조를 가져있기 때문에
제어 변수 등으로 종료시켜주어야만 한다

### do while문

do while문은 while문과 비슷한데

코드
~~~
fun main(){
    
    var x=10
    do {
        println(x)
        x-=1
    }while (x>11)
        
}
~~~
출력
~~~
10
~~~

do while문에 구조를 뜯어보면
do 옆에 중괄호안에 실행할 명령들을 적고
밑에 while에 조건식을 적는 형태를 가지고 있다 

일단 조건식이 참이던 거짓이든 do안에 있는 코드를 실행한다는 점만 제외하면 while문과 같다고 보면 된다

~~~
var x=10
    do {
        println(x)
        x-=1
    }while (x>11)
~~~

위에 코드를 보면 초기 x 값이 10인데 조건식이 x가 11보다 크다이니 while문이었다면 실행이 안 됐겠지만 do while문이기에 일단 실행하여 x 값을 출력하고 종료된다

### for문

코드 
~~~
fun main(){
    for(num in 1..10) {
            print("$num ")
        }

    print("\n")

    for(i in 1 until 10) { 
        print("$i ")
    }    
}

~~~
출력
~~~
1 2 3 4 5 6 7 8 9 10 
1 2 3 4 5 6 7 8 9        
~~~

위와 같은 형태들로 for문을 만들 수 있으며 꺼꾸로 출력할 때는

코드
~~~
fun main(){
        for(i in 10 downTo 1) {     
        print("$i ")
    }

    print("\n")

    for(i in 1 until 10 step 2) { 
        print("$i ")
    }
}
~~~
출력
~~~
10 9 8 7 6 5 4 3 2 1 
1 3 5 7 9 
~~~
위와 같이 역순으로도 가능하며
step으로 얼만큼 증가 혹은 감소할 지도 정할 수 있다

## 반복문에서 사용하는 제어문
반복문에서 사용하는 자주 사용하는 제어문 중에는 continue와 break가 있다

각 역할을 살펴보면 break는 반복문을 종료시켜 반목문을 탈출하는 역할을 하고 continue는 반복문을 빠져나가지 않고 패스시켜주는 역할은 한다

코드
~~~
fun main(){
    for (i in 1..20){
        if(i/2==5){
            break
        }
        println(i)
    }
}
~~~
출력
~~~
1
2
3
4
5
6
7
8
9
~~~
위 코드는 i가 10이 되자 i/2==5 조건이
일치하여 break문이 실행되어 10전까지 출력하다가 반복문이 종료된 코드이다

코드
~~~
fun main(){
        for (i in 1..20){
        if(i/2==5){
            continue
        }
        println(i)
    }
}
~~~
출력
~~~
1
2
3
4
5
6
7
8
9
12
13
14
15
16
17
18
19
20
~~~

위 코드는 i/2==5 조건이
일치하여 continue문 실행되어 10을 건너 뛰어 출력된 코드이다

## 함수

프로그래밍에서 함수(function)란 하나의 특별한 목적의 작업을 수행하기 위해 독립적으로 설계된 프로그램 코드의 집합이며

크게 표준 함수와 사용자 정의 함수로 구분할 수 있다

Kotlin에서 함수를 정의하는 방법은

fun 뒤에 함수명을 적고 소괄호안에 매개변수에 이름과 타입을 지정한뒤 : 뒤에 반환 값에 타입을 적고 중괄호안에 실행시킬 코드를 적으면 된다

 코드

 ~~~
fun main(){
    
    println(3+5)

}

fun plus(a:Int,b:Int):Int{
    return a+b
}
 ~~~
출력

~~~
8
~~~

코드를 뜯어보면 앞에서

~~~
fun plus(a:Int,b:Int):Int{
    return a+b
}
~~~
로 plus라는 a+b를 돌려주는 함수를 정의 했고
~~~
fun main(){
    
    println(3+5)

}
~~~
에서 호출하였기에 출력과 같은 결과가 나온 것이다


### return

return은 뜻 그대로 현재 함수에서 빠져나가 그 함수를 호출한 곳으로 되돌아 가게 하는 것과 함수내의 변수 또는 일정값을 되돌려 주는 역할은 한다


코드
~~~
fun main(){

    print(p())

}
fun p(): String {
    return "실행"
    return "실행 안됨"
}
~~~

출력

~~~
실행
~~~

함수가 종료되는 방법은 두 가지가 있는데
하나는 반환이 되어 종료를 하게 되는 것이고 다른 하나는 함수의 끝 부분 까지 실행하여 종료되는 것이다

그렇기에 return 0에서 함수가 종료되어 뒤에 문장을
실행되지 못한 것이다

### 가변 인자

함수를 선언할 때 매개변수에 vararg를 붙여주면 매개변수의 개수가 정해지지 않게 즉 가변으로 받을 수 있다

코드

~~~
fun main(){

    print(avg(1,2,3,4,5,6,7,8,9,10))
}

fun avg(vararg a:Int): Double {
    var num =0
    for (i in a){
        num+=i
    }
    return (num.toDouble()/a.size)
}
~~~

출력
~~~
5.5
~~~

avg 함수는 a를 가변으로 받고 for문으로 a를 하나 씩 가져와서
num이라는 변수에 더해준 뒤 num을 a에 개수로 나눠 평균 값을 구해주는 함수이다

출력이 5.5가 나온 까닭을 보면 main 함수에서 1부터 10까지 입력하였고 1부터 10에 합인 55에 10을 나눠서 5.5가 나온 것이다

## 널러블

널러블은 코틀린에서 변수가 null 타입을 가질 수 있게 허용한 것을 말한다
코틀린에서 기본적으로는 Non-null 타입으로 null을 가질 수 없는 타입이기에 null을 가지게
하고 싶다면 따로 처리를 해줘야 한다

코드
~~~
fun main(){

    var name : String = "Kotlin"
    name = null

    println(name)
}
~~~

출력
~~~
Error
~~~

코드
~~~
fun main(){

    var name : String? = "Kotlin"
    name = null

    println(name)
}
~~~

출력
~~~
null
~~~

두 코드에 차이를 보면 타입 옆에 ? 표를 붙였는가 안 붙였는 가로
코드가 오류가 나는지 안 나는지 결정되는 것을 볼 수 있다

그 까닭은 타입 뒤에 ? 를 붙이면 Nullable로
null값을 가질 수 있는 타입이 되기 때문이다

## 안전호출 연산자

안전호출 연산자는 Nullable 변수(객체)를 사용할 때 null일 경우 처리를  할 수 있도록 도와준다

코드
~~~
fun main(){

    var name : String? = "Kotlin"
    

    var nameLength = name?.length

    print(nameLength)

}
~~~

출력
~~~
6
~~~

코드
~~~
fun main(){

    var name : String? = "Kotlin"
    name = null

    var nameLength = name?.length

    print(nameLength)

}
~~~

출력
~~~
null
~~~~

안전 호출 연산자인 ?. 에 의미를 살펴보면

~~~
var nameLength = name?.length
~~~

만약 name에 null이 아니라면 name에 length를 nameLength 변수에 담고
null이라면 null을 nameLength 변수에 담는다는 뜻으로

~~~
var nameLength = name?.length
~~~
와

~~~
if(name !=null){
    var nameLength = name.length
}
else {
    var nameLength = null
}
~~~
는 같은 의미이다    

만약 null이 아니라면 name에 length를 출력하는 코드를 살펴보면

코드
~~~
fun main(){

    var name : String? = "Kotlin"
    name = null

    println(name?.length)
}
~~~

출력
~~~
null
~~~

코드
~~~
fun main(){

    var name : String? = "Kotlin"

    println(name?.length)
}
~~~

출력
~~~
6
~~~

이렇게 나타낼 수 있으며

~~~
println(name?.length)
~~~
에 의미는 name이 null이라면 null을 출력하고 아니라면
name에 length를 출력하라는 코드이다

## 엘비스 연산자

엘비스 연산자는 ?:로 표현하며 ?:의 왼쪽 객체가 non-null이면 
그 객체의 값이 리턴하고 null이라면 ?:의 오른쪽 값을 리턴한다

코드
~~~
fun main(){

    var name : String? = "Kotlin"
    
    println(name)

    name = null
    name = name ?: "language"

    println(name)
}
~~~

출력
~~~
Kotlin
language
~~~

해당 코드를 뜯어보면 첫번 째 println에서는 name에 값이 null이 아니었으니
원래 값인 Kotlin이 출력되고 두번 째에선 null로 값이 바뀌었으니 language가 출력된 것이다 

## non-null 연산자

!!을 사용하는 연산자로 널러블 타입을 non-null타입으로 변경해준다
단 null이면 오류가 나기 때문에 값이 있다고 확신해야만 사용할 수 있다

코드
~~~
fun main(){

    var name : String? = "Kotlin"

    name = name!!.toLowerCase()
    println(name)


}
~~~

출력
~~~
kotlin
~~~


코드
~~~
fun main(){

    var name : String? = "Kotlin"
    name = null

    name = name!!.toLowerCase()
    println(name)


}
~~~

출력
~~~
Error
~~~

참고로 여기서 toLowerCase()은 모두 소문자로 바꿔주는 메소드이다 

## 클래스

클래스란 값과 그 값을 사용하는 기능들을 묶어놓은 것으로 고유의 특징 값을 넣는 속성과 기능을 구현한 함수로 이루어졌다

코드
~~~
fun main(){

}
class MobilePhone(osName:String,brand:String,model:String)
~~~

코틀린에서 클래스 선언 법은 위 코드와 같이 class를 적은 뒤 클래스 명과 기본 생성자인 소괄호 안에 속성 값을 속성 값 명과 타입을 쉼표로 구분하며 선언할 수 있다

사실 여기서 constructor은 생략되었다

이러한 클래스는 인스턴스를 만드는 틀로 위에 선언한 클래스로 인스턴스를 만들어보자 

* 참고로 객체란 변수, 자료 구조, 함수, 메서드, 식별자에 의해 참조된 메모리 상의 값 등을 의미하고 인스턴스는 서로 다른 속성의 객체를 지칭하는 용어이다 

코드
~~~
fun main(){
    val galaxy = MobilePhone("Android","Samsung","S23")
}
class MobilePhone(osName:String,brand:String,model:String)
~~~

이렇게 하면 galaxy라는 변수에 osName 속성에는 Android 라는 값을 brand 속성에는 Samsung 이라는 값을 model 속성에는 S23 이라는 값을 인스턴스를 만든 것이다

### 인스턴트

코드
~~~
fun main(){
    val galaxy = MobilePhone("Android","Samsung","S23")
    println("galaxy에 os는 ${galaxy.osName}")
}
class MobilePhone(val osName:String, val brand:String, val model:String)
~~~
출력
~~~
galaxy에 os는 Android
~~~

위 코드처럼 인스턴트를 담은 변수를 사용하는 법은 변수명뒤에 .을 찍고 속성명을 적으면 된다

또한

코드
~~~
fun main(){
    val galaxy = MobilePhone(brand = "Samsung", model = "S23")
    println("galaxy에 os는 ${galaxy.osName} , brand는 ${galaxy.brand} , model은 ${galaxy.model}")
}
class MobilePhone(val osName:String = "Android", val brand:String, val model:String)
~~~

출력
~~~
galaxy에 os는 Android , brand는 Samsung , model은 S23
~~~

위와 같이 특정 속성 값에 기본 값을 지정하거나 특정 속성 값만 담는 것도 가능하다

### 이니셜라이저

다음으로 이렇게 클래스를 선언하게 되면 init을 사용할 수 있는데 여기서 init은 이니셜라이저를
지칭하며 객체가 생성될 때 호출되는 것을 말한다 

코드
~~~
fun main(){
    val galaxy = MobilePhone("Android","Samsung","S23")
    val iphone = MobilePhone("ios","Apple","14 Pro")
    val mi = MobilePhone("Android","Xiaomi","12S Ultra")
}
class MobilePhone(val osName:String,val brand:String,val model:String){
    init {
        println("This phone OS is $osName \nThis phone Brand is $brand \nThis phone Model Name is $model \n")
    }
}
~~~

출력
~~~
This phone OS is Android 
This phone Brand is Samsung 
This phone Model Name is S23 

This phone OS is ios 
This phone Brand is Apple 
This phone Model Name is 14 Pro 

This phone OS is Android 
This phone Brand is Xiaomi 
This phone Model Name is 12S Ultra 
~~~
위 코드에선 init에 속성 값들을 출력하게
만들었으니 인스턴트들이 만들어질 때 속성 값들이 출력된 것이다

### 메소드

자주 쓰는 기능들은 클래스 안에 함수로 만들 수 있는데 이것을 멤버함수 또는 메소드라고 하며
기기에 사양을 위와 같이 생성 될 때가 아닌 내가 원하는 것만 출력시킬 때 편하게 메소드를
만들어보면

코드 

~~~
fun main(){
    val galaxy = MobilePhone("Android","Samsung","S23")
    val iphone = MobilePhone("ios","Apple","14 Pro")
    val mi = MobilePhone("Android","Xiaomi","12S Ultra")

    iphone.spec()
}
class MobilePhone(val osName:String,val brand:String,val model:String){
    fun spec (){
        println("This phone OS is $osName \nThis phone Brand is $brand \nThis phone Model Name is $model \n")
    }
}
~~~
출력
~~~
This phone OS is ios 
This phone Brand is Apple 
This phone Model Name is 14 Pro 
~~~

### 멤버 변수

코드
~~~
fun main(){
    val galaxy = MobilePhone("Android","Samsung","S23")
    galaxy.price=1000

    println("galaxy is ${galaxy.price}$")
}
class MobilePhone(val osName:String,val brand:String,val model:String){
    
    var price : Int? = null
    
}
~~~
출력
~~~
galaxy is 1000$
~~~

클래스 내에서는 메소드 같이 함수 뿐만 아니라 변수도 선언할 수 있는데 이것을
멤버 변수라고 부른다


### 보조 생성자

보조 생성자란 클래스 내부에 정의하는 생성자로 constructor(인자){초기화}형태를 가진다

코드
~~~
fun main(){
    val galaxy = MobilePhone("Android","Samsung","S23",1000)

    galaxy.spec()

}
class MobilePhone(val osName:String,val brand:String,val model:String){
    var price : Int? = null
    constructor(osName:String, brand:String, model:String, price : Int):
            this(osName,brand, model){
                this.price=price
            }
    fun spec (){
        println("This phone OS is $osName \nThis phone Brand is $brand \nThis phone Model Name is $model \n" +
                "This phone Model Prince is $price$\n")
    }
}
~~~

출력
~~~
This phone OS is Android 
This phone Brand is Samsung 
This phone Model Name is S23 
This phone Model Prince is 1000$
~~~

해당 코드에 대해 뜯어보면 
~~~
constructor(osName:String, brand:String, model:String, price : Int)
~~~
라고 보조 생성자를 만들어줬고
~~~
:
            this(osName,brand, model)
~~~
이 부분에서 생성자에 osName,brand, model 값을 받는다고 해준 것이고
~~~
{
                this.price=price
            }
~~~
이 부분은 객체 생성 시 보조 생성자에 전달된 price에 값이 클래스 내부에 생성한 멤버 변수인 price으로 지정한 것이다

### 초기화

코드
~~~
fun main(){

    val galaxy = MobilePhone()


}
class MobilePhone(){

    var brand : String

}
~~~
출력
~~~
Error
~~~

위 코드와 같이 클래스내에 변수를 선언하면 항상 초기화를 시켜주어야 한다

하지만 lateinit을 추가하여 나중에 초기화를 예정시키는 방법이 있다

코드
~~~
fun main(){
    val galaxy = MobilePhone()

    galaxy.brand

}
class MobilePhone(){

    lateinit var brand : String
    
}
~~~
출력
~~~
Error
~~~
하지만 위와 같은 경우에도
아직 초기화를 시키지 않았는데 해당
값에 접근하려 한다면 오류가 나게 된다

그러니

코드
~~~
fun main(){
    val galaxy = MobilePhone()

    galaxy.brand

}
class MobilePhone(){

    lateinit var brand : String

    init {
        brand = "Samsung"
    }

}
~~~
출력
~~~
~~~

위와 같이 init으로 초기화를 시켜주게 되면
오류가 안나게 된다

### private

private는 해당 클래스에서만 사용할 수 있게 하는 것이다
만약 그 밖에서 사용하려고 한다면 오류가 발생하게 된다


코드
~~~
fun main(){
    val galaxy = MobilePhone()

    galaxy.brand

}
class MobilePhone(){



    private var brand : String

    init {
        brand = "Samsung"
    }

}
~~~
출력
~~~
Error
~~~

### 게터와 세터

게터는 필드의 값을 반환하는 역할이고
세터는 필드를 초기화하는 역할이다

코드
~~~
fun main(){
    val galaxy = MobilePhone()

    println(galaxy.brand)

}
class MobilePhone(){



    var brand : String = "SAMSUNG"
    get() {
        return field.toLowerCase()
    }

}
~~~

출력
~~~
samsung
~~~

해당 코드는 brand에 접근하려고 하면
소문자로 받는 코드이다


코드
~~~
fun main(){
    val galaxy = MobilePhone()

}
class MobilePhone(){
    
    var price : Int = 100

    get() = field
    set(value) {
        field = value
    }
    

}
~~~

코드를 보면
~~~
    get() = field
    set(value) {
        field = value
    }
~~~
이 부분에 코드는 우리가 
~~~
var price : Int = 100
~~~
이 변수를 만들 때 자동으로 생성되는 것으로
field(price)는 value 값과 같다라는 것이다

이 코드를 수정하면

코드
~~~
fun main(){
    val galaxy = MobilePhone()

    galaxy.price = -1
    println(galaxy.price)

}
class MobilePhone(){

    var price : Int = 100
    get() = field
    set(value) {
        field = if(value > 0) value else throw IllegalArgumentException("price must be greater than zero")
    }

~~~
출력
~~~
Error 
price must be greater than zero
~~~

아렇게 만약 value가 0 이하일 시 price must be greater than zero 에러 메세지를 출력하게 
코드를 만들 수 있다

### 데이터 클래스

데이터 클래스는 copy(),equals(),toString() 등 다양한 메소드를 자동으로 생성해주는 클래스로 기본 생성자에 1개 이상의 파라미터가 있어야 하고
기본 생성자의 파라미터가 val 또는 var 로 선언해야 한다는 등 조건이 있다

코드
~~~
data class User(val id: Long, var name: String)

fun main(){
    val user1 = User(1,"Kotlin")
    val user2 = User(2,"JAVA")

    println(user1)
    println(user2)
}
~~~

출력
~~~
User(id=1, name=Kotlin)
User(id=2, name=JAVA)
~~~

위 코드처럼 데이터 클래스는
~~~
data class User(val id: Long, var name: String)
~~~
이렇게 data를 class 앞에 적어주고 그 뒤 클래스명과
생성자에 파라미터를 하나 이상 있어야 되며
var나 val이여야 한다

또한 위에서 설명한 것처럼 유용한 메소드를 사용할 수 있는데
~~~
data class User(val id: Long, var name: String)

fun main(){
    val user1 = User(1,"Kotlin")
    val user2 = User(2,"JAVA")
    val user3 = User(3,"Kotlin")

    val copyUser1 = user3.copy(id = 1)

    println(user3)
    println(copyUser1)

    println(user1.equals(copyUser1))
}
~~~

출력
~~~
User(id=3, name=Kotlin)
User(id=1, name=Kotlin)
true
~~~

위 코드처럼
~~~
val copyUser1 = user3.copy(id = 1)
~~~
copy하여 특정 값만 바꿀 수도 있고

~~~
println(user1.equals(copyUser1))
~~~
== 대신 equals()로 비교할 수도 있다

## 상속

코틀린에는 상속이라는 개념이 존재하여 

크게 부모 클래스(상위 클래스)와 자식 클래스(하위 클래스)가 있고 자식 클래스는 부모 클래스를 선택하여 그 부모의 멤버를 상속받아 그대로 쓸 수 있게 된다

코드
~~~
open class Car (val name: String,val brand: String){

}

class ElectricCar(name: String, brand: String , batteryLife:Double) : Car (name, brand){

}
~~~

상속 방법은 위 코드처럼 처럼 부모 클래스가 될 클래스 앞에 open을 적어준 뒤
자식 클래스에는 : 뒤에 상속 받을 부모 클래스를 적어준다 여기서 명심할 점은 

부모의 매개 변수를 자식에게도 추가해 줘야 한다 또한 부모의 매개 변수들 모두 추가했다면
자식에게 다른 배개 변수를 추가해도 된다

상속에 특징으로는

코드
~~~
open class Car (val name: String,val brand: String){
    var range:Double = 0.0

    fun extendRange(amount: Double){
        if (amount>0){
            range+=amount
        }
    }
    fun drive(distance: Double){
        println("Drove for $distance KM")
    }

}

class ElectricCar(name: String, brand: String , batteryLife:Double) : Car (name, brand){

}

fun main(){
    var myCar = Car("A6","Audi")
    var myEcar = ElectricCar("S-Model","Tesla",85.0)

    myCar.drive(200.0)
    myEcar.drive(399.0)
}
~~~

출력
~~~
Drove for 200.0 KM
Drove for 399.0 KM
~~~

이렇게 부모 클래스에 있는 프로퍼티와 메소드를 사용할 수 있다

~~~
open class Car (val name: String,val brand: String){
    var range:Double = 0.0

    fun extendRange(amount: Double){
        if (amount>0){
            range+=amount
        }
    }
    fun drive(distance: Double){
        println("Drove for $distance KM")
    }

}

class ElectricCar(name: String, brand: String , batteryLife:Double) : Car (name, brand){

}



fun main(){
    var myCar = Car("A6","Audi")
    var myEcar = ElectricCar("S-Model","Tesla",85.0)

    myCar.drive(200.0)
    myEcar.drive(399.0)

    myCar.toString()
}
~~~

또한 어느 클래스든 Any 클래스를 상속 받기에
equals,hashCode,toString 같은 함수 또는 메소드를 사용할 수 있다

### 오버라이딩

부모클래스의 메소드를 자식클래스에서 재정의해서 사용할 수 있는데 이걸 오버라이딩이라고 한다

코드
~~~
open class Car (val name: String,val brand: String){
    open var range:Double = 0.0

    fun extendRange(amount: Double){
        if (amount>0){
            range+=amount
        }
    }
    fun drive(distance: Double){
        println("Drove for $distance KM")
    }

}

class ElectricCar(name: String, brand: String , batteryLife:Double) : Car (name, brand){
    override var range = batteryLife*6
}



fun main(){
    var myCar = Car("A6","Audi")
    var myEcar = ElectricCar("S-Model","Tesla",85.0)

    myCar.range = 85.0


    println("myCar range = ${myCar.range}\nmyEcar range = ${myEcar.range}")
}
~~~

출력
~~~
myCar range = 85.0
myEcar range = 510.0
~~~

이렇게 오버라이딩을 하려면 자식 클래스에 오버라이딩을 시킬 것에 override을 적으면
된다 여기서 주의 할 점은 오버라이딩 시킬 요소가 부모 클래스에서 open 되어 있어야 한다

## 인터페이스
인터페이스란 다른 클래스를 작성할 때 기본이 되는 틀을 제공하면서 다른 클래스 사이의 중간 매개 역할까지 담당하는 일종의 추상 클래스를 의미한다

코드
~~~
interface Drivable{
    val maxSpeed: Double
    fun brake() : String
}
~~~

인터페이스는 위 코드처럼 이름 앞에 interface를 붙여 선언한다

코드
~~~
interface Drivable{
    val maxSpeed: Double
    fun brake() : String
}

open class Car (val name: String, val brand: String, override val maxSpeed: Double):Drivable{
    open var range:Double = 0.0

    fun extendRange(amount: Double){
        if (amount>0){
            range+=amount
        }
    }
    fun drive(distance: Double){
        println("Drove for $distance KM")
    }

    override fun brake(): String {
        return "brake!!"
    }


}
~~~

클래스가 인터페이스의 기능을 확장한다면 위 코드처럼 : 뒤에 확장할 인터페이스 명을 붙인다
그리고 인터페이스에 있는 것들을 추가해줘야 한다

코드
~~~
interface Drivable{
    val maxSpeed: Double
    fun brake() : String
}

open class Car (val name: String, val brand: String, override val maxSpeed: Double):Drivable{
    open var range:Double = 0.0

    fun extendRange(amount: Double){
        if (amount>0){
            range+=amount
        }
    }
    fun drive(distance: Double){
        println("Drove for $distance KM")
    }

    override fun brake(): String {
        return "brake!!"
    }


}

class ElectricCar(name: String, brand: String, batteryLife:Double, maxSpeed: Double) :
    Car (name, brand, maxSpeed){

}



fun main(){
    var myCar = Car("A6","Audi",300.0)
    var myEcar = ElectricCar("S-Model","Tesla",85.0,400.0)

    print(myCar.brake())

}
~~~

출력
~~~
brake!!
~~~

그럼 위 코드처럼 사용할 수 있다