# 1. 힙(heap)이란?   
   완전 이진 트리, 우선순위 큐 (Priority Queue)         
   최소 힙, 최대 힙 존재. 기본은 최소 힙        
   왼쪽에서 오른쪽으로 채워 넣음
   가장 작은 원소가 루트 노드, 자식 노드는 부모 노드보다 같거나 커야한다.          
   ![image](https://github.com/user-attachments/assets/4752479b-8bb3-4918-adba-839e3a480d2f)

  
## 1.1 heappush


## 1.2 heappop    
  힙을 제거, 보통 처음 힙이 pop됨
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














출처: https://wikidocs.net/book/9059
