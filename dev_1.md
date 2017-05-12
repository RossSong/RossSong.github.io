# Snapchat, Snow 짝퉁 개발기

이글은 [Snapchat](https://itunes.apple.com/kr/app/snapchat/id447188370?mt=8), [Snow](https://itunes.apple.com/kr/app/snow-selfie-motion-sticker-fun-camera/id1022267439?mt=8) 등에 얼굴을 인식하여 꾸미거나 변형시키는 기능을 가지는 장난감 iOS 앱을 만들어 본 경험에 대한 공유 글입니다.  
이 앱은 OpenFramework(v0.9.8_ios_release) 과 OpenCV 를 이용하여 만들어 졌습니다.  
이 앱의 소스는 [github](https://github.com/RossSong/imitationSnow/blob/master/README.md) 에 있습니다.

<div>
<image width=200 height=300 src="https://github.com/RossSong/RossSong.github.io/blob/master/result.gif?raw=true"/>
<image width=200 height=300 src="https://github.com/RossSong/RossSong.github.io/blob/master/thumb_1.jpg?raw=true"/>
<image width=200 height=300 src="https://github.com/RossSong/RossSong.github.io/blob/master/thumb_2.jpg?raw=true"/>
<image width=200 height=300 src="https://github.com/RossSong/RossSong.github.io/blob/master/thumb_3.jpg?raw=true"/>
</div>

## FaceTracker 발견!

작년(2016) 쯤에 Snapchat(무지개 토!),  [MSQRD](https://itunes.apple.com/us/app/msqrd-live-filters-face-swap-for-video-selfies/id1065249424?mt=8) 그리고 곧이어 Snow 등의 앱이 나와서 인기를 끌기 시작했습니다. 사람들이 참 재미있어 했습니다.

대학교 시절에 이미지 프로세싱을 조금 접해 봤었던 입장에서 보니 한번 만들어 보면 재미 있겠다는 생각을 하게 되었습니다.
그래서 구글링을 잠깐 해보니 Face Tracking 기술들이 많이 발전되었고, 오픈 소스로 많이 공개되어 있었습니다.
[openCV](http://opencv.org)에 Object Detecting 기술 자체가 포함되어 있었고,
여러 플랫폼에서 좀더 쉽게 멀티미디어 처리를 쉽게 해주는 [openFrameworks](https://www.google.co.kr/#q=openframeworks) 라는 것도 알게 되었습니다. OpeCV를 이용해서 동영상에서 얼굴을 찾고 그 얼굴의 Face Mesh 까지 생성해주는 [FaceTracker](https://github.com/kylemcdonald/FaceTracker) 라는 것도 있었습니다.

FaceTracker 은 OpenCV 의 Object Detecting 기술을 이용해서 얼굴, 눈, 코, 입을 찾고 찾은 점들을 이용해서 얼굴 면(Face Mesh)을 생성하는 기능을 제공합니다. OpenFrameworks의 [addon](http://ofxaddons.com/categories) 으로 사용될 수 있는 [ofxFaceTracker](https://github.com/kylemcdonald/ofxFaceTracker) 도 있습니다.
OpenFrameworks 를 함께 사용하면 비디오 처리라던지, Face Mesh 대한 텍스쳐링을 좀 더 손쉽게 할 수 있습니다.
(단점은 OpenFrameworks도 배워야 한다는 점이죠..;;;)

하여튼, 구글 신님의 도움으로 쉽게 자료를 찾을 수 있었습니다. 그래서 한번 도전해보기로 했습니다.

## 초반 대삽질!!

일단 iOS 용 앱으로 만들려고 했기 때문에, Readme에 있는 내용대로 [ofxFaceTracker-iOS](https://github.com/kylemcdonald/ofxFaceTracker-iOS) 를 다운 받아서 돌려보기 시작했습니다.
ofxFaceTracker-iOS 를 사용하려면, [iOS 용 OpenFrameworks](http://openframeworks.cc/versions/v0.9.8/of_v0.9.8_ios_release.zip)를 일단 받아서 압축을 풀고, 하위 폴더 중에 apps/myApps 아래에 ofxFaceTracker-iOS 를 폴더를 넣고 xcode 프로젝트를 열어서 실행해줘야 합니다.
app/myApps 경로는 OpenFrameworks 프로젝트를 새로 생성하면 프로젝트가 생성되는 경로입니다.

아래의 그림처럼 얼굴을 찾고 Face Model 까지는 잘 찾아주기는 합니다.

<image width=200 src="https://github.com/RossSong/RossSong.github.io/blob/master/thumb_4.jpg?raw=true"/>

일단 되는 것은 확인했는데, 이 소스가 일반적인 iOS 앱 개발에 사용되는 Objective-C 나 Swift 형태가 아닌 전체가 C/C++ 소스로 되어 있습니다. 그리고 OpenFrameworks 을 사용하고 있어서, 찾은 Face Model에 어떻게 텍스쳐링 입힐지, 스티커 사진등을 선택할 수 있는 UI는 어떻게 연결시켜야 할지 막막했습니다.

그래서 일단 무식하게 도전했습니다. 일단 OpenFrameworks를 잘 모르는 상태였기 때문에, ofxFaceTracker-iOS 를 온전히 사용할 수 없다고 판단 했습니다. 그래서 ofxFaceTracker-iOS 를 분석해서 일단 FaceTracker과 ofxFaceTracker에서 사용되는 점과 Mesh 들에 대해서 처리하는 부분들을 OpenFrameworks 에서 적당히 잘라서 뜯어냈습니다.(OpenFrameworks 내부 컴포넌트들이 서로 많이 엉켜붙어 있어서, 쉽고 깔끔하게 떼어내기가 불가능했습니다. 결합도가 너무 강한.. ㅡㅜ. 우여곡절 끝에 어찌어찌 동작할 정도로 뜯어냈습니다.)

그리고 뜯어낸 코드들을 일반적인 Objective-C 를 이용한 viewController 처리 코드들과 결합하고, Drawing하는 부분들을 OpenFrameworks 가 아닌 직접 imageView 에 그리고, Face Mesh 관련해서는 GLKit의 GLKView 에 OpenGL 로 직접 필요한 부분만 그리도록 했습니다. 이렇게 하니 viewController 를 통해서 쉽게 UI 컴포넌트를 들을 처리하고, FaceTracker에서 얻어지는 Face Mesh를 일단(!!) 그릴 수 있게 되었습니다. 하지만 Face Mesh 를 그릴 때 imageView에 그려지는 얼굴과 Face Mesh의 좌표가 틀어지는 문제들이 발생하기 시작했습니다. OpenFrameworks이 설정하는 좌표계와 기본 OpenGL 좌표계가 달랐던 것입니다.

그래서 다시 삽질을 하여, 좌표를 비슷하게 맞추긴 했는데... ofxFaceTracker를 온전히 사용할 때 처럼 매끄럽게 얼굴과 Face Mesh가 매칭이
처리되지 않는 것 같았습니다. ㅡㅜ (그리고 뭔가 이건 아니다 싶은 생각이 많이 났지요.. ㅡㅜ)

## OpenFrameworks 구조와 사용법 파악!!

그래서 다시 구글링을 시작했습니다. 그렇게 해서, OpenFrameworks project generator(OpenFrameworks를 쉽게 사용할 수 있도록 프로젝트 생성을 도와 주는 툴)를 이용하는 방법과 OpenFrameworks와 viewController들을 어떻게 연결시켜야 하는지는 알게 되었습니다.
(앞에서 했던 대삽질들은 OpenFrameworks 구조와 사용법을 이해하는데 도움이 많이 되었습니다. 전화위복이라고 할까요... ㅡㅜ)

그런데 viewController 를 이용해서 UI 를 연결시키는 것을 해결하고 나니, OpenFrameworks을 통해서 그려지던 Face Model과 비디오 영상들을 어떻게 불러와서 viewController 위에 그려줘야 할지 다시 막막해졌습니다.

OpenFrameworks 는 기본적으로 모든 Drawing을 OpenGL을 통해서 하게 되어 있었습니다. 유니티처럼 OpenGL을 그릴 수 있는 컨테이너에 해당하는 window를 하나 올려 놓고 그 위에 OpenGL로 모든 걸 다 그리고도록 되어 있었습니다. 그래서 그 위에 viewController 를 올려 버리니 다시 그려지던 화면을 볼 수 없게 된 것은 당연한 것이었지요.

그래서 OpenGL로 그려지는 화면을 가져와서 viewController 위에 다시 그려줄 방법을 찾기 위해서, 다시 구글링을 하게 되었습니다.
저랑 비슷한 질문을 하는 글들은 발견했지만, 해결 책에 대한 답변을 거의 찾을 수 없었습니다.

## 다시 삽질!! 삽질!!

처음 삽질하면서 GLKView 로 OpenGL 처리를 직접하는 방식으로 실험을 하면서, EAGLContext 것을 GLKView 에 설정해준다는 것을 알게 되었습니다. OpenGL로 화면을 그릴 때는 일반적으로 viewController 처리할 때와는 다른 비디오 메모리를 사용하는 것으로 보였습니다.
viewController 위로 다른 모듈에서 OpenGL 로 그리는 그림을 가져올려면 어떻게 해야할까 고민하다보니, 일단 두가지가 비디오 메모리 영역이 다르다는 것을 어렴풋이 파악하게 되었고, OpenGL 로 그리는 영역과 일반 viewController로 그리는 영역을 연결 시킬려면, 직접 그릴 때처럼 EAGLContext 를 어떻게 잘 연결해주면 되지 않을까 하는 생각이 스쳐 지나 갔습니다.

보통 GLKView 를 초기화 해줄때, EAGLContext 를 하나 새로 생성하고 그것을 currrentContext 로 설정하는 과정을 거치는데,
OpenFrameworks 에서는 OpenGL 을 이용한 drawing 방식을 쓰고 있기 때문에, 아마도 OpenFrameworks 생성한 EAGLContext 를 currrentContext 로 설정해서 쓰고 있을 것이라는 추측이 들었습니다.

그래서 그 currentContext 를 현재 나의 viewController 위에 있는 GLKView 로 연결 시키면 되지 않을까라는 결론에 도달했습니다.
그래서 GLKView 를 초기화 할때 새로 생성하지 않고, currentContext 를 GLKView 의 currentContext 로 연결하였습니다.
짜짠!! 그랬더니 원하는 대로, viewController 위에 OpenFrameworks가 그리는 영상이 아름답게! 그려지기 시작했습니다. ㅡㅜ

## 이제는 텍스쳐링!! 얼굴합성!!

이제는 그려지고 있는 Face Mesh 위에 합성할 얼굴에서 가져오 텍스쳐를 맵핑시켜서 그려야 했습니다.
이것도 조금 막막했습니다. 그래서 일단 구글링..(구글신은 모든 것을 알고 계신다!)
[TBFaceMorpherPhoto](https://github.com/terrybu/TBFaceMorpherPhoto)라는 프로젝트를 발견했습니다.
(대학시절에 공부했던 이미지 프로세싱에서 배운 morphing, warping 같은 키워드 단어들을 알고 있는 것이 구글 검색에 도움이 많이 되었습니다.)
TBFaceMorpherPhoto 는 선택된 이미지를 쉐이더를 이용해서 합성하고 그것을 텍스쳐 매핑해주는 기능를 제공하고 있었습니다.
그래서 TBFaceMorpherPhoto 를 분석하여 필요한 기능을 가져와서 붙였습니다. Clone 이라는 모듈이 얼굴 이미지 합성을 담당하고 있었습니다.

그렇게 얼굴 합성해서 매핑하는 기능을 추가했습니다.
이제 재미있는 얼굴 합성 기능이 완성되었습니다.
그런데 따로 저장되거나 불러오는 기능이 없는 것이 아쉬웠습니다.

## 동영상!

그래서 GLKView 영역에 그려지고 있는 부분을 캡쳐를 해서 동영상으로 만드는 기능을 추가 했습니다.
기능을 추가하면서 구글링을 통해 StackOverflow에서 발견한 방법들을 따라하다보니 영상이 밀려서 깨지는 오류가 발생했습니다.
영상이 왜 밀리는지 분석하는데 삽질을 좀 하긴 했지만..
저장될 이미지의 폭과 높이에 맞춰서 bytePerRow 를 계산해서 지정했지만, 실제로 CVPixelBufferRef 에 설정되는 값은 지정한 값과 달라져서
CVPixelBufferGetBytesPerRow 로 읽어 들인 값을 다시 써줘야 한다는 정도의 주의사항을 알게 되었습니다.
추가로 iOS9 이상에서 PHPhotoLibrary 사용해서 동영상 저장시에 앱에서 직접 생성한 이미지 폴더(collection)이 아니면 저장이 안되고 오류가 발생한다는 예외 사항도 있기는 했습니다.
이제 얼굴을 인식하여 합성한 영상들이 동영상으로 저장이 되게 되었습니다.

## 기타

기타로 동영상을 불러와서 처리하는 기능, 전/후면 카메라 전환, 합성할 얼굴 선택을 위한 CollecitonView 추가, 안내 ToolTip 추가 등의 작업이 이루어졌습니다. 얼굴 합성보다는 그냥 얼굴이미지를 바꿔치기 하는 것이 더 깔끔해 보여서 합성하는 것은 동영상을 불러온 것을 처리할 때만 쓰도록 수정하였습니다.

이렇게 해서 1단계 Snow 짝퉁 개발이 완료되었습니다.

## 개선할 점!!

만들면서 테스트하다 보니, Snow의 우수한 점들이 눈에 보입니다. 다른 앱들과 비교해서 확실히 얼굴 인식률이 좋습니다. 기본으로 제공되는 OpenCV의 haar cascade 데이터는 얼굴 정면 이미지들로만 학습이 되어 있고, 같은 정면 얼굴이라도 빛 산란 정도에 따라서 인식률이 왔다 갔다는 하는 현상을 보이는데, 비슷한 기능을 제공하는 snow는 전반적으로 인식률이 훨씬 좋았습니다. [b612](https://itunes.apple.com/us/app/b612-trendy-filters-selfiegenic-camera/id904209370?mt=8) 라는 앱도 있는데, b612는 Line에서 만들고, snow는 CampMobile에서 만든 것이라, 네이버 계열사들이라 같은 엔진을 사용하지 않을까 하는 생각을 해봅니다.
(아닐 수도 있구요..)
snow 나 b612는 harr cascade 가 아닌 요즘 유행하는 TensorFlow 를 이용해서 기계학습시킨 모델을 따로 사용하고 있을 수도 있다는 생각도 듭니다. TensorFlow 를 이용해서 다시 만들어 보면 더 재미있을 것 같기도 합니다. ^^;;

대충 재미로 실험으로 되는 지만 볼려고 만들다 보니.. 소스가 Massive View Controller가 되어 버렸습니다.
다시 만들게 되면 테스트 코드도 넣고, 모듈 별로 분리하고 좀 더 아름다운 설계로 만들고 싶네요.. ㅡㅜ

## 기계학습??

인식률이 떨어진다고 실망하지 않아도 됩니다. OpenCV 에는 [harr cascade](http://wearables.cc.gatech.edu/paper_of_week/viola01rapid.pdf) 방식으로 이미 기계학습 된 데이터를 제공할 뿐만 아니라, 직접 학습시킬 수 있는 툴도 같이 제공하고 있습니다.
OpenvCV2 까지는 (opencv_)harrtraining 이라는 툴이 제공되고, OpenCV2, OpenCV2 (opencv_)traincascade 라는 툴이 함께 제공됩니다. harrtraining 은 학습시키는데 시간이 많이 걸리는데, traincascade 는 병렬 방식으로 개선되어 학습시간이 개선 되었습니다.
두 툴에서 만들어지는 학습된 모델 xml 파일의 형식이 달라서 호환이 안되는 것 같긴합니다.(제가 잘 몰라서 그럴 수도 있겠네요..)

학습 관련 정보  
[http://darkpgmr.tistory.com/70](http://darkpgmr.tistory.com/70)  
[http://docs.opencv.org/2.4/doc/user_guide/ug_traincascade.html](http://docs.opencv.org/2.4/doc/user_guide/ug_traincascade.html)  
[http://note.sonots.com/SciSoftware/haartraining.html](http://note.sonots.com/SciSoftware/haartraining.html)  

인식률을 높이기 위해서 학습 관련해서 조금씩 실험을 하고 있습니다만, 성능이 조금 떨어지는 낡은(?) 기기와 샘플데이터를 직접 만들어야 하는
노가다등으로 인해 개선하려면 시간이 좀 더 필요할 것으로 보입니다.

snow 에서 처럼 토끼 귀, 안경, 얼굴 축소 같은 것은 찾은 face Mesh를 기준으로 좌표를 계산하고, 귀등의 3D Mesh를 추가하면
가능할 겁니다. (이런 것들은 디자인(?)의 영역으로... 쿨럭..)

대선 기간 동안에 쉬면서 재미로 만들어 볼려고 시작했는데, 역시나.. 아무리 간단해 보여도 직접해보면 어려움이 있다는 것을
다시 한번 느끼게 해주는 프로젝트 였습니다. ㅡㅜ

이 글을 읽어 주셔서 감사합니다.
