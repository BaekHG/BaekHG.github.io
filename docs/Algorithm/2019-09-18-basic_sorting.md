2019년 9월 18일

# 기초 정렬

---

> 일반적으로 알고리즘을 공부할 때 가장 먼저 풀어보는 문제는 **'정렬'** 문제이다. 정렬만큼 알고리즘의 **효율성 차이**를 확실히 보여주는 것은 없기 때문이다★★

# 선택 정렬 (Selection Sort)

-	**시간 복잡도 : O(n^2)**
-	**가장 작은 것**을 선택하여 **가장 앞으로** 보낸다!

-	비효율적인 `정렬알고리즘` 중 하나이다.

```C++
#include <stdio.h>

int main(){
    int i,j,min,index,temp;
    int array[10] = {1, 10, 5 ,8 ,7 ,6 , 4 ,3 ,2 ,9};
    for(i=0; i<10; i++ ){
        min = 9999;
        for(j=i; j<10; j++){
            if(min > array[j]){
                min = array[j];
                index = j;
            }
        }
        temp =array[i];
        array[i] = array[index];
        array[index] = temp;
    }
    for(i=0; i<10; i++){
        printf("%d " ,array[i]);
    }
    return 0;
}
```

-	`min` : **가장 작은 숫자**를 일시적으로 저장하는 변수
-	`index` : 해당 for문에서 `가장 작은 값의 위치`를 저장하는 변수이다.
-	`temp` :이 후 `temp변수`를 통해 두 수를 바꿔준다.

---

# 버블 정렬 (Bubble Sort)


-	**시간 복잡도 : O(n^2)**
-	옆에 있는 값과 비교해서 더 작은 값을 앞으로 보낸다.
-	모든 정렬 알고리즘 중에 구현은 가장 쉽지만 **가장 효율성이 떨어지는 알고리즘**.

```C++
#include <stdio.h>
int main(){
    int i,j,temp;
    int array[10] = {1, 10, 5 ,8 ,7 ,6 , 4 ,3 ,2 ,9};
    for (i=0; i<10; i++){
        for(j=0; j<9-i; j++){
            if(array[j] >array[j+1]){
                temp = array[j];
                array[j] = array[j+1];
                array[j+1] = temp;
            }

        }
    }
    for(i=0; i<10; i++){
        printf("%d ", array[i]);
    }
    return 0;
}
```

-	두 숫자를 비교하여 작은 수를 앞으로 보내게 된다.
-	이러한 과정을 통해 한번 돌 때 마다 `가장 큰 값이 맨 뒤로` 보내지게 된다.

---

2019년 9월 20일

# 삽입 정렬(Insertion Sort)

-	**시간 복잡도 : O(n^2)**
-	항상 왼쪽은 정렬이 되어있다. 즉, 자신이 멈출 포인트를 알 수 있다.
-	필요한만큼만 이동하면 된다.
-	`정렬이 되어있으면 되어있을수록` **효율적인 알고리즘** 이다.

```C++
#include <stdio.h>

int main(){
    int i,j,tmp;
    int array[10] = {1, 10, 5 ,8 ,7 ,6 ,4 ,3 ,2 ,9};

    for (i=0; i<9; i++){
        j=i;
        while(array[j] > array[j+1] ){
            tmp = array[j];
            array[j] = array[j+1];
            array[j+1] = tmp;
            j--;
        }
    }
    for(i=0; i<10; i++){
        printf("%d ", array[i]);
    }
    return 0;
}
```

-	자신의 왼쪽은 항상 정렬이 되어있는 상태이므로 필요한만큼만 이동하면 된다.
	-	예를 들어 7의 경우 {1, 5, 8, 10}과 같이 **왼쪽의 값들이 모두 정렬이 된 상태**가 되므로 두 번만 이동을 하면 된다.`{1, 5, 8, 10, 7} -> {1, 5 ,8 ,7 , 10} -> {1, 5, 7, 8, 10}`

---

2019년 9월 23일

# 퀵 정렬 (Quick Sort)

-	평균 속도 : O(N*logN)
-	최악시간복잡도 : O(N^2)
-	대표적인 **분할 정복 알고리즘**
	-	`분할정복(divide and conquer)` : 문제를 작은 **2개의 문제로 분리**하고 각각을 해결한 다음, **결과를 모아서** 원래의 문제를 해결하는 전략
	-	분할 정복 방법은 대개 **순환 호출(재귀)** 을 이용하여 구현한다.

```C++
#include <stdio.h>
int number = 10;
int data[10] = {1, 10, 5, 8, 7, 6, 4, 3, 2, 9};

void quickSort(int *data, int start, int end){
    if(start >= end){ // 원소가 1개인 경우
        return;
    }

    int key = start; // key는 첫번째 원소
    int i = start + 1;
    int j = end;
    int temp;

    while(i<=j) { //엇갈릴 때까지 반복
        while (data[i] <= data[key]){ // 키 값보다 큰 값을 만날때까지
            i++;
        }
        while(data[j] >= data[key] && j>start){// 키 값보다 작은 값을 만날때까지 , 왼쪽에 있는 값이 key값과 교체를 하므로 왼쪽만 체크
            j--;
        }
        if( i>j){//엇갈린 상태면 키 값과 교체
            temp = data[j];
            data[j] = data[key];
            data[key] = temp;
        }else{ // 엇갈리지 않았을 때  , 그대로
            temp = data[j];
            data[j] = data[i];
            data[i] = temp;
        }
    }

    //재귀
    //pivot을 기준으로 왼쪽 오른쪽 다시 퀵정렬
    quickSort(data,start,j-1);
    quickSort(data,j+1, end);
}
int main(void){
    quickSort(data,0,number-1);
    for(int i =0; i<number; i++){
        printf("%d ", data[i]);
    }
}
```

