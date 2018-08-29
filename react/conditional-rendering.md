## 조건에 따라서 특정 Object를 렌더링할 지 말지 결정할 때

```jsx
function ConditionalRender(props){
  var someObject;
  var anotherObject;
  
  if(props.intValue > 0){
    someObject = (<Tag color="gold">{ props.intValue }건</Tag>);
  }
  if(props.anotherIntValue > 0){
    anotherObject = (<Tag color="magenta">{ props.anotherIntValue }건</Tag>);
  }
  
  return(
    <div>
      {someObject}
      {anotherObject}
    </div>
  );
}

class SomeClass extends Component {
  render(){
    return(
      <ConditionalRender intValue="0" anotherIntValue="3"/>
    );
}
```
