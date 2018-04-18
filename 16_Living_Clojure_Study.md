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
