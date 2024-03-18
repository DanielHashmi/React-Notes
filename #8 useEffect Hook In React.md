 ## 18

 # useEffect Hook

 ### What is useEffect: UseEffect is a function that is used when you want something to happen after a certain components renders, loads or changes

 ## This is a simple use case of useEffect 
 ```
  useEffect(() => {
    alert("Hello World")
  }, [])
```
The empty array is for a value
This code means! show alert when nothing changes because of empty array []
so it will show alert only one time when the page loads first time

## This code means! show alert when value changes
```
  useEffect(() => {
    alert("Hello World")
  }, [value])
```

## If we don't pass an empty array than it will show alert on every render

```
  useEffect(() => {
    alert("Hello World")
  })
```
This function will run on every render so because react re renders App function on every change so this function runs on every change

# Return in useEffect
## return in useEffect runs when a certain component unmounts

```
   useEffect(() => {
        return () => {
          alert("Component was unmounted") // Runs when the component is unmounted
        }
      },[])
```