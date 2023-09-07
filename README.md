# algorithm
알고리즘 세미나

## 알고리즘 이해와 기초

### 알고리즘 정의
알고리즘은 명확하게 정의된 단계별 절차로 문제를 해결하기 위한 방법
<br/>
### 알고리즘의 중요성
  - 문제 해결: 알고리즘은 복잡한 문제를 단순하고 구체적인 단계로 분해하여 해결하는 데 도움
  - 자원 관리: 특히 대용량 데이터 처리나 실시간 응용 프로그램에서 중요
  - 시간과 공간 복잡성: 효율적인 알고리즘을 개발하면 프로그램 실행 속도를 향상시키고 메모리 사용을 최적화
  - 보안과 암호화: 알고리즘은 데이터 보안과 암호화 분야에서 핵심적인 역할

## 빅오 표기법
### 빅오(Big O)란?
Big-O 표기법은 ‘입력값의 변화에 따라 연산을 실행할 때, 연산 횟수에 비해 시간이 얼마만큼 걸리는가?’를 표기하는 방법이다.

<img src="https://blog.kakaocdn.net/dn/umDDr/btqYhz5p1ZN/pULPOIs1zk2kA5QykgYEeK/img.png" width="50%" title="빅오표기법"/>
<img src="https://park-answer.netlify.app/static/893fa1e138e04a1c88f56cfb86793e6b/2a195/big-o-table.png" width="80%" title="빅오표기법"/>
<img src="https://blog.kakaocdn.net/dn/byv7cU/btrwGj2VMnK/W7Edg2M8b4VoTw3QD4J221/img.jpg" width="50%" title="빅오표기법"/>

<br/>

- O(1) : 입력값에 상관없이 일정한 실행시간을 최고!의 알고리즘이라 할 수 있다. 하지만 상수 시간에 실행된다 해도 상수값이 상상 이상으로 클 경우 사실상 일정한 시간의 의미가 없다. 최고의 알고리즘이 될 수 있지만 그만큼 신중해야 한다. 예:) 스택에서 Push, Pop
- O(log n) : 로그는 매우 큰 입력값에서도 크게 영향을 받지 않는 편이다. 매우 견고한 알고리즘으로 이진 탐색의 경우가 이에 해당한다. 예:) 이진트리
- O(n) : 알고리즘을 수행하는데 걸리는 시간은 입력값에 비례한다. 이러한 알고리즘을 선형 시간 알고리즘이라 부른다. 정렬되지 않은 리스트에서 최대 또는 최솟값을 찾는 경우가 해당되며 모든 입력값을 적어도 한 번 이상은 살펴봐야 한다. 예:) for문
- O (n log n) : 병합 정렬등의 대부분 효율이 좋은 알고리즘이 이에 해당 한다. 아무리 좋은 알고리즘이라 할지라도 n log n 보다 빠를 수 없다. 입력값이 최선일 경우, 비교를 건너 뛰어 O(n)이 될 수 있다. 예:) 퀵, 병합, 힙 정렬
- O(n^2)  : 버블 정렬 같은 비효율적인 정렬 알고리즘이 이에 해당 한다. 예:) 이중for문, 삽입, 버블, 선택정렬
- O(2^n) : 피보나치의 수를 재귀로 계산하는 알고리즘이 이에 해당 한다. n^2와 혼동되는 경우가 있는데 2^n이 훨씬 더 크다. 예:) 피보나치 수열
- O(n!) : 가장 느린 알고리즘으로 입력값이 조금만 커져도 계산이 어렵다.

<br/>

## 정렬 알고리즘

필요성: 데이터 정리와 검색을 용이하게 만듦
<br/>
### 버블 정렬 (Bubble Sort):
인접한 두 원소를 비교하고 필요한 경우 서로 위치를 교환하는 알고리즘<br/>
시간 복잡도: O(n^2) 높음

<img src="https://www.swtestacademy.com/wp-content/uploads/2021/11/bubble-sort-2.png" width="50%" title="버블정렬"/>

```java
public static void bubbleSort(int[] arr) {
    int n = arr.length;
    boolean swapped;
    do {
        swapped = false;
        for (int i = 0; i < n - 1; i++) {
            if (arr[i] > arr[i + 1]) {
                // 두 원소 교환
                int temp = arr[i];
                arr[i] = arr[i + 1];
                arr[i + 1] = temp;
                swapped = true;
            }
        }
    } while (swapped);
}
```

### 선택 정렬 (Selection Sort)
배열에서 최솟값을 선택하고, 그 값을 첫 번째 원소와 교환하는 과정을 반복하는 알고리즘입니다.<br/>
시간 복잡도: O(n^2)

<img src="https://www.swtestacademy.com/wp-content/uploads/2021/11/selection-sort-Selection-Sort-1.drawio-1.png" width="50%" title="버블정렬"/>

```java
public static void selectionSort(int[] arr) {
    int n = arr.length;
    for (int i = 0; i < n - 1; i++) {
        int minIndex = i;
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }
        // 최솟값과 현재 원소 교환
        int temp = arr[i];
        arr[i] = arr[minIndex];
        arr[minIndex] = temp;
    }
}
```

