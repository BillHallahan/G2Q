## G2Q
---
#### About
G2Q allows constraint programming, via writing Haskell predicates.
A quasiquoter, g2, is provided which can take concrete arguments at runtime, and solve for unknown symbolic arguments.

For example, to find inputs from a list xs which sum to a given number n, you can write:
```hs
sumToN :: Int -> [Int] -> IO (Maybe [Int])
sumToN = [g2| \(n :: Int) (xs :: [Int]) -> ?(ys :: [Int])
            |  sum ys == n
            && all (\e -> e `elem` xs) ys
            && length ys >= 1 |]
```