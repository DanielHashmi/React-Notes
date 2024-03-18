## 14
### To style you can create a CSS file inside components folder, For Example src/components/Navbar.css

Now you add styling in the css file

## 15
### You have to import css file in your component file, For Example: The styling is for the Navbar you have to import it in the Navbar file
```
import "./Navbar.css"
```
The styling will be applied automatically 
## 16
### You can use inline css using {{...inline css here...}}
```
style={{ color: "red" }}
```
You should use inline css in your component For Example: src/components/Navbar.jsx

```
import React from 'react'
import "./Navbar.css"
const Navbar = (props) => {
    return (
        <nav className='main'>
         <div style={{ color: "red" }} className='logo'>{props.logo}
        </div>
        </nav>
    )
}

export default Navbar