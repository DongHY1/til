# React shouldComponentUpdate and PureComponent

if we have a component

```jsx
<h1>{data}</h1>
<ComponentA/>
<ComponentB/>
```

When data change, <ComponentA> and <ComponentB> will reload too,how can we avoid it ?

## use shouldComponentUpdate

```jsx
shouldComponentUpdate(nextProps,nextState) {
    if(this.state.counter !== nextState.counter) {
      console.log('refresh component')
      return true
    }
    return false;
}
```



https://zh-hans.reactjs.org/docs/react-component.html#shouldcomponentupdate

## use PureCompnent (class component) and React.memo(function component)

```jsx
import React from 'react';
export default class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      counter:0
    }
  }  
  render() {
    return (
      <div>
        <h1>{this.state.counter}</h1>
        <button onClick={()=>this.handleClick()}>+1</button>
        <Foo/>
        <MemoBar/>
      </div>
    )
  }
  handleClick() {
    this.setState({
      counter: this.state.counter+1
    })
  }
}
class Foo extends React.PureComponent {
  render() {
    console.log('Foo component is Render!')
    return(
      <div>
        <h1>Foo</h1>
      </div>
    )
  }
}
const MemoBar = React.memo(Bar)
function Bar(){
  console.log('Bar component is Render!')
  return(
    <h1>Bar!</h1>
  )
}
```

## 