## 17
# UseState Hook
## We use useState hook to avoid DOM Manipulation system
### To use useState we have to import it from react

```
import { useState } from "react"
```

## We can use it like this
```
 const [count, setCount] = useState(0)
 ```
 Remember to use it directly in the function not inside return block

```
function App() {

  const [count, setCount] = useState(0)

  return (
    <>
    </>
  )
}
```

## What this code means 

## const [count, setCount] = useState(0)

- ### const is a JavaScript variable
- ### count is the value
- ### setCount is a function that allows us to change the value
- ### = is the assignment operator
- ### useState is a function that returns two things
- #### the value
- #### and a method that has the ability to change the value
- ### 0 is the initial value that we can give as an argument

## The benefit of useState is For Example: We have a variable that has initial value 5 we printed it and the value was 5 now we update the value to 10 we already printed it but still it will print 5 because we didn't printed it again after updating it
```
let value = 5;
console.log(value) // Output 5
value = 5
console.log(value) // we have to print it again
```

## But in react hook useState if we update it ones it will be updated automatically everywhere it is being used
```
  const [count, setCount] = useState(5)
  console.log(count) // Output 5 after updating Output 10
  let a = count
  console.log(a) // Output 5 after updating Output 10

  setCount(() => count = 10) // as we update it the output will show the updated value
 ```
 Always remember to import useState from react

