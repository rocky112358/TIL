## Parent의 state을 Child에게 줄 때
그냥 주면 된다.
#### Parent
```jsx
class ParentComponent extends Component {
  state = {
    some_state: true
  }
  render() {
    return(
      <ChildComponent parentState={ this.state } />
    );
  }
}
```
#### Child
```jsx
class ChildComponent extends Component {
  if(this.props.parentState.some_state){
    do_something;
  }
}
    
```

## Child에서 Parent의 state를 변화시키고 싶을 때
Child에게 callback 함수를 넘겨주면 된다. 때가 되면 부를 것.
#### Parent
```jsx
class ParentComponent extends Component {
  state = {
    some_state: true
  }
  
  callbackFunc = (new_state) => {
    this.setState({
      ...this.state,
      some_state: new_state
    });
  }
  
  render() {
    return(
      <ChildComponent stateChangeCallback={ this.callbackFunc } />
    );
  }
}
```
#### Child
```jsx
class ChildComponent extends Component {
  changeState = (props) => {
    this.props.stateChangeCallback(new_state);
  }
  <ChildComponent onClick={ this.chageState } />
}
    
```
