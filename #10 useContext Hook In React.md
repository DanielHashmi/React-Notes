
# useContext Hook

## We use useContext Hook to get access to our variable directly in our components 

## FIrst we will create a JavaScript file then we'll import and export createContext inside the javascript file
```
import { createContext } from 'react'
export const contextHook = createContext()
```

## Now we can use it in our App.jsx file we will simply import it inside our App and wrap our component like this
```
 <contextHook.Provider value={ count }>
   <Navbar />
 </contextHook.Provider>
```
### We can access the count variable inside the Navbar component and components it means we have the ease to access our variables directly inside our components without passing them through a hierarchy

## We can use the variables like this
```
import React, { useContext } from 'react'
import { contextHook } from './context'

const Navbar = () => {
    const newContext = useContext(contextHook)
    return (
        <nav>
            navbar{newContext.count}
        </nav>
    )
}

export default Navbar
```

### We can also pass multiple variables inside an object
```
 <contextHook.Provider value={{ count, count2 }}>
   <Navbar />
 </contextHook.Provider>
```
### And can use them like this

```
import React, { useContext } from 'react'
import { contextHook } from './context'

const Navbar = () => {
    const newContext = useContext(contextHook)
    return (
        <nav>
            navbar{newContext.count}
            navbar2{newContext.count2}
        </nav>
    )
}

export default Navbar
```
