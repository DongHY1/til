# React setState

## Why use setState

to tell React our data is change 

## setState is asynchronous 

```jsx
//originval message:'A'
this.setState({message:'B'})
console.log(this.state.message) // 'A'
```

> why use asynchronous?
>
> https://github.com/facebook/react/issues/11527

Data change -> setState -> render()

## How to get data immediately ?

+ put a callback function 

```jsx
this.setState({message:'B'},()=>{
  console.log(this.state.message)
})
```

+ use componentDidUpdate

```jsx
componentDidUpdate(){
  console.log(this.state.message)
}
```

## Force setState Synchronize

+ use setTimeout

```jsx
setTimeout(()=>{
  this.setState(...)
},0)
```

+ use dom 

```jsx
<button id='btn'></button>
...
document.getELementById('btn').addEventListener('click',()=>{
  this.setState(...)
})
```

