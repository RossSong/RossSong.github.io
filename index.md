# Swift, RxSwift, MVVM 관련 번역

#### [1.A practical MVVM example in Swift – Part 1](https://github.com/RossSong/RossSong.github.io/blob/master/1.md)

#### [2.A practical MVVM example in Swift – Part 2 (featuring RxSwift)](https://github.com/RossSong/RossSong.github.io/blob/master/2.md)

#### [3.Implementing MVVM in iOS with RxSwift](https://github.com/RossSong/RossSong.github.io/blob/master/3.md)

#### [4.The introduction to Reactive Programming you've been missing](https://github.com/RossSong/RossSong.github.io/blob/master/4.md)

#### [5.Getting Started With RxSwift and RxCocoa](https://github.com/RossSong/RossSong.github.io/blob/master/5.md)

#### [6.ReactiveCocoa vs RxSwift](https://github.com/RossSong/RossSong.github.io/blob/master/6.md)

#### [7.Learning RxSwift's Github Sample](https://github.com/RossSong/RossSong.github.io/blob/master/8.md)

#### [8.Introducing Protocol-Oriented Programming in Swift 3](https://github.com/RossSong/RossSong.github.io/blob/master/9.md)

#### [9.Introduction to Protocol Oriented Programming in Swift](https://github.com/RossSong/RossSong.github.io/blob/master/10.md)

#### [10.Protocol Oriented Programming View in Swift3](https://github.com/RossSong/RossSong.github.io/blob/master/11.md)

#### [11.Understanding Publish, Connect, RefCount and Share in RxSwift](https://github.com/RossSong/RossSong.github.io/blob/master/12.md)

# 기술 자료
#### [Snapchat, Snow 짝퉁 개발기](https://github.com/RossSong/RossSong.github.io/blob/master/dev_1.md)

