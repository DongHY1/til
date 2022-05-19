# React Event Handler

## why need callback function

for example:

if we use this.xxx,we should bind the function in constructor

```jsx
class App extends Component{
 constructor(){
  this.add = this.add.bind(this)
}
  render(){
    return(
      // 🙅
      <button onClick={this.add()}></button>
      // 🙆
      <button onClick={this.add}></button>
    )
  }

}

```

if we don't like write too much in constructor,we can use **Arrow Function** in there:

```jsx
<button onClick={(e)=>this.add(e)></button>
```



