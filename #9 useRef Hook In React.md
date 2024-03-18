
## 19
# useRef Hook

### Why useRef: In react we have a problem that everything re renders when a state changes For Example: We create a button and when we click on it variable num increases by one but in react we can't do it directly because it will refresh it again to zero than it will be updated! again it will be zero...because react re renders everything

```
import { useState, useEffect } from "react"

function App() {
  const [count, setCount] = useState(0)
  let num = 0
  useEffect(() => {
    num = num + 1
    console.log(num) // Output 1 never changes
  })
  return (
    <>
      <button onClick={() => { setCount(count + 1) }}>Click Me</button>
    </>
  )
}

export default App

console.log(a)
```
This code never increase num one by one it remains 1 always


# That's why we use useRef
## This is how useRef code looks like
```
const num = useRef(0)
```
## Now we use this variable like this
```
num.current
```
This works fine
```
import { useState, useEffect, useRef } from "react"

function App() {
  const [count, setCount] = useState(0)
  let num = useRef(0)
  useEffect(() => {
    num.current = num.current + 1
    console.log(num.current)
  })
  return (
    <>
      <button onClick={() => { setCount(count + 1) }}>Click Me</button>
    </>
  )
}

export default App
```
## Now if we change the num variable react do not re render and useEffect will not be triggered still if we change something else react will re render everything except the num variable so the num variable persists and useEffect will be triggered

## We can also use useRef like this
```
let ref = useRef(0)

ref.current.style.backgroundColor = "red"

<button ref={ref}>Click Me</button> // The button will be red
```
### The full code looks likes this
```
import { useEffect, useRef } from "react"

function App() {

  let ref = useRef()
  
  useEffect(() => {
    ref.current.style.backgroundColor = "red"
  })
  return (
    <>
      <button ref={ref}>Click Me</button>
    </>
  )
}

export default App
```
We cannot use it without useEffect

# Difference betweent useRef, useState, Normal variable

- <b>Normal variable:</b> Normal variable will be re initialized when rerendering it means we can't update it because its value can't survive rerendering

- <b>useState:</b> useState survives rerendering and it will update the updated value automatically when a certain value changes

- <b>useRef:</b> useRef also survives rerendering but it cannot automatically update the values, it acts like a Normal variable in normal javascript
