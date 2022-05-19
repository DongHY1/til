# React Component Communication

+ Father to Son : Father props to Son
+ Son to Father : Father give a callback funtion props to Son,Son can call this function

For example

```jsx
class myBtn extends Components{
 	render(){
    const {onClick} = this.props
    return(
    <button onClick={onClick}>+1</button>
    )
  }
}
class App extends Components{
  add(){
    .....
  }
  render(){
  	return(
    	<myBtn onClick={()=>this.add()}></myBtn>
    )  
  }
}
```





