
# useMemo Hook

## Why we use useMemo Hook
- Just because react rerenders whenever a State changes thats why we use useMemo Hook 
- If we are doing a huge computing in a function when a state changes react rerenders so the function starts computing again it means whenever a state changes the function starts from start again and again and our app becomes slow and hangy 
## What useMemo Hook does 
- It Memoizes/Saves the results by caching them to avoid redundant computations and return them when same input occurs again and again
so when react rerenders it does not computes again because its saved.

- It also has a dependency array to tell it when to compute when react renders For Example we can tell it that you should recompute when the computation changes

## We use it like this

### Import it

```
import { useMemo } from "react"
```

### To save the results in memory we use useMemo() Hook
```
const isMagicalNum = useMemo(() => numbers.find(item => item.isMagical === true), [numbers])
```
### Now it only recomputes when the array [numbers] changes otherwise it uses the previous results again and again

## This is an Example

```
import { useMemo, useState } from "react"
const nums = new Array(30_000_000).fill(0).map((_, i) => {
  return {
    index: i,
    isMagical: i === 29_000_000
  }
})

function App() {
  const [count, setCount] = useState(0)
  const [numbers, setNumbers] = useState(nums)
  const magical = useMemo(() => numbers.find(item => item.isMagical === true), [numbers])
  console.log("hello")
  return (
    <>
      <h1>The magical number is {magical.index} and count is {count}</h1>
      <button onClick={() => {
        setCount((count) => count + 1);
        if (count === 10) {
          setNumbers(new Array(30_000_000).fill(0).map((_, i) => {
            return {
              index: i,
              isMagical: i === 28_000_000
            }
          }))
        }
      }}>Click Me</button>
    </>
  )
}

export default App
```

