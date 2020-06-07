# [네트워크](https://github.com/ppurx/PrepareInterview/blob/master/Network)
  ## OSI 7계층
      - 개요 : 온라인 통신 시 문제점확인을 좀더빠르게 하기위해 만든 7계층의 layer
      - 계층별 설명     
        - 물리 : 통신 케이블, 리피터, 허브
        - 데이터링크 : 브릿지나 스위치를 통해 맥주소를 가지고 물리계층에서 받은 정보를 전달함.
        - 네트워크 : 주소부여(IP), 경로설정(Route)
        - 전송 : 데이터 패킷화하여 TCP / UDP 로 전송
        - 세션 : TCP/IP 세션을 만들고 없애는 책임 (운영체제에서 함)
        - 표현 : 포장/압축/암호화
        - 응용 : 네트워크 소프트웨어 UI 부분, 사용자의 입출력(I/O)부분
      
  ## TCP/IP 모델
      - 개요 : OSI7계층을 좀더 압축하여 표현
      - 계층별 설명
        - 응용 : tcp/ip 기반의 응용프로그램 (HTTP, FTP, Telnet, DNS, SMTP)
        - 전송 : 데이터 패킷화하여 TCP / UDP 로 전송 (osi7 layer의 전송계층과 동일) 
        - 인터넷 : IP 패킷을 전송하는 기능 및 라우팅 기능을 담당 (osi7 layer 네트워크계층과 동일)
        - 네트워크 접근 : (osi7 layer 의 물리+데이터링크)
        
  ## 웹통신 흐름
  
  ## TCP - UDP
    - TCP : 연결형 , 신뢰성 , handshake(연결시 3way, 해제시 4way) 1:1
    - UDP : 비연결형, 비신뢰성, no-handshake, 1:1 / 1:N
    
  ## 3Way , 4Way Handshake
    - TCP 통신시 사용
    - 3way : 연결 시 connect -> connected -> data transport
    - 4way : 해제 시 fin -> ack -> fin -> ack
  
  ## DNS 서버
    - internet 통신시 우리는 domain을 사용한다(www.naver.com) 도메인으로 바로 목적지를 찾아갈수 없기때문에 browser -> os로 도메인을 전달하고 os에서 DNS 서버에서 실제 통신 할 IP를 가져온다 (nslookup명령어 사용)
   
