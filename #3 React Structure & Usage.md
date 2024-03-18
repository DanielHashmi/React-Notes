
## 5
### Your src/App.jsx react simple boilerplate code should looks like this when starting to create a new app
```
function App() {

  return (
    <>

    </>
  )
}

export default App
```
## 6
### Your src/index.css should be empty to avoid defualt styling


## 7
### The code rafce generates a simple boilerplate code for react

```
import React from 'react'

const Navbar = () => {
  return (
    <div>Navbar</div>
  )
}

export default Navbar
```

## 8
### You have to type everything inside these blocks inside return block
```
return {

  <>
    your code here...
  </>

}
```
## 9
### You can create components of codes, For Example: you created a NavBar 
```
src/components/Navbar.jsx
```

## 10
### Now you can import it in your App.jsx and use it multiple times
```
import Navbar from "./component/Navbar"


function App() {

  return (
    <>
      <Navbar />
      <Navbar />

    </>
  )
}

export default App
```