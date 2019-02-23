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

## Functional Programming, Algorithm

### Functor, Applicative, Monad
```
functors: you apply a function to a wrapped value using fmap or <$>
something that can be mapped over.
typeclass that has a definition for fmap.

applicatives: you apply a wrapped function to a wrapped value using <*> or liftA
typeclass that has a definition for <*>.

monads: you apply a function that returns a wrapped value, to a wrapped value using >>= or liftM
typeclass that has definitions for return, bind
"return" operator return a monad.
"bind" operator return a monad as a result that come from a function applied to Monad(wrapped value)
```
[Kotlin Functors, Applicatives, And Monads in Pictures](https://hackernoon.com/kotlin-functors-applicatives-and-monads-in-pictures-part-3-3-832d58d92445)  
[Swift Functors, Applicatives, and Monads in Pictures](https://www.mokacoding.com/blog/functor-applicative-monads-in-pictures/)

### Clojure  
[Living clojure - Chapter 7. Creating Web Applications With Clojure](https://github.com/RossSong/RossSong.github.io/blob/master/16_Living_Clojure_Study.md)

[Destructuring in Clojure](https://clojure.org/guides/destructuring)

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

### Elixir
```
mix new hello_exunit
mix test
iex -S mix
```

[Algorithm](https://github.com/RossSong/RossSong.github.io/blob/master/Elixir_algorithm.md)  

### Swift
[Algorithm](https://github.com/RossSong/RossSong.github.io/blob/master/22_Swift_algorithm.md)

### Algorithm/Data Structure
#### hash table? hash code?
hashtable 은 Store/Retrieve 가 O(1)
hashtable 의 index 를 만드는 hashcode 는 입력 string 의 길이 m 에 대해 O(m)
hashtable insert 의 시간 복잡도는 hashtable 크기 n 이 m 에 비해서 아주 크다고 할때 m/n 은 아주 작아서 O(1) 로 볼 수 있을까? 
아니면 한번 계산하면 계속 값을 유지 하고 있어서 한번만 계산하면 되니 O(1)로 볼 수 있는 것일까?
그냥 보면 O(m) m 은 n 보다 아주 작다?
어찌 되었든 검색할 때 n 을 다 조회해볼 필요는 없으니 장점. 확실히 검색에서는 O(1) 이니..

### Tree

### Heap
```
min/max heap
heapify
```

### Sort
```
bubble sort
quick sort
merge sort
```

### Graph

# ML
## Machine Learning/Deep Learning/scikit-learn
[scikit-learn](https://github.com/RossSong/RossSong.github.io/blob/master/21_Scikit-Learn-1.md)

### trends(?)
Scaled Dot-Product Attention, Multi-Head Attention, Transformer

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

1.2.3 베이지안 확률

베이지안 확률 이론에서는 빈도론과는 대조적으로 오직 하나의 (실제로 관측된) 데이터 집합 D 만이 존재하고 매개변수의 불확실성은 w 의 확률분포를 통해 표현한다.
-> 불확실성의 대상이 매개변수 w임. 데이터 집합 D 가 하나이고 이 D 를 만족하는 Y = WX + b 의 W가 여러가지일 수 있고, W가 여러개이기 때문에 불확실한 것이고, 이  W 를 어떻게 결정하느냐가 관건인데?? 빈도론적 방법에서 자주 사용되는 최대가능도(maximum likehood)를 이용해서, p(D|w)를 최대화 하는 값을 선택한다. -log(p(w|D)) 를(오차함수)를 최소화하는 w 를 찾으면 가능도가 최대화되고, p(D|w)가 최대화 된다. P(D|w) = P(w|D)p(w)/p(D) 이므로 P(D|w)는 p(w|D) 에 비례하기 때문?? -> 그런데 -log(p(w|D)) 를 최소화하는 w 를 어떻게 찾지?? p(w|D) 는 D가 주어질때 p(w)의 확률분포가 가우시안, 베타, 디리클레 분포 등을 따른 다고 가정하고 가장잘 맞는 w 를 골라낸다????? (계속 헷갈림..)


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

# Block Chain
BitCoin  
Ethereum  
Cardano(ada)  

# Cross-platform
### Flutter

Redux in Flutter

### React

Redux

# Clean Code/TDD
### Clean Code
Robert C. Martin   

#### Chapter 1: Clean Code
##### The Boy Scout Rule
```
Leave the campground cleaner than you found it.
```
#### Chapter 2: Meaningful Names
##### Use Intention-Revealing Names
##### Avoid Disinformation
##### Make Meaningful Distinctions
##### Use Pronounceable Names
#### Chapter 3: Meaningful Names
##### Small!!
```
Every function in this program was just two, or three, or four lines long.
Each was transparently obvious. 
Each told a story. 
And each led you to the next in a compelling order. 
That’s how short your functions should be!
```
###### Blocks and Indenting
```
This implies that the blocks within if statements, else statements, while statements, and so on should be one line long. Probably that line should be a function call. Not only does this keep the enclosing function small, but it also adds documentary value because the function called within the block can have a nicely descriptive name.
This also implies that functions should not be large enough to hold nested structures. Therefore, the indent level of a function should not be greater than one or two. This, of course, makes the functions easier to read and understand.
```
##### Do One Thing
```
So, another way to know that a function is doing more than “one thing” is if you can extract another function from it with a name that is not merely a restatement of its imple- mentation [G34].
```
##### One Level of Abstraction per Function
##### Reading Code from Top to Bottom: The Stepdown Rule
##### Have No Side Effects
##### Don't Repeat Yourself

#### Chapter 4: Comments
##### Comments Do Not Make Up for Bad Code
##### Explain Yourself in Code
##### Good Comments
```
Legal Comments
Informative Commnets
Explanation of Intent
Clarification
Warning of Consequences
TODO Comments
Amplification
Javadocs in Public APIs
```
##### Bad Comments
```
Mumbling
Redundant Comments
Misleading Comments
Mandated Comments
Journal Comments
Noise Comments
Don’t Use a Comment When You Can Use a Function or a Variable
Position Markers
Closing Brace Comments
Attributions and Bylines
Commented-Out Code
HTML Comments
Nonlocal Information - " Don’t offer systemwide information in the context of a local comment. "
Too Much Information
Inobvious Connection - " The purpose of a comment is to explain code that does not explain itself. It is a pity when a comment needs its own explanation."
Function Headers - "Short functions don’t need much description. A well-chosen name for a small function that does one thing is usually better than a comment header. "
Javadocs in Nonpublic Code
```

### TDD
```
TDD 에서 가장 중요한 것은 아무래도 요구사항(requirements/spec)을 코드가 아닌 글로 명확히 작성하는 것같다.
모든 것의 시작이 되는 부분이다.
요구사항을 기술은 문장이 있어야 Product code 를 작성하기 이전에 Test code 를 명확하게 작성할 수 있다.
```   

requirements/spec -> test code -> product code

### Legacy code 에 Unit Test 적용하기 
[Legacy code with Unit Test](https://github.com/RossSong/RossSong.github.io/blob/master/15_Legacy_code_with_Unit_Test.md)

### TDD in iOS
Use case based Test Driven Development

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

# Mobile
### iOS
#### Swift
##### [Rx 기본요소 Event, Diposable, Observer, Observable 구현해보기](http://minsone.github.io/programming/swift4-implement-own-rx-event-disposable-observer-observable)
iPhoneX 이상에서 full screen popview 만들때, 아래의 코드를 추가해야 full screen (탈(?) status bar 포함.)
```
viewController.modalPresentationStyle = .overFullScreen
self.navigationController?.definesPresentationContext = false
```
#### VIPER

MVVM 을 적용하여 사용하다 보니, 좀 더 Rendering 로직과 비지니스 로직을 좀 더 분리해서 관리하면 좋을 것 같다는 생각을 가지게 되고, ViewController 간에 전환 로직도 따로 분리하면 좋을 것 같다는 생각을 하게 되는데, 그런 생각에 적합한 구조가 VIPER 가 아닌가 싶다. Rendering 로직은 Presenter 로, ViewConteroll 간에 전환은 Router 로, 비지니스 로직은 Interactor 로 분리하면 좋을 것 같다는 생각이 든다. (View와 Model(Entity)은 MVVM이나 VIPER도 같은 것이고..)   

# ETC
## PDF 문서 포맷 분석
PDF 내에 특정 문자열(전화번호, 이메일 등)을 치환하는 것에 대한 리서치
1.PDF 에서 Text 영역을 분리
```
PDF 파일에서 Text 영역은 아래의 형식으로 저장됨.
BT
/F1 12 Ft
(...)Tj
ET
Tj 앞에 있는 부분들이 Text 내용임.
Ft 앞에 있는 내용들이 Text 가 Encoding 된 Font 에 대한 내용임. F1 폰트를 쓰고, 폰트 사이즈를 12로 함.
Tj 앞에 있는 부분들은 Plain Text 일 수도 있고, Encoding 된 Text 일 수도 있다.
Encoding 된 경우 Tj 에는 해당 Text 의 encoding index가 나타난다. (예 - <01>2<0203>2..)
<> 안에 내용이 index 이고 <> 다음에 오는 것이 glyph 라고하는 것의 위치를 지정하는 값인 것 같다. (대충 글자 간격 같은 것인가 보다..)
해당 폰트 리소스에서 해당 글자를 읽어 와야 한다.
해당 폰트 리소스는 PDF 문서내에 다른 object 에 정의되어 있는데 정의 되어 있는 방식이 pdf 버전별로 조금씩 다른 것 같다.
pdf 1.3 에서

44 0 obj
<<
/F1 45 0 R 
/F2 46 0 R 
/F3 47 0 R
>>
endobj

이런식으로 정의되어 있고,
F1 폰트가 45 0 object 에 리소스로 정의 되어 있다고 되어 있고,

45 0 obj
<</BaseFont /BAAAAA+Lato-Light /FirstChar 0 /FontDescriptor 56 0 R
  /LastChar 44 /Subtype /TrueType /ToUnicode 57 0 R /Type /Font /Widths
  [512 579 550 222 425 271 578 760 564 258 510 521 550 353 484 342 551
  340 558 805 506 551 791 842 471 580 233 580 580 580 258 469 755 476
  535 755 655 764 676 607 549 582 240 623 221]>>
endobj

45 object 는 위와 같이 정의 되어 있는데 ToUnicode 항목에 57 0 object 에 리소스로 정의 되어 있다고 표기 되어 있다.

57 0 obj
<</Length 858>>
stream
/CIDInit/ProcSet findresource begin
12 dict begin
begincmap
/CIDSystemInfo<<
/Registry (Adobe)
/Ordering (UCS)
/Supplement 0
>> def
/CMapName/Adobe-Identity-UCS def
/CMapType 2 def
1 begincodespacerange
<00> <FF>
endcodespacerange
44 beginbfchar
<01> <0054>
<02> <0068>
<03> <0069>
<04> <0073>
<05> <0020>
<06> <0050>
<07> <0044>
<08> <0046>
<09> <0028>
<0A> <0067>
<0B> <0065>
<0C> <006E>
<0D> <0072>
<0E> <0061>
<0F> <0074>
<10> <0064>
<11> <0066>
<12> <006F>
<13> <006D>
<14> <004C>
<15> <0062>
<16> <004F>
<17> <006600660069>
<18> <0063>
<19> <0035>
<1A> <002E>
<1B> <0031>
<1C> <0034>
<1D> <0032>
<1E> <0029>
<1F> <0078>
<20> <0048>
<21> <006B>
<22> <0053>
<23> <004E>
<24> <0041>
<25> <0077>
<26> <0043>
<27> <0052>
<28> <0075>
<29> <00740069>
<2A> <003A>
<2B> <0058>
<2C> <006C>
endbfchar
endcmap
CMapName currentdict /CMap defineresource pop
end
end

57 object 에는 index 와 매핍되는 unicode 글자 테이블이 정의 되어 있다.

----
PDF 1.4 에서는

폰트 리소스 정의가 ProcSet /Font 으로 되어 있다.

<< /ProcSet [/PDF /ImageB] 
/Font 
<< 
/F5 6 0 R
/F6 8 0 R
/F7 10 0 R
/F8 12 0 R
>>
/XObject << /Im1 130R
>>
----
PDF 1.7 에서는 /Resources /Font 에 정의 되어 있다.

/Resources
<< /Font << 
/F13 23 0 R
23 0 obj
<< /Type /Font
/Subtype /Type1
/BaseFont /Helvetica >>
endobj
```
2.Text 영역내에 특정문자열(전화번호, 이메일 등) 치환  
3.PDF 로 다시 저장

#### Compiler Compiler
