> 작성일 2023/02/11 ~ 2023/02/11 

# 문제 상황

<img width="910" alt="스크린샷 2023-02-10 오후 7 29 44" src="https://user-images.githubusercontent.com/102157871/218070487-424291c5-cbbf-4f9c-bf75-79932d9e9700.png">

구글 공식문서에서는 위와 같이 windowSplashScreenAnimatedIcon 을 통해 창 중앙 아이콘을 변경할 수 있다고 나와있다

<img width="908" alt="스크린샷 2023-02-10 오후 7 17 07" src="https://user-images.githubusercontent.com/102157871/218070466-6d08d64b-ea70-4cd3-9f83-72a8e4dc655a.png">

그래서 공식문서에 따라 배경과 아이콘을 설정하고 빌드하였지만 무언가 이상하여 Splash 화면을 멈춰서 확인해 보니

<img width="388" alt="스크린샷 2023-02-10 오후 7 38 00" src="https://user-images.githubusercontent.com/102157871/218071510-e881a22c-c40a-4795-91f5-2bc6bf56173b.png">

위와 같이 배경은 변경이 잘되고 있으나 아이콘을 변경이 되지 않고 뜨지 않는 문제가 발생하였다 

<img width="1126" alt="스크린샷 2023-02-10 오후 7 24 53" src="https://user-images.githubusercontent.com/102157871/218070476-3d54f8ae-c31f-40c7-8328-13c9ae46ddd3.png">

그래서 해당 문제를 해결하려고 열심히 구글링을 한 결과 구글 이슈 트래커에서 왜 이러한 문제가 발생하는지 

위와 같은 답을 얻을 수 있었다

<img width="1257" alt="스크린샷 2023-02-10 오후 7 26 11" src="https://user-images.githubusercontent.com/102157871/218070479-f6485cdf-0520-4fda-8735-f6bfa06783e1.png">
<img width="1048" alt="스크린샷 2023-02-10 오후 7 27 42" src="https://user-images.githubusercontent.com/102157871/218070483-b54ab981-5547-4bbc-9161-051e3d651e59.png">
<img width="998" alt="스크린샷 2023-02-10 오후 7 28 44" src="https://user-images.githubusercontent.com/102157871/218070484-917e76d5-a37f-493d-af67-7bea00519514.png">

코멘트들을 보니 해당 문제에 대해 불만을 가진 개발자들이 많은 것 같다

<img width="414" alt="스크린샷 2023-02-10 오후 7 47 34" src="https://user-images.githubusercontent.com/102157871/218073453-b88bd1ea-9659-41c9-858f-a4eb21cdb2ed.png">

어쨌든 이번엔 빌드를 11로 낮춰서 진행하니 변경한 아이콘이 잘 나오는 걸 볼 수 있다

안드로이드 개발 공부를 하던 중 아이콘이 설정한 대로 나오지 않아 내가 어느 부분에서 잘못하였는지 몰라 해당 문제를 해결하려고 끙끙대는 나 같은 사람이 없었으면 하는 마음에서 정보를 공유해 본다

# 해결법

해당 문제를 해결하는 법에 대해 조금 고민해 봤는데 개발 공부를 시작한 지 얼마 안 되어서 잘 모르지만 앱 아이콘 나오는 것이 중요하다면 

~~~
Handler().postDelayed({
    startActivity(Intent(this,MainActivity::class.java))
    finish()
},2000)
~~~

비효율적인 방식이라고 하지만 예전처럼 Splash를 위한 Activity를 첫 화면으로 세팅해 주고 Handler를 통해 일정 시간 이후 MainActivity로 넘겨주는 방법을 사용하거나 

Splash API를 사용하되, 안드로이드 버전을 확인하여 높은 버전에서는 추가적으로 빌드가 끝나면 Handler를 통해 잠깐 원하는 이미지를 보여주고 넘기는 방법을 써야 할 거 같다