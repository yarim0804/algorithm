# algorithm
알고리즘 세미나

## 알고리즘 이해와 기초

### 알고리즘의 정의: 알고리즘은 명확하게 정의된 단계별 절차로 문제를 해결하기 위한 방법
### 알고리즘의 중요성
  - 문제 해결: 알고리즘은 복잡한 문제를 단순하고 구체적인 단계로 분해하여 해결하는 데 도움
  - 자원 관리: 특히 대용량 데이터 처리나 실시간 응용 프로그램에서 중요
  - 시간과 공간 복잡성: 효율적인 알고리즘을 개발하면 프로그램 실행 속도를 향상시키고 메모리 사용을 최적화
  - 보안과 암호화: 알고리즘은 데이터 보안과 암호화 분야에서 핵심적인 역할

## 빅오 표기법
<img src="https://blog.kakaocdn.net/dn/umDDr/btqYhz5p1ZN/pULPOIs1zk2kA5QykgYEeK/img.png" width="50%" title="빅오표기법"/>
<img src="https://park-answer.netlify.app/static/893fa1e138e04a1c88f56cfb86793e6b/2a195/big-o-table.png" width="50%" title="빅오표기법"/>
<img src="https://blog.kakaocdn.net/dn/byv7cU/btrwGj2VMnK/W7Edg2M8b4VoTw3QD4J221/img.jpg" width="50%" title="빅오표기법"/>



- O(1) : 입력값에 상관없이 일정한 실행시간을 최고!의 알고리즘이라 할 수 있다. 하지만 상수 시간에 실행된다 해도 상수값이 상상 이상으로 클 경우 사실상 일정한 시간의 의미가 없다. 최고의 알고리즘이 될 수 있지만 그만큼 신중해야 한다. 예:) 스택에서 Push, Pop
- O(log n) : 로그는 매우 큰 입력값에서도 크게 영향을 받지 않는 편이다. 매우 견고한 알고리즘으로 이진 탐색의 경우가 이에 해당한다. 예:) 이진트리
- O(n) : 알고리즘을 수행하는데 걸리는 시간은 입력값에 비례한다. 이러한 알고리즘을 선형 시간 알고리즘이라 부른다. 정렬되지 않은 리스트에서 최대 또는 최솟값을 찾는 경우가 해당되며 모든 입렵값을 적어도 한 번 이상은 살펴봐야 한다. 예:) for문
- O (n log n) : 병합 정렬등의 대부분 효율이 좋은 알고리즘이 이에 해당 한다. 아무리 좋은 알고리즘이라 할지라도 n log n 보다 빠를 수 없다. 입력값이 최선일 경우, 비교를 건너 뛰어 O(n)이 될 수 있다. 예:) 퀵, 병합, 힙 정렬
- O(n^2)  : 버블 정렬 같은 비효율적인 정렬 알고리즘이 이에 해당 한다. 예:) 이중for문, 삽입, 버블, 선택정렬
- O(2^n) : 피보나치의 수를 재귀로 계산하는 알고리즘이 이에 해당 한다. n^2와 혼동되는 경우가 있는데 2^n이 훨씬 더 크다. 예:) 피보나치 수열
- O(n!) : 가장 느린 알고리즘으로 입력값이 조금만 커져도 계산이 어렵다.

## 정렬 알고리즘

필요성: 데이터 정리와 검색을 용이하게 만듦

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
배열을 정렬된 부분과 정렬되지 않은 부분으로 나누고, 정렬되지 않은 부분의 원소를 정렬된 부분에 삽입하는 알고리즘입니다.
시간 복잡도: O(n^2)

```
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




## 탐색 알고리즘

### 선형 탐색 (Linear Search):
주어진 배열에서 원하는 값을 찾는 가장 기본적인 탐색 알고리즘입니다.
시간 복잡도: O(n)

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
정렬된 배열에서 원하는 값을 빠르게 찾는 알고리즘입니다.
시간 복잡도: O(log n)

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

## 그래프 알고리즘

그래프 개념: 정점과 간선으로 이루어진 그래프의 기본 개념을 소개합니다.
최단 경로 알고리즘: 다익스트라 알고리즘은 단일 출발지에서 모든 노드까지의 최단 경로를 찾습니다.
그래프 탐색: 깊이 우선 탐색 (DFS)와 너비 우선 탐색 (BFS)을 그래프에서 어떻게 활용하는지 설명합니다.

```java
import java.util.*;

class Graph {
    private int V; // 노드 수
    private LinkedList<Integer> adjList[]; // 인접 리스트

    public Graph(int v) {
        V = v;
        adjList = new LinkedList[v];
        for (int i = 0; i < v; ++i) {
            adjList[i] = new LinkedList<>();
        }
    }

    // 무방향 그래프에서 간선 추가
    public void addEdge(int v, int w) {
        adjList[v].add(w);
        adjList[w].add(v);
    }

    // 깊이 우선 탐색 (Depth-First Search) 구현
    public void DFS(int start) {
        boolean visited[] = new boolean[V];
        DFSUtil(start, visited);
    }

    private void DFSUtil(int v, boolean visited[]) {
        visited[v] = true;
        System.out.print(v + " ");

        for (Integer neighbor : adjList[v]) {
            if (!visited[neighbor]) {
                DFSUtil(neighbor, visited);
            }
        }
    }

    // 너비 우선 탐색 (Breadth-First Search) 구현
    public void BFS(int start) {
        boolean visited[] = new boolean[V];
        LinkedList<Integer> queue = new LinkedList<>();

        visited[start] = true;
        queue.add(start);

        while (queue.size() != 0) {
            start = queue.poll();
            System.out.print(start + " ");

            for (Integer neighbor : adjList[start]) {
                if (!visited[neighbor]) {
                    visited[neighbor] = true;
                    queue.add(neighbor);
                }
            }
        }
    }
}
```

```java
public class GraphExample {
    public static void main(String[] args) {
        Graph graph = new Graph(6);
        
        graph.addEdge(0, 1);
        graph.addEdge(0, 2);
        graph.addEdge(1, 3);
        graph.addEdge(2, 4);
        graph.addEdge(3, 5);

        System.out.println("Depth-First Search (DFS) starting from node 0:");
        graph.DFS(0);

        System.out.println("\nBreadth-First Search (BFS) starting from node 0:");
        graph.BFS(0);
    }
}
```
