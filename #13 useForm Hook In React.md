# useForm Hook

### useForm Hook is a package we have to install it then we can import it

## Why we use useForm Hook

### useForm Hook is a package that gives us predefined code for form handling
- It gives us predefined checks for usernames. passwords etc...

## Install It
```
npm i react-hook-form
```

## Import It
```
import { useForm } from "react-hook-form"
```
## Get the keys from the useForm Hook by calling it inside a variable like this

```
const {
  register,
  handleSubmit,
  setError,
  formState: { errors, isSubmitting },
} = useForm()
```
## Now we can use the keys in our form like this

## register Key
```
<input {...register("username", { required: { value: true, message: "This field is required" }, minLength: { value: 6, message: "Min Length is 6" }, maxLength: { value: 12, message: "Max Length is 12" } })} type="text" />
```
## handleSubmit
```
const onSubmit = (data) => console.log(data)
<form onSubmit={handleSubmit(onSubmit)}></form>
```
## setError
```
const onSubmit = (data) => setError("myForm", { message: "This user is not allowed" })

<form onSubmit={handleSubmit(onSubmit)}></form>

{errors.myForm && <div style={{ color: "red" }}>{errors.myForm.message}</div>}
```
## formState

```
{errors.username && <div style={{ color: "red" }}>{errors.username.message}</div>}

{isSubmitting && <div style={{ color: "white" }}>Submiting...</div>}


<input disabled={isSubmitting} type="submit" value="Submit" />
```

## A Form Example
```
import { useForm } from "react-hook-form"

function App() {
  const {
    register,
    handleSubmit,
    setError,
    formState: { errors, isSubmitting },
  } = useForm()

  const delay = (time) => {
    return new Promise((res, rej) => {
      setTimeout(() => {
        res()
      }, time * 1000);
    })
  }

  const onSubmit = async (data) => {
    await delay(2)
    if (data.username != "Daniel") {
      setError("myForm", { message: "This user is not allowed" })
    }
    console.log(data)
  }
  return (
    <>
      {isSubmitting && <div style={{ color: "white" }}>Submiting...</div>}
      <form action="" onSubmit={handleSubmit(onSubmit)}>
        <input placeholder="username" {...register("username", { required: { value: true, message: "This field is required" }, minLength: { value: 6, message: "Min Length is 6" }, maxLength: { value: 12, message: "Max Length is 12" } })} type="text" />
        {errors.username && <div style={{ color: "red" }}>{errors.username.message}</div>}
        <br />
        <input placeholder="password" {...register("password", { required: { value: true, message: "This field is required" }, minLength: { value: 6, message: "Min Length is 6" }, maxLength: { value: 12, message: "Max Length is 12" } })} type="password" />
        {errors.password && <div style={{ color: "red" }}>{errors.password.message}</div>}
        <br />
        <input disabled={isSubmitting} type="submit" value="Submit" />
        {errors.myForm && <div style={{ color: "red" }}>{errors.myForm.message}</div>}
      </form >
    </>
  )
}

export default App
```

# To submit form data to an Express App we can do by following these steps

## Install cors, body-parser, express

## Express
```
npm i express@4
```

## Cors
```
npm i cors
```

## BodyParser
```
npm i body-parser
```

## Now create a server.js file and create a basic express app and import cors, bodyParser and use them like this

```
import express from "express"
const app = express()
const port = 3000
import cors from "cors"
import bodyParser from "body-parser"

app.use(cors())
app.use(bodyParser.json())

app.get('/', (req, res) => {
    res.send('Hello hashir!')
})
app.post('/', (req, res) => {
    console.log(req.body)
    res.send('Hello World!')
})

app.listen(port, () => {
    console.log(`Example app listening on port ${port}`)
})
```

## Now simply post the data in the onSubmit function in the URL using fetch
```
const onSubmit = async (data) => {
  let req = await fetch("http://localhost:3000/", { method: "POST", headers: { "Content-Type": "application/json" }, body: JSON.stringify(data) })
}
``` 
## The data in this onSubmit function is the data that you submit when submiting the form after filling the input boxes
## Because we are calling this function when we submit the form

```
<form onSubmit={handleSubmit(onSubmit)}></form>
```
