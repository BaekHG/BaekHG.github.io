#Component의  lifeCycle

여러 단계가 있을 수 있지만 자주 호출되는 단계를 살펴보자.

1. `component`에 생성자가 있다면 **생성자가 가장 먼저 호출 된다.**
2. `render`가 호출이 되며 return 값을 실행시켜준다.
3. `componentDidMount()` 가 호출되며 component가 render 됐음을 알려준다.

----
이외에 component를 떠날 때 호출 되는 `componentWillUnmount()`, this.setState로 인해 state가 변경 됐을 때 호출 되는 `componentDidUpdate()` 등이 있다.
