# 1. OAuth 2.0   
  Open Authorization 2.0    
  인증을 위한 개방형 표준 프로토콜      
  Third-party 프로그램에게 리소스 소유자를 대신하여 리소스 서버에서 제공하는 자원에 대한 접근 권한을 위임       
  구글, 페이스북, 카카오, 네이버 등에서 제공하는 간편 로그인 기능                 
        
## -역할     
  - Resource Owner: 리소스 소유자, 자격을 승인하는 주체, 즉 로그인할 사용자, resource owner는 클라이언트를 인증 하는 역할 수행, 인증 완료 후 클라이언트에게 자격 부여     
  - Client: 리소스를 사용하고자 접근 요청하는 애플리케이션      
  - Resource Server: 리소스 소유자의 정보가 저장되어 있는 서버    
  - Authorization Server: 권한 서버, 인증/인가를 수행하는 서버, Access token 발급    
         
## - 용어     
 - Authentication: 인증, 접근 자격 검증 단계     
 - Authorization: 인가, 자원 접근 권한을 부여하고, access token 제공      
 - Access Token: 리소스 서버에게 소유자의 정보를 획득할 때 사용되는 token     
 - Refresh Token: access token 만료 시, 이를 재발급 받기 위한 용도로 사용하는 token    
          
## - 권한 부여 방식       
OAuth 2.0 프로토콜에서는 다양한 클라이언트 환경에 적합하도록 권한 부여 방식에 따른 프로토콜 4가지로 구분     
     
1) Authorization Code Grant: 권한 부여 승인 코드 방식    
권한 부여 승인을 위해 자체 생선한 Authorization code를 전달하는 방식.    
        
2) Implicit Grant: 암묵적 승인 방식         
자격 증명을 안전하게 저장하기 힘든 클라이언트에게 최적화된 방식      
            
3) Resource Owner Password Credentials Grant: 자원 소유자 자격증명 승인 방식      
username, password로 access token을 받는 방식.    
       
4) Client Credentials Grant: 클라이언트 자격 증명 승인 방식      
클라이언트의 자격증명만으로 access token을 획득하는 방식    
  
   
