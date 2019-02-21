### loops
```
iex(2)> defmodule Loop do
...(2)>     def print_multiple_times(msg, n) when n <= 1 do
...(2)>         IO.puts msg
...(2)>     end
...(2)>     def print_multiple_times(msg, n) do
...(2)>         IO.puts msg
...(2)>         print_multiple_times(msg, n - 1)
...(2)>     end
...(2)> end
iex(3)> Loop.print_multiple_times("Hello", 10)
```
