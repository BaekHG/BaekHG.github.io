# map과 reduce

자바 스크립트 내장 메소드로 다양한 곳에 활용할 수 있는 map과 reduce에 대해 알아보자!!

----


##map

간단히 말해 `map`은 반복문을 돌며 배열 안의 요소들을 **1대1로** 매칭시켜주는 것이다. 어떻게 짝지어줄 것인가는 정의한 함수에 메소드의 인자를 넣어주면 된다.
```JavaScript
const food =["kimchi","kimbap", "samgyupsal"]
let result = food.map(favorite =>{
  console.log(favorite);
  return favorite
});
// ["kimchi", "kimbap", "samgyupsal"] 출력!
```
또한, 아래 코드와 같이 배열 모두를 반환할 수 있는 것이 아니라  **함수 안에 명시한대로 반환할 수 있기 때문에 자유도가 높다!**
```javascript
result = food.map(favorite =>{
  if(favorite == "kimchi"){
    return 'spicy';
  }else{
    return 'soso';
  }
});
result;
//  ["spicy", "soso", "soso"] 출력!
```

다시 말해 map은 배열을 **1대1로 매칭시켜주며 기존 객체는 수정하지 않는 메소드이다.**

##reduce

**reduce는 누적값 , 현재값을 통해 결과를 return해주는 메소드이다.**
reduce는 `배열.reduce((누적값,현재값,인덱스,요소)=>{return 결과}, 초기값);` 이러한 형태로 사용한다.
```javascript
number = [1,2,3,4,5]
result = number.reduce((acc,cur,i) =>{
	console.log(acc,cur,i);
	return acc + cur;
}, 0);
result;
//0 1 0
//1 2 1
//3 3 2
//6 4 3
//10 5 4

//15

```
