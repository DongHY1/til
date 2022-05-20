# React Context

The aim is share data across different component

1. we have Three component

```jsx
export default class GrandFather extends React.Component {
  constructor(props) {
    super(props);
    this.state={
      name:'david'
    }
  }
  render() {
    return (
     	<Father/>
    )
  }
}
function Father(){
  return (
      <Son/>
  )
}
class Son extends React.Component{
  render() {
    return (
        <h1>{......}</h1>
    )
  }
}

```

How can we get data from GrandFather component in Son component?

use **React.createContext** we can share data

```jsx
// copy GrandFather values in 'this.state'
const UserContext = React.createContext({
  // 'david' is a default value
  name:'david'
})
// use Provide in GrandFather
<UserContext.Provider value={this.state}>
	<Father/>
</UserContext.Provider>
```

+ If our Son component is 'class component'

```jsx
class Son extends React.Component{
  render() {
    return (
      <div>
        <h1>{this.context.name}</h1>
      </div>
    )
  }
}
Son.contextType = UserContext;
```

+ if our Son component is 'function component'

```jsx
function Son2(){
  return (
    <UserContext.Consumer>
      {
        value =>{
          return(
            <div>
              <h1>{value.name}</h1>
            </div>
          )
        }
      }
    </UserContext.Consumer>
  )
}
```



It's seems so complex, if we have more React.createContext,we must have nested structure.

Actually,we often use **Redux** or **React Hook** to replace Context

