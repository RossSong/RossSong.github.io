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
#####test code
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
iPhoneX 이상에서 full screen popview 만들때, 아래의 코드를 추가해야 full screen (탈몰(?) status bar 포함.)
```
viewController.modalPresentationStyle = .overFullScreen
self.navigationController?.definesPresentationContext = false
```
        
