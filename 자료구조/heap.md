# 1. 힙(heap)이란?   
   완전 이진 트리, 우선순위 큐 (Priority Queue)         
   최소 힙, 최대 힙 존재. 기본은 최소 힙        
   왼쪽에서 오른쪽으로 채워 넣음
   가장 작은 원소가 루트 노드, 자식 노드는 부모 노드보다 같거나 커야한다.          
   ![image](https://github.com/user-attachments/assets/4752479b-8bb3-4918-adba-839e3a480d2f)

  
## 1.1 heappush


## 1.2 heappop    
  힙을 제거, 보통 처음 힙이 pop됨        
  ![image](https://github.com/user-attachments/assets/950d2401-22f7-4390-a62f-b32071c58e73)    
       
 1) heap이 비어있으면 emtpy     
2) 루트노드만 있으면 그대로 반환        
3) 루트노드 값 임시 저장 -> 맨 처음 값 pop이기 때문            
4) 힙에서 pop해서 마지막 값을 루트에 넣음     
5) 현재 노드와 자식 노드의 인덱스로 0,1을 대입     
6) 자식 노드의 인덱스가 heap의 길이보다 작으면 반복     
6-1) 오른쪽 노트의 인덱스를 구함 (+1 형제 노드)    
6-2) 현재 노드의 값을 왼쪽 오른쪽 노드와 비교 (부모노드를 자식과 형제 노드랑 비교)   
6-3) 현재 노드값이 자식노드값 보다 크면 더 작은 자식 노드와 교환   
6-3-1) 현재 노드의 인덱스를 자식 노드로 갱신, 자식 노드 인덱스를 다시 구함          
6-4) 현재 노드의 값이 자식 노드보다 작으면 종료 

  ```
  [3, 4, 6, 8, 5, 7]

pop_data = 3, 
heap[0] = 7

[7,4,6,8,5]

0 1 왼쪽 자식 노드
7 4

child = 1

child < len(heap) 

sibling =child + 1 -> 오른쪽 형제 노드 idx 2 (6)

4 6
if 형제 노드 idx < len(heap) and 자식 값 > 형제값:
	형제 값중 더 작은 값을 자식 idx로 바꿈
	child = sibling
	
currnet = 7 child = 4
if heap[current] > heap[child]:
	heap[current], heap[child] = heap[child], heap[current]
	현재가 자식보드 크면 체인지
		
	[4,7,6,8,5]
	current = child 인덱스 이동
	#current = 1 -> 7
	
	child = current *2 +1 -> 자식 노드 인덱스로 변경 -> 완전 2진 트리이기 때문에 공식 가능
	#child = 1 *2 = 2 + 1 = 3 -> 8
	
	반복

  ```
       
```
def heappop(heap):
    if not heap:
        return "Empty Heap!"
    elif len(heap) == 1:
        return heap.pop()

    pop_data, heap[0] = heap[0], heap.pop()
    current, child = 0, 1
    while child < len(heap):
        sibling = child + 1
        if sibling < len(heap) and heap[child] > heap[sibling]:
            child = sibling
        if heap[current] > heap[child]:
            heap[current], heap[child] = heap[child], heap[current]
            current = child
            child = current * 2 + 1
        else:
            break
    return pop_data
```


## 1.3 heapify    
힙이 아닌 구조를 힙으로 변경        



![image](https://github.com/user-attachments/assets/f639ef47-f969-4650-b32b-639f3000ea0e)      

```
heapify

[6, 2, 5, 1, 3, 4]

     6
  2     5
1 3   4

len(arr) = 6

last = len(arr) // 2 -1 -> 마지막 트리 상위 노드 = 2 (5)

마지막 상위노드 인덱스 부터, 자식 노드들 까지 

for current in range (last, -1, -1):
				시작 종료 스텝
					-1이면 종료, (0까지), -1씩 감소
		# current = 처음 2 부터 시작 , 1, 0, 
	while current <= last: #현재값이 마지막 트리 상위노드랑 같거나 작으면 계속 돎 
		child = current * 2 +1  # 자식 노드 인덱스 구하는 공식 # 암기  
		sibling = child + 1  # 자식 형제 노드
		
		if sibling < len(arr) and arr[child] > arr[sibling]: # 자식 노드가 형제 노드보다 크면
			child = sibling  # 형제 자식 인덱스 바꿈 -> 작은수 인덱스를 가져오는 것임
		
		if arr[current] > arr[child]: # 자식노드가 현재노드보다 작으면 (부모노드)       # 5 ,  4
			arr[current], arr[child] = arr[child], arr[current] # 서로 바굼        
			current = child
	
		
```
```
def heapify(arr):
    last = len(arr) // 2 - 1
    for current in range(last, -1, -1):
        while current <= last:
            child = current * 2 + 1
            sibling = child + 1
            if sibling < len(arr) and arr[child] > arr[sibling]:
                child = sibling
            if arr[current] > arr[child]:
                arr[current], arr[child] = arr[child], arr[current]
                current = child
            else:
                break
```









출처: https://wikidocs.net/book/9059
