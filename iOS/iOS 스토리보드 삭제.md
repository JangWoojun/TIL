> 작성일 2023/02/11 ~ 2023/02/11 

# 스토리보드 삭제

### 1. **Info.plist 수정**

<img width="866" alt="스크린샷 2023-02-11 오후 8 02 31" src="https://user-images.githubusercontent.com/102157871/218255547-d6029789-994d-41de-b40d-ae0a9f5f3520.png">

여기서 StoryBoard Name 완전 삭제

### 2. **프로젝트 수정**

<img width="678" alt="스크린샷 2023-02-11 오후 8 06 56" src="https://user-images.githubusercontent.com/102157871/218255549-48af520b-1a2f-4702-a1dd-bfc6fcc12266.png">

Supports multiple windows 클릭

<img width="675" alt="스크린샷 2023-02-11 오후 8 07 36" src="https://user-images.githubusercontent.com/102157871/218255551-16e4083a-9fbd-4d4f-97de-4cc60d0bddfd.png">

Main storyboard file base name에 Value 값 삭제

### 3. **SceneDelegate scene 수정**

```swift
guard let windowScene = (scene as? UIWindowScene) else { return }
        
        window = UIWindow(frame: UIScreen.main.bounds)
        
        let viewController = ViewController()
        window?.rootViewController = viewController
        
        window?.makeKeyAndVisible()
        window?.windowScene = windowScene
```
[1번 방법](#https://www.youtube.com/watch?v=UKknl2yxQr4)

```swift
        guard let windowScene = (scene as? UIWindowScene) else { return }

        let window = UIWindow(windowScene: windowScene)

        let viewController = ViewController()
        window.rootViewController = viewController

        window.makeKeyAndVisible()
        self.window = window
```
[2번 방법](#https://velog.io/@minni/Storyboard-%EC%97%86%EC%9D%B4-%EC%BD%94%EB%93%9C%EB%A1%9C-view-%EC%9E%91%EC%84%B1%ED%95%98%EA%B8%B0)

### 4. **iOS 13이하 버전 대응**

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        if #available(iOS 13.0, *) { 
            return true
        }
        window = UIWindow()
        window?.rootViewController = ViewController() 
        window?.makeKeyAndVisible()
        return true
    }
```

