## 22
# Event Handling In React
### We can simply handle events in react like this
```
function App() {


  return (
    <>
      <button onClick={ }></button>
      <button onMouseOver={ }></button>
    </>
  )
}

export default App
```
### We can get the javascript addEventListener e like this

```
function App() {
  function hello(e) {
    console.log(e.target)
  }

  return (
    <>
      <div onClick={hello}>
        <button >Hello</button>
      </div>
    </>
  )
}

export default App
```
### element.addEventListener((e)=>{})

# 23
## Inputs In React

### We handle inputs in react in a different way
```
import { useState } from "react"
function App() {
  const [form, setForm] = useState({ email: "mango111@gmail.com", phone: "45341111" })
  function handleChange(e) {
    setForm({ ...form, [e.target.name]: e.target.value })
    console.log(form)
  }
  return (
    <>
      <input type="text" name="email" value={form.email} onChange={handleChange} />

      <input type="text" name="phone" value={form.phone} onChange={handleChange} />
    </>
  )
}

export default App
```

#### This way we can handle multiple inputs in one handleChange function

## What the code means above

### This is an object
```
const [form, setForm] = useState({ email: "mango111@gmail.com", phone: "45341111" })
```
#### It contains two key value pairs: email, phone

### This is a function that sets the form objects keys values
```
  function handleChange(e) {
    setForm({ ...form, [e.target.name]: e.target.value })
    console.log(form)
  }
```
- E is the event of the element of which it is being listened
- e.target.name is the name attribute of the input
- e.target.value is the value attribute of the input

### These are the inputs
```
    <input type="text" name="email" value={form.email} onChange={handleChange} />

      <input type="text" name="phone" value={form.phone} onChange={handleChange} />
```
- It has a name and a value attribute
- It has a onChange event inside the event it has a function handleChange