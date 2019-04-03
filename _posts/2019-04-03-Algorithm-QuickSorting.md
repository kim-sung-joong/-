---
layout: post
title: QuickSort Algorithm
category: Algorithm
---
### 퀵정렬이란 ?
```
다른 원소와의 비교만으로 정렬을 수행하는 비교 정렬에 속한다.
퀵 정렬은 n개의 데이터를 정렬할 때, 최악의 경우에는 O(n2)번의 비교를 수행하고, 평균적으로 O(n log n)번의 비교를 수행한다.
->n개의 데이터를 비교하고 n/2의 데이터를 또 비교하므로 n log n
퀵 정렬의 내부 루프는 대부분의 컴퓨터 아키텍처에서 효율적으로 작동하도록 설계되어 있고
(그 이유는 메모리 참조가 지역화되어 있기 때문에 CPU 캐시의 히트율이 높아지기 때문이다.),

대부분의 실질적인 데이터를 정렬할 때 제곱 시간이 걸릴 확률이 거의 없도록 알고리즘을 설계하는 것이 가능하다. 
때문에 일반적인 경우 퀵 정렬은 다른 O(n log n) 알고리즘에 비해 훨씬 빠르게 동작한다. 
그리고 퀵 정렬은 정렬을 위해 O(log n)만큼의 memory를 필요로한다.

많은 라이브러리에서는 세 값(좌측 끝, 중앙, 우측 끝)의 중위법을 이용하여 분할한다. 
이 방법을 사용하면 중앙에서 분할될 가능성이 높아 전체적으로 정렬의 성능이 좋아진다.

병합 정렬 과 마찬가지로 QuickSort는 나누기 및 정복 알고리즘입니다. 
요소를 피벗 (pivot)으로 선택하고 주어진 배열을 픽업 된 피벗 주위로 분할합니다.
다양한 방식으로 피벗을 선택하는 여러 버전의 quickSort가 있습니다.

1.항상 첫 번째 요소를 피벗으로 선택하십시오.
2.마지막 요소를 항상 피봇으로 선택 (아래 구현)
3.임의의 요소를 피벗으로 선택하십시오.
4.중앙값을 피벗으로 선택하십시오.
```

### 퀵정렬의 핵심은?
```
quickSort의 핵심 프로세스는 partition 입니다. 
분할의 대상은 배열과 요소 x가 피벗 인 경우 정렬 된 배열의 올바른 위치에 x를 놓고 x 앞에 작은 모든 요소 (x보다 작음)를 놓고
다음에 더 큰 모든 요소 (x보다 큼)를 넣습니다.

파티션 알고리즘 (Partition Algorithm)
여러 가지 방법으로 파티션을 할 수 있으며, 의사 코드는 CLRS book에 주어진 방법을 사용합니다. 
논리는 간단합니다. 가장 왼쪽에있는 요소부터 시작하여 i와 같이 더 작은 요소 (또는 같은 요소)의 인덱스를 추적합니다. 
횡단하는 동안 더 작은 요소를 발견하면 현재 요소를 arr [i]로 교체합니다. 그렇지 않으면 현재 요소를 무시합니다.

/ * 낮음 -> 시작 색인, 높음 -> 종료 색인 * /
quickSort (arr [], low, high)
{
    if (low <high)
    {
        / * pi는 분할 색인입니다. arr [pi]는 지금입니다.
           올바른 장소에서 * /
        pi = 파티션 (arr, low, high);

        quickSort (arr, low, pi-1); // 파이 전에
        quickSort (arr, pi + 1, high); // 파이 이후
    }
}
```

