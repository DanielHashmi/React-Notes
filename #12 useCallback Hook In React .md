# useCallback Hook
## useCallback Hook works same as useMemo Hook, the only defference is that the useMemo Hook Memoizes the results and the useCallback Memoizes the whole function itself and returns a Memoize version of that function

## We use it like this

### Import it

```
import { useCallback } from "react"
```

### To freaze a function in memory we use useCallback() Hook
```
const hello = useCallback(() => {
  return "hello"
}, [anything])
```
### Now it only recomputes when the array [anything] changes otherwise it uses the previous results again and again

## This is an Example

```
import Navbar from "./component/Navbar"
import { useCallback, useState } from "react"

function App() {
  const [count, setCount] = useState(0)
  const [adj, setAdj] = useState("good")
  console.log(count)
  const hello = useCallback(() => {
    return "hello"
  }, [])

  return (
    <>
      <Navbar adj={adj} hello={hello} />
      <button onClick={() => setCount(count + 1)}>Count</button>
    </>
  )
}

export default App
```

