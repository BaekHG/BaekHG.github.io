# functional component 와 class component

react에는 두 가지 종류의 컴포넌트가 있다. 하나는 클래스로 만들어진 `class component`와 다른 하나는 함수로 만들어진 `functional component`이다.

## class component
`class component` 는 state를 가지고 있기 때문에 setState과 같은 메소드를 통해 **동적데이터를 사용할 수 있다.** <br> **또한 lifecycle을 사용할 수 있으므로** 홈화면이 뜨기 전 로딩창등을 구현할 수 있다.

## functional component
`functional component`의 단점부터 말하자면 **state를 가질 수 없고 lifecycle이 적용되지 않는다는 것이다.**
`functional component`의 장점은 함수이므로 간단하고 이해하기 쉬운 코드를 작성할 수 있다. 따라서 state와 lifecycle이 필요하지 않는 컴포넌트에서는 `functional component` 가 더 효율적이다.


-----
## class component와 functional component의 사용법
```javascript

//class component
class Food extend React.Component{
  render(){
    return(
      <div>
        <h1> samgyupsal </h1>
      <div>
    )
  }
}

//functional component
function Food(){
  return (
    <div>
      <h1> samgyupsal </h1>
    <div>
  )
}
```