### 다른 정렬기법과의 차이점?
```
QuickSort의 최악의 시간 복잡도는 O (n 2 )이지만 병합 정렬 및 힙 정렬 과 같은 다른 많은 정렬 알고리즘보다 많지만 QuickSort는 실제로 내부 루프가 대부분의 아키텍처에서 효율적으로 구현 될 수 있기 때문에 실제로 더 빠릅니다. 실제 데이터. QuickSort는 피벗 선택을 변경하여 다양한 방식으로 구현 될 수 있으므로 주어진 유형의 데이터에 대해 최악의 경우가 거의 발생하지 않습니다. 그러나 병합 정렬은 일반적으로 데이터가 크고 외부 저장소에 저장 될 때 더 나은 것으로 간주됩니다.

1. 병합정렬은 추가로 사용하는 공간할당 및 공간해제로 실행시간을 늘린다.
퀵정렬은 하나의 배열을 사용하기 때문에 추가 배열이 필요없습니다.
-> 캐시친화적인 정렬 알고리즘이 될수 있다.
Quicksort는 특히 캐시 위치를 잘 나타내므로 가상 메모리 환경과 같이 많은 경우 병합 정렬보다 빠르게 만듭니다.

LinkedList 에서 퀵정렬보다는 병합정렬을 !
 배열과 달리 링크드리스트에서는 중간에 O (1) 여분의 공간과 O (1) 시간 안에 항목을 삽입 할 수 있습니다. 
 따라서 병합 정렬의 병합 작업은 연결된 목록에 대한 추가 공간없이 구현할 수 있습니다.
 
quicksort가 빠르다는 이유는 하드웨어에서 매우 잘 작동하는 특성을 가지고 있기 때문입니다. 
예를 들어, quicksort는 동적 할당이 필요 없습니다. 
재귀에 필요한 스택 프레임을 저장하기 위해 O (log n) 스택 공간 (올바르게 구현 된 경우 최악의 경우) 만 사용하여 
원래 배열에서 그대로 작동 할 수 있습니다. 
mergesort는이를 수행 할 수 있지만 일반적으로 병합 단계에서 큰 성능 저하가 발생합니다. 
heapsort와 같은 다른 정렬 알고리즘에도이 속성이 있습니다.

또한 quicksort는 뛰어난 참조 지역을 제공합니다. 
파티셔닝 단계를 수행하는 경우 본질적으로 어레이의 양쪽 끝에서 안쪽으로 수행되는 두 개의 선형 스캔입니다. 
이것은 quicksort가 매우 적은 수의 캐시 미스를 가지게됨을 의미합니다. 
이는 현대 아키텍처에서 성능에 결정적입니다. 
반면에 Heaport는 매우 좋은 지역을 가지고 있지는 않습니다. 대부분의 mergesort 구현은 합리적으로 지역적입니다.

Quicksort도 병렬 처리가 가능합니다. 
초기 분할 단계가 어레이를 더 작은 영역과 더 큰 영역으로 분할하기 위해 발생하면, 이 두 부분은 서로 독립적으로 정렬 될 수 있습니다.
mergesort를 포함하여 많은 정렬 알고리즘을 병렬 처리 할 수 있지만 병렬 퀵 정렬의 성능은 위의 이유로 다른 병렬 알고리즘보다 우수합니다. 
반면 힙은 그렇지 않습니다.

quicksort의 유일한 문제는 O (n 2 )로 저하 될 가능성이 있다는 것인데, 대용량 데이터 세트에서는 매우 심각 할 수 있습니다. 
이것을 피하는 한 가지 방법은 알고리즘을 자체적으로 더 신뢰할 수있는 알고리즘 중 하나로 전환하는 것입니다. 
introsort 라고하는이 알고리즘 은 병리학 적 사례없이 퀵 소트의 많은 이점을 얻는 훌륭한 하이브리드 정렬 알고리즘입니다.
```
-----------------------------------------------

```
public class QuickSort {
	private static void quickSort(int[] arr) {
		//재귀 함수로  배열과 시작위치 , 끝나는 지점을 받아온다.
		quickSort(arr , 0 , arr.length-1);
	}
	private static void quickSort(int[] arr, int start, int end) {
		//start 와 end를 받아오면 그 안에서 파티션을 나눔.
		//나눈 파티션의 오른쪽값 첫번째 값을 받아온다.
		int rPart = partition(arr,start,end);
		// 오른쪽 첫번째 값이 start 값이면 비교할 필요가 없음.
		// 따라서 오른쪽 파티션이 start랑 1개 이상 차이가 나면 재귀함수를 호출한다.
		if(start < rPart - 1) {
			quickSort(arr, start, rPart - 1);
		}
		//오른쪽 배열방이 1개 이상일때만 호출해야 함.
		if(rPart < end) {
			quickSort(arr, rPart, end);
		}
	}
	private static int partition(int[] arr, int start, int end) {
		//중앙값으로 지정
		int pivot = arr[(start+end)/2];
		
		//start와 end가 cross할때까지
		while(start <= end) {
			//왼쪽에는 피벗값보다 작은값이 온다.
			//따라서 피벗값보다 큰걸 만나면 stop
			while(arr[start] < pivot) {
				start++;
			}
			//오른쪽에는 피벗값보다 큰 값이 온다.
			//따라서 피벗값보다 작은값을 만나면 stop
			while(arr[end] > pivot) {
				end--;
			}
			//서로 만났다가 지나치지 않았는지 확인해줌.
			//아직 안지나갔으면 swap후 인덱스 업데이트
			if(start <= end) {
				swap(arr,start,end);
				start++;
				end--;
			}
		}
		//계속 하다보면 새로 나눌 파티션의 오른쪽 인덱스 첫번째
		return start;
	}

	private static void printArray(int[] arr) {
		for (int i = 0; i < arr.length; i++) {
			System.out.print(arr[i]+" ");
		}
		System.out.println();
	}

	private static void swap(int[] arr, int start, int end) {
		int temp = arr[start];
		arr[start] = arr[end];
		arr[end] = temp;
	}
	public static void main(String[] args) {
		int[] arr = {3,9,4,7,5,0,1,6,8,2};
		//정렬전에 출력
		printArray(arr);
		quickSort(arr);
		//정렬 후 출력
		printArray(arr);
	}//end of main
}//end of class

```
