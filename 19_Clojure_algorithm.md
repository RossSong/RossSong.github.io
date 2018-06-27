
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
