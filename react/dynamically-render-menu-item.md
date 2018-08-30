## 조건에 따라 특정 Object만 보이게/안보이게 하고싶을 때
예시) 관리자일 때만 보이게 하려고 함.
key를 AdminPanel 옆에 안쓰고 Menu.Item 옆에 쓰면 왜인지 Menu에서 key 인식이 안된다. item_1 이런식으로 나옴.
```jsx
function AdminPanel(props){
  if(props.isadmin){
    return(
      <Menu.Item {...props}>
        <Icon type="code" />
        <span className="nav-text">Admin Page</span>
      </Menu.Item>
    );
  }
  else{
    return null;
  }
}

class SideBar extends Component {
  render(){
    <Menu>
      <Menu.Item key="dashboard">
        <Icon type="dashboard" />
        <span className="nav-text">대시보드</span>
      </Menu.Item>
      <AdminPanel key="admin" isadmin={ this.props.isAdmin ? 1 : 0 } />
    </Menu>
  }
}
```
