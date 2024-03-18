## 20
# Conditional Rendering In React

### We use conditional rendering when we want to do something based on a condition For Example: If we want to display a button when variable bool is true else show a text Hello!

#### We do it like this
```
const [bool,setBool] = useState(true)
{bool ? <button>Click Me</button> : <h1>Hello</h1>}
```
#### We do this when we want to use if else statements

## If we just want to use if statement like if the bool is true show the button else do nothing

#### We do it like this

```
const [bool,setBool] = useState(true)
{bool && <button>Click Me</button>}
```

## 21

# Rendering Multiple Components Using Map

### Sometimes we want to render many components in one place so we need loops

This is how we do it with Map method

```
import { useState } from "react"

function App() {
  const [todos, setTodos] = useState([
    {
      title: "hello #1",
      id: "123"
    },
    {
      title: "hello #2",
      id: "456"
    },
    {
      title: "hello #3",
      id: "789"
    }
  ])

  function Todo({ props }) {
    return <>
      <h1>{props.title}</h1>
      <h1>{props.id}</h1>
    </>
  }
  return (
    <>
      {todos.map((todo) => {
        return <Todo props={todo} />
      })}
    </>
  )
}

export default App
```
#### But we need to add a unique key to each component so we do it like this
```
import { useState } from "react"

function App() {
  const [todos, setTodos] = useState([
    {
      title: "hello #1",
      id: "123"
    },
    {
      title: "hello #2",
      id: "456"
    },
    {
      title: "hello #3",
      id: "789"
    }
  ])

  function Todo({ props }) {
    return <>
      <h1>{props.title}</h1>
      <h1>{props.id}</h1>
    </>
  }
  return (
    <>
      {todos.map((todo) => {
        return <Todo key={todo.id} props={todo} />
      })}
    </>
  )
}

export default App
```
#### Remember we need a unique key in this example id is the key: key={todo.id}