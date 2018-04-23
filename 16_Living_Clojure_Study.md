# Living Clojure Study

## Chapter 7. Creating Web Applications With Clojure

```
lein new compojure cheshire-cat

lein ring server
```

http://localhost:3000 접속 -> "Hello World" 페이지 완성   

project.clj 에서 다음 부분이 확인

```
:plugins [[lein-ring "0.9.7"]]

:ring {:handler cheshire-cat.handler/app}
```

ring-server 를 plugin 으로 사용하고,   
ring-server 에서 src/cheshire_cat/handler.clj 의 app 함수를 실행   

src/cheshire_cat/handler.clj 에 defroutes app-routes 에 아래 코드 추가
```
(GET "/cheshire-cat" [] "Smile!")
```

http://localhost:3000/cheshire-cat 접속 -> "Smile!" 페이지 완성

#### Cheshire Library 와 Ring 으로 JSON 사용하기

project.clj :dependencies 에 [cheshire "5.4.0"] 추가  

src/cheshire_cat/handler.clj :require 에 [cheshire.core :as json] 을 추가   

(GET "/cheshire-cat" [] 을 아래의 내용으로 변경   
```
(GET "/cheshire-cat" []
       {:status 200
        :headers {"Content-Type" "application/json; charset=utf-8"}
        :body (json/generate-string
               {:name "Cheshire cat"
                :status :grinning})})
```
서버 다시 시작
lein ring server

```
curl -i http://localhost:3000/cheshire-cat
```

다음과 같은 JSON 이 return 된다.

```
HTTP/1.1 200 OK
Date: Wed, 18 Apr 2018 03:25:26 GMT
Set-Cookie: ring-session=8a05f03c-4ee8-452f-820d-92a8582f05d6;Path=/;HttpOnly
X-XSS-Protection: 1; mode=block
X-Frame-Options: SAMEORIGIN
X-Content-Type-Options: nosniff
Content-Type: application/json; charset=utf-8
Content-Length: 43
Server: Jetty(7.6.13.v20130916)

{"name":"Cheshire cat","status":"grinning"}
```

### Ring-JSON 으로 JSON 을 리턴하는 Rest API 만들기

Cheshire Library 를 이용하면 JSON 처리를 할 수 있지만, http response status header body 등을 수작업으로 만들어 줘야 하는데, Ring-JSON 을 사용하면 쉽게 만들 수 있다.   

project.clj 파일에서 Cheshire 를 제거하고, Ring-JSON 을 추가한다.   
```
[ring/ring-json "0.3.1"]
```
src/cheshire_cat/handler.clj 에서 ring-json 과 response 에 대한 라이브러리 참조를 추가한다.   
```
[ring.middle.json :as ring-json]
[ring.util.response :as rr]
```
cheshire-cat 에 대한 response 를 다음과 같이 수정한다.
```
(GET "/cheshire-cat" []
    (rr/response {:name "Chesire Cat" :status :grining}))
```   

그리고 def app 을 다음과 같이 수정한다.
```
(def app
    (-> app-routes
        (wrap-defaults site-defaults)
        (ring-json/wrap-json-response)))
```

서버를 다시 실행시키고, "/cheshire-cat"을 다시 요청해 본다.
```
lein ring server
curl -i http://localhost:3000/cheshire-cat"
```
아래와 같은 response 를 수신한다.
```
HTTP/1.1 200 OK
Date: Mon, 23 Apr 2018 03:16:21 GMT
Set-Cookie: ring-session=1e7442c6-d676-437e-973e-6b05eb9c4687;Path=/;HttpOnly
X-XSS-Protection: 1; mode=block
X-Frame-Options: SAMEORIGIN
X-Content-Type-Options: nosniff
Content-Type: application/json; charset=utf-8
Content-Length: 42
Server: Jetty(7.6.13.v20130916)

{"name":"Cheshire Cat","status":"grining"}
```
