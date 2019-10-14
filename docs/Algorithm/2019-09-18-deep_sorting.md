
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

---

# 힙 정렬 (heap sort)
