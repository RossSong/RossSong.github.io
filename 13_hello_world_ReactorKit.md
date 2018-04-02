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
```

Link Binary With Libraries 에 framework 파일 추가

```
RxSwift.framework   
RxCocoa.framework   
ReactorKit.framework   
```
