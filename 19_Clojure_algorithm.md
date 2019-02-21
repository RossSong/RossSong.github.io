### loops
```
user=> (loop [x 10]
  #_=>       (when (> x 1)
  #_=>             (println "hello world!")
  #_=>             (recur (dec x)))
  #_=> )
```
### random generate
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
                               (quick-sort (filter #(> % pivot) coll))
                        )
                  )
)
       
(quick-sort (numbers 100))
```

### binary-tree
```
(defrecord Node [el left right])

(defn insert [{:keys [el left right] :as tree} value]
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

### heapsort
```
(defn- swap [a i j]
  (assoc a i (nth a j) j (nth a i)))

(defn- sift [a pred k l]
  (loop [a a x k y (inc (* 2 k))]
    (if (< (inc (* 2 x)) l)
      (let [ch (if (and (< y (dec l)) (pred (nth a y) (nth a (inc y))))
                 (inc y)
                 y)]
        (if (pred (nth a x) (nth a ch))
          (recur (swap a x ch) ch (inc (* 2 ch)))
          a))
      a)))

(defn heapsort
  ([a pred]
   (let [len (count a)]
     (reduce (fn [c term] (sift (swap c term 0) pred 0 term))
             (reduce (fn [c i] (sift c pred i len))
                     (vec a)
                     (range (dec (int (/ len 2))) -1 -1))
             (range (dec len) 0 -1))))
  ([a]
     (heapsort a <)))
```
