---
layout: post
title: Sort Algorithm
category: Algorithm
---

### 버블정렬 (Bubble sort)

-------------------------------------------------------------------------
```
import java.util.Arrays;
public class BubbleSort {
    public static void main(String[] args) {
		int[] arr = {3,44,38,5,47,15,36,26,27,2,46,4,19,50,48};
		for (int i = 0; i < arr.length; i++) {	// 시간복잡도 O(N^2)
			for (int j = 0; j < arr.length-i-1; j++) { // 회전 한번하면 맨뒤의 값은 가장 큰값이므로 -i를 한다.
				if(arr[j]>arr[j+1]) {
					int temp = arr[j+1];
					arr[j+1]=arr[j];
					arr[j]=temp;
				}
			}
			System.out.println(Arrays.toString(arr));
		}
    }// end of main
}// end of class
```
-------------------------------------------------------------------------

#### 회전을 1번 끝내면 맨 뒤에는 가장 큰 값 외 있다. 따라서 2번째 회전에는 맨 마지막 값을 확인할 필요가 없다.
#### -> for (int j = 0; j < arr.length-i-1; j++)
#### 앞에 있는 값과 뒤에 있는 값을 확인해 큰값 이를 뒤로 swap 한다.

</br>
</br>
</br>

### 삽입정렬(Insert Sort)

-------------------------------------------------------------------------
```
import java.util.Arrays;
public class InsertSort {
	public static void main(String[] args) {
		int[] arr = {3,44,38,5,47,15,36,26,27,2,46,4,19,50,48};
		for (int i = 0; i < arr.length-1; i++) { //최선 = O(N) 최악=O(N^2)
			for (int j = i+1; j>0; j--) {
				if(arr[j]<arr[j-1]) {
					int temp=arr[j];
					arr[j]=arr[j-1];
					arr[j-1]=temp;
				}
			}
			System.out.println(Arrays.toString(arr));
		}
	}
}
```
-------------------------------------------------------------------------

#### 마지막의 값은 자동으로 정렬된다.
#### -> for (int i = 0; i < arr.length-1; i++)
#### 앞에 있는 값들 중에서 현재의 값보다 작은 값이 있다면 그 값을 찾아서 swap한다.
#### ->	for (int j = i+1; j>0; j--)

</br>
</br>
</br>

### 선택정렬 (Select Sort)

-------------------------------------------------------------------------
```
import java.util.Arrays;
public class SelectSort {
	public static void main(String[] args) {
		int[] arr = {3,44,38,5,47,15,36,26,27,2,46,4,19,50,48};
		int index=0;
		for (int i = 0; i < arr.length-1; i++) { // 마지막에는 자동으로 제일 큰값이 뒤에오기 때문에 -1 만큼 for문
			int min = arr[i];
			for (int j = i+1; j < arr.length; j++) { //시간복잡도는 O(N^2)
				if(min>arr[j]) {
					min = arr[j];
					index=j;
				}
			}
			int temp = arr[i];
			arr[i]=min;
			arr[index]=temp;
			System.out.println(Arrays.toString(arr));
		}
	}
}
```
-------------------------------------------------------------------------

#### 마지막에는 자동으로 가장 큰 값이 오기 때문에 length-1;
#### -> for (int i = 0; i < arr.length-1; i++)
#### min 값을 i 인덱스 값으로 설정하고 뒤에 값들 중에 min보다 작은 값이 있으면 i 번째 값과 j 번째 값을 swap 한다.
#### min 값을 설정하고 min보다 작은 값이 있는지 배열의 크기만큼 탐색한다.
#### -> for (int j = i+1; j < arr.length; j++)

</br>
</br>
</br>

### Merge Sort
-------------------------------------------------------------------------
```
import java.util.Arrays;
public class MergeSort {
	public static void mergeSort(int[] arr, int left, int right) {
		if(left<right) {
			int mid = (left+right)/2;
			mergeSort(arr,left,mid);
			mergeSort(arr,mid+1,right);
			merge(arr,left,mid,right);
		}
	}
	public static void merge(int[] arr, int left, int mid , int right) {
		int i=left;
		int j = mid+1;
		int k=left;
		int[] tmp = new int[arr.length];
		
		while(i<=mid && j<=right) { 	// 비교해서 작은값들을 순서대로 tmp배열에 값을 넣는다.
			if(arr[i]<=arr[j]) {
				tmp[k++]=arr[i++];
			}
			else {
				tmp[k++]=arr[j++];
			}
		}
		while(i<=mid) { 	// 남는 값들을 tmp값에 모조리 넣기.
			tmp[k++]=arr[i++];
		}
		while(j<=right) {	// 남는 값들을 tmp값에 모조리 넣기.
			tmp[k++]=arr[j++];
		}
		for(int z=left; z<=right; z++) { // tmp값을 arr배열에 넣기.
			arr[z]=tmp[z];
		}
		System.out.println(Arrays.toString(tmp)+" "+mid+" "+left+" "+right+" "+i+" "+k);
	}
	public static void main(String[] args) {
		int[] arr = {3,44,38,5,47,15,36,26,27,2,46,4,19,50,48};
		mergeSort(arr, 0, arr.length-1);
		System.out.println(Arrays.toString(arr));
	}
}
```
-------------------------------------------------------------------------

#### 배열 arr을 크기가 2인 배열로 나눈다.
#### 배열 arr은 mid의 값을 기준으로 왼쪽배열 , 오른쪽배열로 나뉜다.
#### 왼쪽배열 , 오른쪽배열이 크기가2인 배열로 나누어지면 왼쪽 배열부터 merge한다.
#### 왼쪽배열(0~7) 배열은 (0~1)->(2~3)->(4~5)->(6~7)
#### 왼쪽배열(0~7) 배열은 (0~3)->(4~7)
#### 왼쪽배열(0~7) 배열은 (0~7) 순서대로 merge한다.
#### 오른쪽배열(8~14) 배열도 똑같이 merge를 한다.
#### 마지막으로 (0~14)배열로 merge를 한다.
#### merge할때 작은값부터 tmp배열에 저장한다.
```
		while(i<=mid && j<=right) { 	// 비교해서 작은값들을 순서대로 tmp배열에 값을 넣는다.
			if(arr[i]<=arr[j]) {
				tmp[k++]=arr[i++];
			}
			else {
				tmp[k++]=arr[j++];
			}
		}
```
#### 정렬하고 변수 i나 j가 while문 조건에 맞지 않는다면
```
		while(i<=mid) { 	// 남는 값들을 tmp값에 모조리 넣기.
			tmp[k++]=arr[i++];
		}
		while(j<=right) {	// 남는 값들을 tmp값에 모조리 넣기.
			tmp[k++]=arr[j++];
		}
```
#### 의 과정으로 남는값을 모두 tmp에 넣는다.
#### ex) 6 7 8 9    ,   2 3 4 5  두개를 merge하면
#### 2 3 4 5 먼저 들어오기 때문에 j의 값은 right의 값보다 커지게 되므로 while문을 나오게된다.
#### 따라서 i값으로 tmp에 남는값을 모두 넣어준다.
