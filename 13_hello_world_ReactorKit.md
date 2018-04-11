Reactorkit 으로 "Hello world" 해보기

*이 Tutorial 에서는 Carthage 를 이용한다.

1.iOS 프로젝트 생성 (Single View App)

2.Carthage 이용을 위한 cartfile 작성

```
github "ReactiveX/RxSwift" ~> 4.0   
github "ReactorKit/ReactorKit"
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
$(SRCROOT)/Carthage/Build/iOS/ReactorKit.framework  
$(SRCROOT)/Carthage/Build/iOS/ReactorKitRuntime.framework     
```

Link Binary With Libraries 에 framework 파일 추가

```
RxSwift.framework   
RxCocoa.framework   
ReactorKit.framework   
ReactorKitRuntime.framework
```

5.Reactor 정의 - Reactor 를 상속한 ViewReactor 를 생성

```
import ReactorKit

class ViewReactor: Reactor {
}
```

6.ViewReactor 멤버로 Action, Mutation, State 정의

```
enum Action {
    case sayHello
}
    
enum Mutation {
    case setTitle(String)
}
    
struct State {
    var title: String = ""
}
```

7.initialSate 생성

```
var initialState = State()
```

8.Action 을 Mutation 으로 변환시키는 mutate 함수 정의

```
func mutate(action: ViewReactor.Action) -> Observable<ViewReactor.Mutation> {
    switch action {
    case .sayHello:
        return Observable.just(Mutation.setTitle("hello world!"))
    }
}
```

9.현재 상태 와 변환된 Mutation 으로 새로운 상태를 생성하는 reduce 함수 정의
```
func reduce(state: ViewReactor.State, mutation: ViewReactor.Mutation) -> ViewReactor.State {
    switch mutation {
    case let .setTitle(newTitle):
        return State(title: newTitle)
    }
}
```


10. Reactor 와 연결할 ViewController 가 View 를 상속하도록 추가

```
class ViewController: UIViewController, View {
```

11. ViewReactor 를 ViewController 의 reactor 로 설정   
(ViewController 생성 후 Reactor 를 따로 설정하도록 하는 것을 권장하지만, 간단히 테스트 하기 위해서 viewDidLoad 에서 설정)

```
override func viewDidLoad() {
    super.viewDidLoad()
    reactor = ViewReactor()
}
```

12.View 를 상속한 ViewController 가 ViewReactor 에 Bind 되도록 bind 함수 정의   
(View 를 상속함으로써 생성시 bind 함수가 내부적으로 자동으로 호출된다.)

```
func bind(reactor: ViewReactor) {
}
```

13.Button Tap 이벤트 발생시 sayHello Action 을 Reactor 로 발생시키도록 한다.

```
self.buttonGo.rx.tap.map{ Reactor.Action.sayHello }.bind(to: reactor.action).disposed(by: disposeBag)
```

14.Reactor 에서 Action 이 처리되어 새로운 State 가 발생하면 UI 로 반영할 수 있도록 연결한다.

```
reactor.state.map{ $0.title }.bind(to: labelTitle.rx.text).disposed(by: disposeBag)
```

결과적으로 bind 함수는 다음과 같이 된다.

```
func bind(reactor: ViewReactor) {
    self.buttonGo.rx.tap.map{ Reactor.Action.sayHello }.bind(to: reactor.action).disposed(by: disposeBag)
    reactor.state.map{ $0.title }.bind(to: labelTitle.rx.text).disposed(by: disposeBag)
}
```
