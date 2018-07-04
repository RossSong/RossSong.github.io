### bubble-sort
```
bubbleSort :: (Ord a) => [a] -> [a]
bubbleSort [] = []
bubbleSort [x] = [x]
bubbleSort (x:y:xs) = if sorted thisSort then thisSort else bubbleSort thisSort
    where thisSort = (min x y) : bubbleSort ((max x y):xs)

sorted :: (Ord a) => [a] -> Bool
sorted [] = True
sorted [x] = True
sorted (x:y:xs) = if x <= y then sorted (y:xs) else False

main = do
    let ret = bubbleSort [6, 5, 3, 1, 8, 7, 2, 4] :: [Integer]
    print ret
```
### quick-sort
```
quicksort [] = []
quicksort (x:xs) = quicksort small ++ (x: quicksort large)
    where small = [y | y <- xs, y <= x]
          large = [y | y <- xs, y > x]

main = do
    let ret = quicksort [10,2,5,3,1,6,7,4,2,3,4,8,9]
    print ret
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
