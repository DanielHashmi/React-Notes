# Redux In React
## We use redux in big project where we want to use our states, functions etc... to our components directly easily

## FIrst Install It
```
npm install @reduxjs/toolkit react-redux
```

## Now create a redux folder and create a store.js file in it. Now create a redux store in it

```
import { configureStore } from '@reduxjs/toolkit'

export const store = configureStore({
    reducer: {}
})
```
## Now we have to give access our App.jsx to this store, To do it we just need to import Store, Provider and wrap our App with the Provider
```
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App.jsx'
import './index.css'


import { store } from './redux/store.js'
import { Provider } from "react-redux"

ReactDOM.createRoot(document.getElementById('root')).render(

  <React.StrictMode>

    <Provider store={store}>
      <App />
    </Provider>

  </React.StrictMode>

)
```

## To store variables, functions etc... to our store we have to create slices.

# Slices
- Slice is just a state in which we can store data the difference is that it can be used in any of our component without passing it as a prop

## In this example we created a counterSlice it is just a state that has 3 functions through which we can manipulate the state, The initial value of the state is 0
```
import { createSlice } from '@reduxjs/toolkit'

const initialState = {
    value: 0,
}

export const counterS1ice = createSlice({
    name: 'counter',
    initialState,
    reducers: {
        increment: (state) => {
            state.value += 1
        },
        decrement: (state) => {
            state.value -= 1
        },
        incrementByAmount: (state, action) => {
            state.value += action.payload
        },

    },
})

export const { increment, decrement, incrementByAmount } = counterS1ice.actions
export default counterS1ice.reducer
```


## To increase the value of this state we use dispatch like this, Before everything we have to import them and assign them in variables

## Importing
```
import { useSelector, useDispatch } from 'react-redux'

import { increment, decrement, incrementByAmount } from './redux/counter/counterSlice'
```
## Assigning
```
const count = useSelector((state) => state.counter.value)

const dispatch = useDispatch()
```

## Usage
### Whenever we click on this button the state increases by one
```
<button onClick={() => { dispatch(increment()) }}>+</button>
```

### Same with decrement and incrementByAmount
```
<button onClick={() => { dispatch(decrement()) }}>-</button>
<button onClick={() => { dispatch(incrementByAmount(2)) }}>+</button>
```
