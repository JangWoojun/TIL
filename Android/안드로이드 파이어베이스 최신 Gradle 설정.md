> 작성일 2022/09/24 ~ 2022/09/24

# 안드로이드 스튜디오 최신버전 파이어베이스 Gradle Kotlin 설정

# 문제 상황

파이어베이스 사이트에서 알려주는 android studio gradle 연결 방법이 최신 버전과는 다르다

# 해결법

파이어베이스 사이트에서 알려주는 android studio gradle 연결 방법이 최신 버전과는 다르기 때문에

공식 문서와 다른 방법으로 gradle을 설정해주어야 한다

project 수준 gradle에는

~~~
plugins {
    id 'com.google.gms.google-services' version '4.3.13' apply false
}
~~~
해당 부분을 추가해 주고

app 수준 gradle (gradle)에는

~~~
plugins {
    id 'com.google.gms.google-services'
}
dependencies {
    implementation platform('com.google.firebase:firebase-bom:30.3.1')
    implementation 'com.google.firebase:firebase-database:20.0.5'
    implementation 'com.google.firebase:firebase-analytics-ktx'
}
~~~
이것들을 추가해 준다
