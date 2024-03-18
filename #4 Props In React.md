## 11 
### You can pass values to Navbar.jsx file, For Example: hold="" logo=""
```
import Navbar from "./component/Navbar"


function App() {

  return (
    <>
      <Navbar hold="Enter Your Name" logo="DH" />
      <Navbar hold="Search Something" logo="Daniel" />

    </>
  )
}

export default App
```
## 12
### Now you can get values in a variables in the Navbar function in Navbar.jsx file, For Example: props
```
import React from 'react'

const Navbar = (props) => {
    return (
        <nav className='main'>
            <div className='logo'>DH</div>
            <div className='inpSec'>
                <input type="text" placeholder="Search" />
            </div>
        </nav>
    )
}

export default Navbar
```

## 13
### Now you can use them everywhere you want, For Example: {props.hold} {props.logo}

```
import React from 'react'
import "./Navbar.css"
const Navbar = (props) => {
    return (
        <nav className='main'>
            <div className='logo'>{props.logo}</div>
            <div className='inpSec'>
                <input type="text" placeholder={props.hold} />
            </div>
        </nav>
    )
}

export default Navbar
```