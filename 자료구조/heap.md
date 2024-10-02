# 1. 힙(heap)이란?   
   완전 이진 트리, 우선순위 큐 (Priority Queue)         
   최소 힙, 최대 힙 존재. 기본은 최소 힙 (최소힙 에서 최대 힙으로 변환 시, -부호를 붙이면 쉽게 변경 가능)             
   왼쪽에서 오른쪽으로 채워 넣음     
   가장 작은 원소가 루트 노드, 자식 노드는 부모 노드보다 같거나 커야한다.            
   ![image](https://github.com/user-attachments/assets/32234927-7e9e-4aef-b46e-ce976109d8cd)          

  
## 1.1 heappush       
힙 구조 배열에의 끝에 새로운 원소를 넣음    
![image](https://github.com/user-attachments/assets/fc73c807-e639-4f16-b57c-8e6cb3a03b9c)          
          
1) 가장 끝에 새 값을 추가                     
2) 추가한 원소의 인덱스를 구함 -> 배열 크기 (배열 마지막 번호가 인덱스일 테니까)                           
3) 부모 인덱스를 구하여 값을 비교 -> 부모 인덱스 배열 크기 // 2          
4) 새 값이 부모의 값보다 작으면 값을 교환            
4-1) 인덱스 갱신 후, 루트에 도달할 때 까지 3번 부터 반복      
5) 새 값이 부모의 값보다 크거나 같으면 종료     
               
```
     3
  4    6
8 5  7


heap = [3,4,6,8,5,7]

2 추가

3,4,6,8,5,7,2

len = 7-1

idx = 0~6


while len> 0:
부모노드 구하기

parent = (len-1)#인덱스가 0부터 시작하니까 -1 // 2 = 2


heap[parent] =  6 -> 맞음

if h[p] > h[len]: 
 	h[p], h[len] = h[len], h[p]
	
	len = p

else:
	break

```



## 1.2 heappop    
  힙을 제거, 보통 처음 힙이 pop됨        
![image](https://github.com/user-attachments/assets/938d7da4-9f2b-4cf0-bbc7-5d3dd3b7e1fd)            
               
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



![image](https://github.com/user-attachments/assets/037ae203-873c-48a5-bc60-c6006d6a51dc)
  

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
    last = len(arr) // 2 - 1  # 마지막 부모 노드의 인덱스
    for current in range(last, -1, -1):  # 역순으로 부모 노드를 처리
        # 힙 속성을 만족하도록 자식 노드와 비교하며 조정
        while True:
            child = current * 2 + 1  # 왼쪽 자식 노드 인덱스
            if child >= len(arr):  # 자식 노드가 배열의 길이보다 크면 종료
                break
            sibling = child + 1  # 오른쪽 자식 노드 인덱스
            if sibling < len(arr) and arr[child] > arr[sibling]:  # 오른쪽 자식이 더 작으면 교환
                child = sibling
            if arr[current] > arr[child]:  # 부모가 자식보다 크면 교환
                arr[current], arr[child] = arr[child], arr[current]
                current = child  # 교환 후 자식 노드로 이동하여 계속 힙 구성
            else:
                break  # 힙 속성을 만족하면 종료
```









출처: https://wikidocs.net/book/9059
