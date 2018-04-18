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

다음과 같은 json 이 return 된다.

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

