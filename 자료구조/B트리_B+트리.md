## 1. 다원 탐색 트리 (Multiway Search Tree) or M원 검색 트리 (M-way Search Tree)    
  이진 탐색 트리의 차수는 2라서 트리의 높이가 커지는 문제점 존재    
  이러한 문제를 차수를 2에서 m개로 늘려 문제 해결    
  각 노드들은 m-1 개의 레코드와 m개의 서브트리를 가질 수 있음   
  k개의 서브트리를 가지는 노드는 k-1개의 요소를 갖음 (k<=m)     
  이진 탐색 트리의 확장 형태로 높이를 줄일 수 있음    
  각 노드안에서는 정렬되어 있음     
       
  - 장점    
    트리의 높이 h -> 트리 속도 O(h) 때문에, h 를 낮춤으로 속도를 높일 수 있음 -> 노드에 저장하는 요소수를 늘려 높이 줄임         
           
  - 단점    
    스스로 균형을 유지하지 못해 불균형이 발생할 수 있음 -> 검색 성능 떨어짐    
    이러한 단점을 보완하려고 나온게 B-트리     
          
  - 이진 탐색 트리, 다원 탐색 트리 구조 그림      
    ![image](https://github.com/user-attachments/assets/08e87782-25c3-458a-bf42-5f3eb157743f)      
           
## 2. B-트리 (B-Tree)         
   M원 검색 트리로 높이를 줄일 수 있지만, 균형이 맞지 않는 문제가 있음. 이러한 문제를 B-트리에서 해결                 
   모든 단말 노드는 같은 레벨에 있음       
   루트 노트와 단말 노드를 제외한 모든 노드는 M/2이상 M이하의 자식을 갖음      
   루트 노드는 적어도 2개의 자식을 갖음     
   각 노드의 원소수는 최소 M/2-1개 ~ 최대 M-1개를 가짐      
   (최소 개수 이하: underflow, 최대 개수 이상: overflow)            
   B-트리 시각화 사이트: https://www.cs.usfca.edu/~galles/visualization/BPlusTree.html       
          
  - 데이터 삽입      
     데이터느 항상 단말 노드에 추가됨     
     단말 노드에 여유 공간이 있으면 삽입, 없으면 분할
             
    * 분할 규칙:      
      루트 노드가 가득 찼을 때:          
      ![image](https://github.com/user-attachments/assets/c010d71f-b21b-480b-ae63-509bf25368ac)       
       
      루트 노드 이외 노드가 가득 찼을 때:             
      ![image](https://github.com/user-attachments/assets/cd577e55-312b-4ff7-ae61-2a7e6fb76d72)

      예) 차수가 3인 B-트리 데이터 삽입 (1, 8, 4, 6, 13, 5, 27, 9)
      각 노드의 원소 개수: 0.5개 ~ 2개 사이 (M/2-1 ~ M-1)
      노트의 자식 개수: 1.5 이상 ~ 3 이하 (M/2 ~ M)
   
      1, 8 삽입     
      ![image](https://github.com/user-attachments/assets/5afbe11d-91d6-4f16-b16c-7b34a4e29352)      
      4 삽입 후 분할: 원소 개수 2개 초과     
      ![image](https://github.com/user-attachments/assets/d22b1d32-ba9b-44b5-8956-5e44525aa524)         
      6 삽입: 자식 개수 최대 3개             
      ![image](https://github.com/user-attachments/assets/953917a8-1d07-46bc-a1c0-d8c2f1dff236)           
      13 삽입 후 분할: 자식 개수 4개 됨                
      ![image](https://github.com/user-attachments/assets/0b701962-efc7-47c4-a9bc-2262ae843834)          
      5 삽입              
      ![image](https://github.com/user-attachments/assets/c1ef6195-ff5a-4aba-b049-7e01306699b6)             
      27 삽입            
      ![image](https://github.com/user-attachments/assets/87c163bc-85d1-4de7-b730-ed318539e37e)            
      9 삽입 후 분할: 자식 개수 4개 됨         
      ![image](https://github.com/user-attachments/assets/6fcb11e8-2b75-4105-a619-220ab1e57bc4)         
          
           
  - 데이터 삭제  
    삭제 시 B-트리 조건을 만족하지 않으면 조건을 만족하게 수정해야 함         
                
    예1) 단말 노드 삭제         
    빌리기: B데이터 삭제 시, 형제 노드가 m/2-1개보다 많은 데이터를 가지고 있을 경우            
    ![image](https://github.com/user-attachments/assets/e515dece-7124-4f9f-a17d-628a7dfbb082)       
                        
    결합하기: 형제 노드에서 빌릴 수 없는 경우 결함          
    ![image](https://github.com/user-attachments/assets/cd8d8b62-955c-418b-96d3-0e831d84f965)            
     
    예2) 8 삭제 예시           
    왼쪽 서브 트리 중 가장 큰 값인 6과 자리 변경                 
    ![image](https://github.com/user-attachments/assets/14122ef2-09e6-4b9c-b56a-560122be886c)              
               
    ![image](https://github.com/user-attachments/assets/adb52a7a-c5da-460c-8bf1-e537f1ff6e5e)
          
    ![image](https://github.com/user-attachments/assets/131f36c9-2f55-4c99-8da2-8171beb389f7)      
     
## 3. B+트리       
B-트리의 변형된 형태, 효율적인 삽입, 검색, 삭제를 추구
삽입, 삭제 연산이 단말 노드에서만 이루어지며 단말 노드끼리 연결 리스트로 연결됨   
단말 노드가 순차 집합으로 연결되어 있기 때문에 순차적인 탐색에 유리함.      
     
![image](https://github.com/user-attachments/assets/4a236cb8-6ac7-4f95-8217-f1d4d2681c70)      


- 데이터 삽입
  1) 단말 노드가 가득 찼을 경우 -> 중간 값을 부모 노드로 올리고 분할
  예) 4 삽입         
![image](https://github.com/user-attachments/assets/9787ed45-a37c-40b3-a829-bf3591b90ecd)    
2 3,4로 분열, 부모 노드 중간 값인 3을 올림

  2) 내부 노드가 가득찼을 경우    
  예) 5 삽입          
   ![image](https://github.com/user-attachments/assets/1fe8cf95-b4ed-4e7b-a575-f08afec1ad30)    
    ![image](https://github.com/user-attachments/assets/c0f5a618-90cd-4491-a2fe-5e44ac5ebfad)    
     3 4,5 노드로 분열, 중간 값 4를 부모 노드로 올림     
     ![image](https://github.com/user-attachments/assets/ab9eb101-560c-4afa-bd8e-092798ea18e5)     
     부모 노드도 꽉 찾기 때문에 중간 값 3을 부모로 올리고 2, 4 분열    
     index set은 3,4로 분열 되지 않음       
         
- 데이터 삭제   

 
  
   


    
 

     
    







      



  
