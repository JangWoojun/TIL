> 작성일 2022/10/05 ~ 2022/10/05

# 안드로이드 Kotlin 일정 시간동안 특정 코드 지연 시키기

## 문제 상황

<img width="335" alt="스크린샷 2022-10-05 오후 8 39 06" src="https://user-images.githubusercontent.com/102157871/194052294-4a559164-2287-484a-9fdf-eb15915f53bf.png">

어떠한 코드를 일정 시간 이후, 딜레이 시켜 실행시키고 싶다 


## 해결법

~~~
Handler(Looper.getMainLooper()).postDelayed({
    //실행할 코드
}, //딜레이 시킬 시간)
~~~

해당 코드를 사용하여 딜레이 시킬 시간과 실행시킬 코드를 적으면 원하는 시간 만큼 딜레이 시켜 사용할 수 있다


<img width="590" alt="스크린샷 2022-10-05 오후 8 32 33" src="https://user-images.githubusercontent.com/102157871/194052291-bb7a60bc-404a-4f76-9e97-e798289e6e0a.png">
