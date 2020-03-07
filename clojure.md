```
(defn main []
     (println "What's your name?")
     (let [your_name (read-line)]
          (println (str "Hey " your_name ", you rock!"))))

(defn main2 []
       (println "What's your name?")
       (def _name (read-line))
       (println (str "Hey " _name ", you rock!")))
```
