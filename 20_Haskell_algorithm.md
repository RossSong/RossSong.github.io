### loops
```
Prelude> :{
Prelude| repeatNTimes 0 _ = return ()
Prelude| repeatNTimes n action =
Prelude|   do
Prelude|     action
Prelude|     repeatNTimes (n-1) action
Prelude| :}

repeatNTimes 10 (putStrLn "hello word")
```

### add
```
add :: Integer -> Integer -> Integer; add x y = x + y  
let ret = add 1 2  
print ret
3
```
```
 (\x y -> x + y ) 3 5
 8
```

### bubble-sort
```
doit []  = []
doit [x] = [x]
doit (x:xs) | x > head xs = head xs:doit (x:tail xs)
             | otherwise = x:doit xs
bubbleSort xs = foldl (\acc e -> doit acc) xs xs
bubbleSort [5, 3, 4, 6, 1, 2]
```

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

### BinaryTree
```
data BinaryTree a = EmptyTree | Node a (BinaryTree a) (BinaryTree a)
     deriving (Show)

treeInsert :: Ord a => a -> BinaryTree a -> BinaryTree a
treeInsert el EmptyTree = Node el EmptyTree EmptyTree
treeInsert el (Node a left right)
       | el == a = Node el left right
       | el < a = Node a (treeInsert el left) right
       | el > a = Node a left (treeInsert el right)
       
let aaa = treeInsert 1 EmptyTree
let bbb = treeInsert 2 aaa
let ccc = treeInsert 3 bbb
```
