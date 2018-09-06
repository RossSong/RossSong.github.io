ReSwift 로 "Hello World" 해보기

*이 Tutorial 에서는 Carthage 를 이용한다.

1.iOS 프로젝트 생성 (Single View App)

2.Carthage 이용을 위한 cartfile 작성

```
github "ReactiveX/RxSwift" ~> 4.0   
github "ReSwift/ReSwift"
```

3.Carthage 를 이용해서 framework 파일 받기
carthage update --platform iOS

4.Carthage 를 통해서 받아온 framework 파일을 프로젝트 Build Phrases 에서 Run Script 를 추가 하여 파일을 복사하고,
```
/usr/local/bin/carthage copy-frameworks   
```

```
$(SRCROOT)/Carthage/Build/iOS/RxSwift.framework   
$(SRCROOT)/Carthage/Build/iOS/RxCocoa.framework   
$(SRCROOT)/Carthage/Build/iOS/ReSwift.framework   
```

Link Binary With Libraries 에 framework 파일 추가

```
RxSwift.framework   
RxCocoa.framework   
ReSwift.framework   
```

5.ReSwift 사용을 위한 State, Action, appReducer 정의
```
import RxSwift
import RxCocoa
import ReSwfit 

struct AppState: StateType {
    var title = "Are you ready??"
}

struct SetupTitleAction: Action {
    let title: String
}

func appReducer(action: Action, state: AppState?) -> AppState {
    var state = state ?? AppState()
    
    switch action {
    case let setupTitleAction as SetupTitleAction: state.title = setupTitleAction.title
    default: break
    }
    
    return state
}
```

6.Store 생성

```
let store = Store(reducer: appReducer, state: AppState(), middleware: [])
```

7.ViewController 가 Store 의 State 를 수신할 수 있도록 StoreSubscriber 를 상속하고 Store 를 Subscribe  

```
class ViewController: UIViewController, StoreSubscriber {
    let disposeBag = DisposeBag()
    
    override func viewWillAppear(_ animated: Bool) {
        mainStore.subscribe(self)
    }

    override func viewWillDisappear(_ animated: Bool) {
        mainStore.unsubscribe(self)
    }
```


8.버튼 tap 이벤트에서 ReSwift Action 을 생성해서 보냄.

```
store.dispatch(SetupTitleAction(title: "hello world!"))
```

```
self.buttonGo.rx.tap
            .debounce(0.3, scheduler: MainScheduler.instance)
            .subscribe({ _ in
            store.dispatch(SetupTitleAction(title: "hello world!"))
        }).disposed(by: disposeBag)
```

9.appReducer 에서 처리된 Action 의 결과 State 를 UI 로 반영   
(StoreSubscriber를 상속한 ViewController 의 멤버 함수로 정의)

```
func newState(state: AppState) {
    self.labelTitle.text = state.title
}
```
