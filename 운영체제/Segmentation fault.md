1. Segmentation Fault    
   잘못된 메모리 참조 때문에 일어남     
     
   1) NULL값을 가리키는 포인터에 접근            
   2) 할당 받은 메모리 이외의 공간을 건드린 경우:                 
      메모리 누수: 동적 할당에서 할당 받지 않은 메모리 접근, 동적으로 할당된 메모리를 해제하지 않고 계속해서 사용할 경우                 
      스택 오버플로우: 스택 메모리를 너무 많이 사용하여 스택 영역을 벗어나는 경우     
      배열 인덱스 오류: 배열의 인덱스를 벗어나는 위치에 접근할 때          
   4) 더 이상 존재하지 않는 메모리 영역을 가르킬 경우 (잘못된 포인터 참조)          
   5) read-only 메모리 영역에 쓰려고 하는 경우 (권한이 없는 경우)           
