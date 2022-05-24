---
title: Functional Programming in Plain Terms
author: Eric Weinstein
twitter: ericqweinstein
---

TL;DPA
- Pure functions and immutable ds make reasoning about our programs easier
- Functors, monoids, and monads are just ways to solve our everyday programming problems
- Good type systems are amazing tools - try them out!
---

Wrote Ruby Wizardry

Dynamic Programming = _programming with a cache_

**What is this for**


**Pure Functions**
- Can be safely memoized: The same inputs will have the same outputs
- Side effects are anything that's not a return value from a function. (I/O, state mutation, etc.)
- Immutability makes your program easier to reason because you're getting a new value rather than updating an existing one

**Types**

```haskel
add :: Integer -> Integer -> Integer
add x y = x + y


-- The real version of head throws
-- an error of an empty list; this
-- fanciful version uses 'Maybe'.

-- Type that contains another type
head :: [a] -> Maybe a
head [] = Nothing
head (x:__) Just x
```

**Algebraic Data Types
- Types made up of other types
- They come in two "flavros" :sum types(think of these as enum-like) and products types (think of hash-like)

**functor**
`{:functor => :mappable}`  




**Pros/Cons**
- Benefits of mutating 

**Books**
- Type Driven Development