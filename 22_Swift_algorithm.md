### quick sort
```
func quicksort(_ xs: [Int]) -> [Int]  {
        guard 0 < xs.count else { return [] }
        let pivot = xs[0]
        return quicksort(xs.filter({$0 < pivot})) + [pivot] + quicksort(xs.filter({$0 > pivot}))
    }

quicksort([4,9,3,1,5])
```