### ReactorKit, ReSwift
[Hello World - ReactorKit](https://github.com/RossSong/RossSong.github.io/blob/master/13_hello_world_ReactorKit.md)   
[Hello World - ReSwift](https://github.com/RossSong/RossSong.github.io/blob/master/14_hello_world_ReSwift.md)  
[Algorithm](https://github.com/RossSong/RossSong.github.io/blob/master/22_Swift_algorithm.md)

### Legacy code 에 Unit Test 적용하기 
[Legacy code with Unit Test](https://github.com/RossSong/RossSong.github.io/blob/master/15_Legacy_code_with_Unit_Test.md)

### TDD in iOS
Use case based Test Driven Development

## Functional Programming
### Clojure  
[Living clojure - Chapter 7. Creating Web Applications With Clojure](https://github.com/RossSong/RossSong.github.io/blob/master/16_Living_Clojure_Study.md)

[Algorithm](https://github.com/RossSong/RossSong.github.io/blob/master/19_Clojure_algorithm.md)   
##### test code
```
(use 'clojure.test)
(defn add2 [x] (+ x 2))
(deftest test-adder (is (= 24 (add2 2))))
(test-adder)
FAIL in (test-adder) (form-init8814306212613603266.clj:2)
expected: (= 24 (add2 2))
  actual: (not (= 24 4))
nil
```
### Haskell

[Algorithm](https://github.com/RossSong/RossSong.github.io/blob/master/20_Haskell_algorithm.md)

#### command
```
stack runghc xxx.hs
runhaskell xxx.hs
```

#### Yesod

Hello world

## Machine Learning/Deep Learning/scikit-learn
[scikit-learn](https://github.com/RossSong/RossSong.github.io/blob/master/21_Scikit-Learn-1.md)

### OCR
### ChatBot/Q&A machine
### CycleGAN
### Kaggle
#### Dogs vs Cats

### Gaussian Process for Machine Learning
### PRML(Pattern Recognition & Machien Learning, Bishop)

Chapter 1. Introduction
```
1.1 Example: Polynomial Curve Fitting
sin(2pix) + noise(가우시안 정규분포를 따르는) 를 이용해서 학습 데이터 생성, sin(2pix) 를 찾는다.
계수 w, 차수 M 을 찾는다.
w 는 미분하여 기울기로 계산?.
M 2 이하일 때 Fitting 이 안되고, 9 이상이면 심하게 진동(Over Fiting)한다.
M 이 9 이상이어도 학습 데이터가 많거나, error function 에 regularization term 을 더하면 보정이 가능하다.
regularization term 의 ln lambda 가 0 이면 피팅이 거의 안되고, -18 이면 fitting 이 된다(?).
(ln lambda 가 - 무한대 이면, lambda 는 0 에 해당)
```
1.2 확률 이론


Chapter 6. 커널 방법론

커널이란?(https://www.quora.com/What-is-the-intuitive-explanation-of-a-kernel-in-statistics)

확률 분포는 평균과 분산으로 표현될 수 있는데, 분산값을 나타내는 함수??

6.2 커널의 구성

커널 대입을 위해서는 유효한 커널함수를 구성할 수 있어야 한다. 특정 공간 함수를 정한 후 이에 해당하는 커널을 찾는 방법. 대안으로 커널을 직접 구성하는 방법.   

--

Chapter 8. 그래프 모델

8.3 마르코프 무작위장

8.3.1 조건부 독립 성질

--

Chapter 10. 근사 추정

10.3.3 하한 경계

10.4 지수족 분포

### Block Chain
BitCoin  
Ethereum  
Cardano(ada)  

### Flutter

Redux in Flutter

### React

Redux

### TDD

requirements/spec -> test code -> product code

### Test-Driven Development with Python
chapter 1
```
django, web devier 설치
browser title 이 'django' 인지 확인하는 Test code 작성
Test failed.
$ python3 functional_tests.py Traceback (most recent call last):
      File "functional_tests.py", line 6, in <module>
        assert 'Django' in browser.title
    AssertionError

Product code 작성.
$ django-admin.py startproject superlists

Test passed
$ python3 manage.py runserver
Validating models...

0 errors found
Django version 1.7, using settings 'superlists.settings' 
Development server is running at http://127.0.0.1:8000/ Quit the server with CONTROL-C.

$ python3 functional_tests.py 
$
```
Chapter 2
```
User Story 먼저 작성(BDD?, Use case??, Spec??) -> Test Code -> Product Code
```

#### TDD in refactoring, woking with legacy code

#### python, flask, unit test

Hello world

test code
```
from app import app
import unittest

class BasicTestCase(unittest.TestCase):
    def testIndex(self):
        tester = app.test_client(self)
        response = tester.get('/', content_type='html/text')
        self.assertEqual(response.status_code, 200)
        self.assertEqual(response.data, b'Hello, World!')


if __name__ == '__main__':
    unittest.main()
```

product code
```
rom flask import Flask

app = Flask(__name__)

@app.route('/')
def hello():
     return 'Hello, World!'

if __name__ == '__main__':
     app.run()
```
#### jest

#### iOS
#### Swift
##### [Rx 기본요소 Event, Diposable, Observer, Observable 구현해보기](http://minsone.github.io/programming/swift4-implement-own-rx-event-disposable-observer-observable)
iPhoneX 이상에서 full screen popview 만들때, 아래의 코드를 추가해야 full screen (탈(?) status bar 포함.)
```
viewController.modalPresentationStyle = .overFullScreen
self.navigationController?.definesPresentationContext = false
```
#### VIPER

MVVM 을 적용하여 사용하다 보니, 좀 더 Rendering 로직과 비지니스 로직을 좀 더 분리해서 관리하면 좋을 것 같다는 생각을 가지게 되고, ViewController 간에 전환 로직도 따로 분리하면 좋을 것 같다는 생각을 하게 되는데, 그런 생각에 적합한 구조가 VIPER 가 아닌가 싶다. Rendering 로직은 Presenter 로, ViewConteroll 간에 전환은 Router 로, 비지니스 로직은 Interactor 로 분리하면 좋을 것 같다는 생각이 든다. (View와 Model(Entity)은 MVVM이나 VIPER도 같은 것이고..)   

### Elixir
```
mix new hello_exunit
mix test
iex -S mix
```

### hash table? hash code?
hashtable 은 Store/Retrieve 가 O(1)
hashtable 의 index 를 만드는 hashcode 는 입력 string 의 길이 m 에 대해 O(m)
hashtable insert 의 시간 복잡도는 hashtable 크기 n 이 m 에 비해서 아주 크다고 할때 m/n 은 아주 작아서 O(1) 로 볼 수 있을까? 
아니면 한번 계산하면 계속 값을 유지 하고 있어서 한번만 계산하면 되니 O(1)로 볼 수 있는 것일까?
그냥 보면 O(m) m 은 n 보다 아주 작다?
어찌 되었든 검색할 때 n 을 다 조회해볼 필요는 없으니 장점. 확실히 검색에서는 O(1) 이니..
