> 작성일 2022/09/06 ~ 2022/09/06

<br>

# C++ 기본 문법

## 기본 형태

~~~
#include <iostream>


int main(){
    

    return 0;
}
~~~

위에 형태가 C++를 사용하는 기본 형태다

차근 차근 뜯어보자
~~~
include <iostram>
~~~

해당 부분은 iostram이라는 헤더파일을
include 즉 포함한다는 의미로
외부 소스 파일에 정의된 변수나 함수를 쓰기 위해한다고 보면 된다

여기서 iostram은 C++에서 제공하는 입출력을 위한 표준 라이브러리다

~~~
int main(){
    

    return 0;
}
~~~

여기서 int main(){} 부분은 
프로그램이 가장 먼저 찾는 곳이며 이곳에서부터 실행을 시작하는 곳이다

return 0;에 의미는 성공적인 종료이며 main()으로 return 되면 프로그램이 종료된다 C99 버전 업데이트 이후 이제는 개발자가 직접쓰지 않아도 성공적으로 종료되면 알아서 리턴하기 때문에 생략해도 문제는 없다

## 네임스페이스(namespace)
C언어에는 없는 C++ 만의 새로운 기능인
네임스페이스(namespace)는 어떤 변수나 함수의 소속을 알려주는 기능을 한다

예제를 보면 이해하기 쉬운데 

~~~
#include <iostream> 
namespace A{
	int Num = 100;
}
namespace B{ 
	int Num = 200;
} 

using namespace A;
using namespace B; 

int main(){ 
	int Num = 300;

    std::cout << A::Num << std::endl;
    std::cout << B::Num << std::endl; 
	std::cout << Num << std::endl; 
	
    return 0; 
}
~~~
~~~
출력 값

100
200
300
~~~
보다시피 같은 Num 이라도 다르게 값이 출력된다
여기서 A::,B::,std:: 이렇게 앞에 붙인 것이
해당 소속 네임스페이스에서 가져온다고 표시하는 거라고 이해하면 된다

이걸 생략하는 방법이 있는데

~~~
#include <iostream>
namespace std;

int main(){
    
    cout << "a" << endl;

    return 0;
}
~~~
이렇게 using namespace "이름" 이렇게 적어놓으면 굳이 해당 네임스페이스를 사용할 때
std:: 이렇게 일일이 적지 않아도 된다

하지만 이름 충돌이 날 수 있으니 std::cout 이런 식으로 붙이는 걸 권장한다

여기서 std는 "standard(표준)"의 약자로 C++ 표준 라이브러리의 모든 기능은 std라는 namespace 안에 있다고 보면 된다
