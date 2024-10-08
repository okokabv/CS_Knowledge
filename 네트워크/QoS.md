1. Quality Of Service
  한정된 네트워크 자원 내에서 특정 트래픽이 일정수준의 성능, 속도를 보장받는 네트워크 기술     
  Network의 대역폭, 처리율, 지연율, 손실율 등을 관리하는 기술     
  서비스 이용자의 만족도를 결정하는 서비스 성능의 총체적 효과     
       
  - 필요성    
    품질요구: 다양한 서비스 관련 네트워크 서비스 품질을 보장하여 사용자 권리 보장(SLA)     
    서비스 다양화: 다양한 애플리케이션 출현 및 관련 트래픽의 다양화    
    고비용: 충분한 네트워크 자원 할당 및 설치를 위한 많은 비용 필요     
    고대역폭 및 고속처리: 대용량 처리를 위한 멀티미디어 서비스, 실시간 인터랙티브 서비스가 다수 출현      
       
  - 구성도
    라우터와 스위치 사이에 위치하여 내외부망 사이의 트래픽을 관리, 사용자 서비스 수준 확보               
    ![image](https://github.com/user-attachments/assets/f49df7b4-d54e-4020-a449-98f87ca9c4f8)

  - 관리기술      
    * Queue관리: 대기중인 작업들이 Queue 형태로 구성, 일련의 작업들을 특정 순서에 따라 처리       
      종류:            
            FIFO(First In First Out): FCFS(First Come First Served), 선입선출         
            CBQ(Class-Based Queuing): IP주소, 프로토콜 등에 따라 계층을 나눠 계층수서대로 처리, WFQ, CQ, PQ, CB-WFQ등 여러 queuing 관리 기법을 모두 하나의 기능으로 통합한 것       
            PQ(Priority Queue): 우선순위에 따라 개별 큐 처리                   
            FQ(Fair Queue): 개별 큐를 공정하게 라운드로빈 방식으로 처리         
            WFQ(Weighted Fair Queue): 큐에 특정 가중치를 둔 FQ의 변형
           
    * Traffic Shaping: 네트워크 망에 유입, 유출 되는 트래픽의 양 및 속도를 조절하는 기술               
      종류:           
            Leaky bucket 네트워크 혼잡을 회피하기 위해 패킷 버퍼를 이용하여 조절               
            Token bucket 패킷 토큰을 이용하여 네트워크 트래픽의 속도 조절        
            Hybrid Leaky와 Token 방식의 장점을 혼합         
        
    * Traffic Policing: 네트워크 트래픽의 혼잡을 미리 감지/폐기 방식으로 트래픽을 제어하는 기술                 
      종류:            
            RED(Random Early Detection): 네트워크 혼잡사항을 미리 감지하여 패킷 drop 수행
            WRED(Weighted RED): 대상 패킷의 가중치에 따라 Drop 수행
            Tail Drop: 패킷 버퍼에 설정된 임계치를 초과 할 경우 이후 패킷은 모두 drop
           
    * QoS 보장 기술: 통신망 전체에 해당         
      종류:                
            IntServ/RSVP: RSVP 프로토콜을 이용하여 라우터의 자원을 예약, 플로우 성능 보장, 비디오나 고대역폭의 멀티캐스트 메시지 전송을 위함, Intergrated service           
            DiffServ: 미리 정의된 패킷 등급에 따라 구분하여 서비스, IP헤더에 type of service 필드 값을 이용하여 ISP가 결정, Differentiated service            
            MPLS: 프레임에 라벨을 추가하여 2계층의 스위칭정보로 QoS 보장, Multi protocol labeling switch            
            CDN: ISP의 네트워크 하단에 여러 대의 캐시 서버를 설치            

  - 주요 지표     
    * 대역폭(Bandwidth): 특정 애플리케이션에 할당된 네트워크 자원의 양       
              일정 시간에 처리한 데이터의 총량을 가리키는 지표            
              대역폭이 부족한 경우 데이터를 압축하여 전송       
      제어 기법: Queuing, Shaping, Policing               
             
    * 지연(Delay): 서비스, 특정처리의 응답시 발생하는 지연, 발송 목적지까지의 경로에서 발생되는 지연, 지연시간이 크면 실시간성 감소   
      제어 기법: Queuing           
                  
    * 지터(Jitter): 신호가 네트워크를 통해 전달되는 과정에서 원래 신호로부터 왜곡되는 정도, 멀티미디어 트래픽에 있어서 지터는 치명적인 영향 존재, 연속지연(Serializaition Delay), 전달지연(Propagation Delay), 큐잉지연(Queuing Delay) 각 단계별 프로세싱과 딜레이가 발생       
      제어 기법: Queing     
      
    * 패킷 손실(Packet Loss): 네트워크에서 데이터를 전송하는 과정 중 패킷의 손실정도, 주된 원인응 네트워크 혼잡으로 인항 버퍼 오버플로우, 흐름제어 알고리즘이 임의적으로 패킷을 폐기, 혼잡이 방샐하면 중요도에 따라 임의로 패킷을 drop시켜 중요 애플리케이션의 보장을 확보   
     제어기법: Queuing, RED, WRED      
    
    