### 삽입 정렬 (Insertion Sort)
배열을 정렬된 부분과 정렬되지 않은 부분으로 나누고, 정렬되지 않은 부분의 원소를 정렬된 부분에 삽입하는 알고리즘
시간 복잡도: O(n^2)

```java
public static void insertionSort(int[] arr) {
    int n = arr.length;
    for (int i = 1; i < n; i++) {
        int key = arr[i];
        int j = i - 1;
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
    }
}
```

### 퀵 정렬(Quick Sort)
퀵 소트는 분할 정복 기법을 통해 데이터를 정렬하는 알고리즘
단, 불안정한 정렬(정렬 이후 데이터의 순서가 정렬 이전 원래 순서와 같음을 보장하지 못하는 정렬 알고리즘)
시간 복잡도: O(nlogn)

(1) 주어진 배열에서 임의의 한 원소를 고르고, 이를 피벗(Pivot) 이라 칭한다. (배열 한 가운데, 맨 앞 원소 등) <br/>
(2) 피벗을 기준으로 피벗보다 값이 작은 원소들을 모두 모아놓은 배열 하나와, 피벗보다 값이 큰 원소들을 싸그리 모아놓은 배열 하나 → 이렇게 배열을 둘로 나눈다. 분할을 마친 뒤 피벗은 그 자리에서 더이상 움직이지 않는다. <br/>
(3) 분할된 두 개의 배열에 대해 위 1, 2 과정을 재귀적으로 반복한다.<br/>

단, 정렬이 되어 있는 경우 최악의 시나리오가 될 수 있음 (시간 복잡도 : O(n^2))

<img src="https://static.podo-dev.com/blogs/images/2019/07/10/origin/PAPKSS181224235509.PNG" width="70%" title="퀵 정렬"/>

```java
public class QuickSort {

  public static void main(String[] args) {
    int[] arr = { 3, 1, 5, 6, 20, 10, 7, 11, 15, 9 };
    quickSort(arr);
  }

  public static void quickSort(int[] arr) {
    quickSort(arr, 0, arr.length - 1);
  }

  private static void quickSort(int[] arr, int start, int end) {
    // start가 end보다 크거나 같다면 정렬할 원소가 1개 이하이므로 정렬하지 않고 return
    if (start >= end)
      return;
    
    // 가장 왼쪽의 값을 pivot으로 지정, 실제 비교 검사는 start+1 부터 시작
    int pivot = start;
    int lo = start + 1;
    int hi = end;
    
    // lo는 현재 부분배열의 왼쪽, hi는 오른쪽을 의미
    // 서로 엇갈리게 될 경우 while문 종료
    while (lo <= hi) {
      while (lo <= end && arr[lo] <= arr[pivot]) // 피벗보다 큰 값을 만날 때까지
        lo++;
      while (hi > start && arr[hi] >= arr[pivot]) // 피벗보다 작은 값을 만날 때까지
        hi--;
      if (lo > hi)				 // 엇갈리면 피벗과 교체
        swap(arr, hi, pivot);
      else
        swap(arr, lo, hi);			 // 엇갈리지 않으면 lo, hi 값 교체 
      }
	
    // 엇갈렸을 경우, 
    // 피벗값과 hi값을 교체한 후 해당 피벗을 기준으로 앞 뒤로 배열을 분할하여 정렬 진행
    quickSort(arr, start, hi - 1);
    quickSort(arr, hi + 1, end);

  }

  private static void swap(int[] arr, int i, int j) {
    int temp = arr[i];
    arr[i] = arr[j];
    arr[j] = temp;
  }
}
```

<br/><br/>

## 탐색 알고리즘

### 선형 탐색 (Linear Search):
주어진 배열에서 원하는 값을 찾는 가장 기본적인 탐색 알고리즘
시간 복잡도: O(n)

<img src="https://kwonsoonwoo.github.io/assets/cs50/%EC%84%A0%ED%98%95%ED%83%90%EC%83%89%EC%98%88%EC%8B%9C.png"  width="50%" title="탐색"/>

```java
public static int linearSearch(int[] arr, int target) {
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] == target) {
            return i; // 원하는 값이 발견되면 인덱스 반환
        }
    }
    return -1; // 원하는 값이 발견되지 않으면 -1 반환
}
```
### 이진 탐색 (Binary Search):
정렬된 배열에서 원하는 값을 빠르게 찾는 알고리즘
시간 복잡도: O(log n)

<img src="https://thebook.io/img/006950/327.jpg" width="80%" title="이진탐색"/>

```java
public static int binarySearch(int[] arr, int target) {
    int left = 0;
    int right = arr.length - 1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2;
        
        if (arr[mid] == target) {
            return mid; // 원하는 값이 발견되면 인덱스 반환
        } else if (arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return -1; // 원하는 값이 발견되지 않으면 -1 반환
}
```

<img src="https://images.velog.io/images/dgk089/post/4831dacc-e64a-43b0-88a5-4ed2f633a70f/%EC%BA%A1%EC%B2%98.PNG"  width="50%" title="탐색"/>