## 퀵정렬 알고리즘 간단 요약

1.	리스트 안에 한 요소를 선택한다. 이렇게 고른 요소를 `피벗(pivot)`이라고 한다.
2.	피벗을 기준으로 피벗보다 `작은 요소들은 모두 피벗의 왼쪽`으로, `큰 요소들은 오른쪽`으로 옮겨진다.
3.	피벗의 왼쪽부분과 오른쪽부분을 다시 `재귀`를 통해 정렬을 해준다.
4.	리스트의 크기가 `0 또는 1`이 될 때까지 반복해준다. **(분할이 불가능할때까지)**

## 분할정복 및 결합

-	`분할` : 선택한 요소(피벗)을 기준으로 2개의 파트로 나누어 준다.
-	`정복` : 나누어진 2개의 파트를 피벗을 제외하고 정렬해 준다.
-	`결합` : 정렬된 파트들을 다시 하나로 합쳐준다.
-	**순환 호출이 한번 진행되면 최소한 하나의 원소(피벗)은 최종적으로 위치가 정해지므로, 이 알고리즘은 반드시 끝난다는 것을 보장할 수 있다.**

## 최대의 단점

-	pivot값을 설정함에 따라 `최악시간복잡도`인 **O(n^2)** 이 나올 수 있다.
	-	이미 정렬이 되어있는 경우, **분할 정복의 이점을 사용하지 못하는 경우.**
	-	**But** 삽입정렬의 경우 이미 정렬이 되어있거나 거의 정렬이 되어있는 경우, 매우 효율적

  ---

  2019년 10월 5일

  # 병합 정렬 (Merge Sort)

  -	평균 속도 : O(N*logN)
  - `분할 정복 방법`을 사용한 알고리즘
  - `풀이 방식` :주어진 문제를 반으로 나눠 각자 계산하여 정렬한 후에 나중에 합친다.
  - 퀵 정렬은 이미 정렬이 되어있는 경우 `최악시간복잡도`인 **O(n^2)** 가 나오는 반면 병합 정렬은 반을 나누고 나서 나중에 합치는 형식이므로 **최악의 경우에도 O(N*logN)** 이 보장된다.

## 과정

### 1. 분할 과정
- 따로 피벗을 정하지 않고 정확히 반으로 계속해 쪼개나간다.
- 크기가 1이었던 배열이 2^3 인 8이 된다. **즉, 3단계만 거치면 분할과정이 끝이나게 된다.**
`이를 통해 단계의 크기는 logN 임을 알 수 있다.`
![split](./img/merge_sort1.png)


### 2. 병합 과정
- 쪼개졌던 것들을 합치는 순간 정렬을 수행한다.
- 정렬이 필요한 수행시간은 배열의 크기인 N이므로 `분할 수행시간 logN`과 `정렬 수행시간 N` 이 곱해져 시간복잡도는 **O(N*logN)** 이 된다.
![merge](./img/merge_sort2.png)


```C++
#include <stdio.h>

int number = 8;
int sorted[8]; // 배열은 반드시 전역변수로


void merge(int a[], int m, int middle, int n){
	// m = 시작점, middle = 중간점 , n = 끝점
	int i=m;
	int j = middle + 1;
	int k = m;
	//작은 순서대로 배열에 삽입
	while( i <= middle && j<=n){
		if (a[i] <= a[j]){
			sorted[k]= a[i];
			i++;
		}else{
			sorted[k] = a[j];
			j++;
		}
		k++;
	}

	if(i > middle){
		for (int t = j; t <= n; t++){
			sorted[k] = a[t];
			k++;
		}
	}else{
		for (int t = i; t <= middle; t++){
			sorted[k] = a[t];
			k++;
		}
	}

	//정렬된 배열 삽입
	for ( int t = m; t <= n; t++){
		a[t] = sorted[t];
	}
}

void mergeSort(int a[], int m, int n){
	if (m<n){
		int middle = (m+n) / 2;
		mergeSort(a,m, middle);
		mergeSort(a, middle+1 , n);
		merge(a, m, middle, n);
	}
}

int main(void) {
	int array[number] = {3, 1, 5, 9, 2, 4, 8, 7};
	mergeSort(array, 0, number - 1);
	for (int i =0; i< number; i++){
		printf("%d ", array[i]);
	}
}
```
- `코드를 짤 때 주의할 점` : 반드시 정렬에 사용되는 배열은 전역변수로 선언해주어야 한다. 함수 안에서 배열을 선언해 준다면 필요할 때마다 계속 선언을 해주어야 하므로 **메모리 낭비가 생길 수 있기 때문이다.**
