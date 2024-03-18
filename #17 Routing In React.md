# 24
# Routing In React

## We use routing to avoid reloading our page when changing pages

# Installation of React Router DOM

Install by running this code
```
npm i react-router-dom
```

## Now import createBrowserRouter, RouterProvider and Link from React Router DOM in your App
```
import { createBrowserRouter, RouterProvider, Link } from 'react-router-dom'
```
## Create a new router
```
const Router = createBrowserRouter()
```

## Now you can use it like this
#### We can go to the pages like this


```
function App() {
  const Router = createBrowserRouter([
    {
      path: '/',
      element:<> <Navbar /> <Home /> </>
    },
    {
      path: '/about',
      element:<> <Navbar /> <About /> </>
    },
    {
      path: '/contact',
      element:<> <Navbar /> <Contact /> </>
    }
  ])
  return (
    <>
      <RouterProvider router={Router} />
    </>
  )
}

export default App
```

### Now we need RouterProvider
#### To use RouterProvider we have to add it where ever we want to use our components

### For Example
```
function App() {
  const Router = createBrowserRouter([
    {
      path: '/',
      element:<> <Navbar /> <Home /> </>
    },
    {
      path: '/about',
      element:<> <Navbar /> <About /> </>
    },
    {
      path: '/contact',
      element:<> <Navbar /> <Contact /> </>
    }
  ])
  return (
    <>
      <RouterProvider router={Router} />
    </>
  )
}

export default App
```

## Now you can create a simple Navbar with buttons home, about, contact and we should use { Link } instead of a/anchor and { to } instead of href
### For Example

```
import React from 'react'
import { Link } from 'react-router-dom'

const Navbar = () => {
    return (
        <nav>
            <Link to="/">Home</Link>

            <Link to="/about">About</Link>

            <Link to="/contact">Contact</Link>
        </nav>
    )
}

export default Navbar

```

## And create the components Home.jsx, About.jsx, Contact.jsx inside components to keep the example simple

#### Just create home and about like this

```
import React from 'react'

const Contact = () => {
  return (
    <div>Contact</div>
  )
}

export default Contact
```

## Now your App.jsx looks like this 

```
import { useState } from "react"
import Navbar from "./component/Navbar"
import { createBrowserRouter, RouterProvider } from 'react-router-dom'
import Home from "./component/Home"
import About from "./component/About"
import Contact from "./component/Contact"


function App() {
  const Router = createBrowserRouter([
    {
      path: '/',
      element:<> <Navbar /> <Home /> </>
    },
    {
      path: '/about',
      element:<> <Navbar /> <About /> </>
    },
    {
      path: '/contact',
      element:<> <Navbar /> <Contact /> </>
    }
  ])
  return (
    <>
      <RouterProvider router={Router} />
    </>
  )
}

export default App
```

## You can click on the elements in your browser and see the results

## Now your pages will change without reloading the pages with the help of <b>react-router-dom</b>

# 25

# We can also get Params from the browser using useParams

```
import { useParams } from 'react-router-dom'
```

## Create a component
```
import React from 'react'
import { useParams } from 'react-router-dom'
const User = () => {
  const params = useParams()
  return (
    <div>Username is {params.username}</div>
  )
}

export default User
```
## Add :/colons before the variable, For Example /:username

```
import Navbar from "./component/Navbar"
import { createBrowserRouter, RouterProvider } from 'react-router-dom'
import User from "./component/User"


function App() {
  const Router = createBrowserRouter([
    {
      path: '/user/:username',
      element: <> <Navbar /> <User /> </>
    }
  ])
  return (
    <>
      <RouterProvider router={Router} />
    </>
  )
}

export default App
```

## Now if you type anything after / it will be displayed
#### if i type following in the browser
```
/daniel
```
## Output
```
Username is daniel
```

# 26

## We can add patterns in our links like when ever we click on the link its background color should change

## Todo that instead of using { Link } we use { NavLink }

```
import React from 'react'
import { NavLink } from 'react-router-dom'

const Navbar = () => {
    return (
        <nav>
            <NavLink className={(e => e.isActive ? "blue" : "")} to="/">Home</NavLink>

            <NavLink className={(e => e.isActive ? "blue" : "")} to="/about">About</NavLink>

            <NavLink className={(e => e.isActive ? "blue" : "")} to="/contact">Contact</NavLink>
        </nav>
    )
}

export default Navbar
```
### And then we can give it a class like this
## Remember! we have to define the class