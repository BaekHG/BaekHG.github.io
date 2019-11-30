# async & await
**`async`와 `await`는 비동기 javascript를 동기식으로 만들어주는 문법이다!**<br>
`async`를 선언해주면 함수 내부에서 `await`를 선언한 코드가 끝날 때까지 기다려준다.<br>


```javascript
getGoogle = async () =>{
  const movies = await axios.get("https://google.com");
}
```
다음과 같은 코드가 있을 때 await가 걸려있는 코드가 끝날 때까지 javascript는 기다려준다.<br>
만약` await`를 사용하지 않는다면 javascript는 `getGoogle`이라는 함수를 기다려주지 않을 것이고 우리가 하고자 하는 작업을 위해 더 많은 코드를 작성해야 한다.
