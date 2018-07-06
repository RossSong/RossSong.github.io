
### rnadom generate
```
(defn numbers [n] (take n (repeatedly #(rand-int 100))))
```
### bubble sort

```
(defn bubble [ys x]
      (if-let [y (peek ys)]
              (if (< x y)
                    (conj (pop ys) x y)
                    (conj ys x)
              )
              [x]))
              
(defn bubble-sort [xs]
      (if-let [ys (reduce bubble [] xs)]
              (if (= ys xs)
                  xs
                  (recur ys))))
                  
(bubble-sort (numbers 100))
```
### quick-sort
```
(defn quick-sort [[pivot & coll]]
                 (when pivot
                       (concat (quick-sort (filter #(< % pivot) coll))
                               [pivot]
                               (quick-sort (filter #(>= % pivot) coll))
                        )
                  )
)
       
(quick-sort (numbers 100))
```

### binary-tree
```
(defrecord Node [el left right])

(defn insert [:{keys [el left right] :as tree} value]
      (cond
        (nil? tree) (Node. value nil nil)
        (> el value) (Node. el (insert left value) right)
        (< el value) (Node. el left (insert right value))
        :else tree))
        
(def to-tree #(reduce insert nil %))
(def tree (to-tree '(6 5 8 3))) 

tree
#user.Node{:el 6, :left #user.Node{:el 5, :left #user.Node{:el 3, :left nil, :right nil}, :right nil}, :right #user.Node{:el 8, :left nil, :right nil}}
```
