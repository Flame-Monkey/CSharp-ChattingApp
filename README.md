# 정리
- 채팅서버를 구현해봄
- 프로토콜을 설계해봤으며 바이트 스트림 수신에 대하여 고민해봄
- 대부분 GPT를 활용하였지만 웹서버(ASP.NEt Core)와 데이터베이스(PostgrSQL)를 사용해봄
- Azure를 통해 리눅스 서버에 원시적인? 배포를 해봄
- 송신시에 동시성 관리를 해줘야 함을 깨달았으며(지금 구조에선 송신 바이트 스트림이 꼬이는 경우가 생김) 현재 구조에서 송신 메시지가 많이 쌓이면 Send 함수 2개가 서로를 반복적으로 호출해 스택이 터짐
- 소감: 완성도는 많이 떨어져 난잡하지만 채팅서버 구현, DB 사용에 대한 감을 잡을 수 있었고 소켓프로그래밍 시에 유의해야 할 점, 설계 방향을 생각해볼 수 있었음

# 웹서버 
appsettings.json에서 데이터베이스 설정  
dotnet build   
dotnet ef migrations add InitialCreate  
dotnet ef database update  

# 채팅 서버 
MongoDB는 주석처리 해놓음  
program.cs에서 postgrsql 설정 문자열 세팅  
따로 Init함수 만들어놔서 데이터베이스까지만 만들어놓으면 알아서 테이블 생성됨  

# 주소 설정
클라이언트측 client.cs의 62번째줄 (LoginAsync메소드) ipa = 웹서버 주소, 몇 줄 밑에 포트넘버 하드코딩 돼있음  
  

채팅서버측 MessageProcessor.cs의 GetUserInfoFromWeb 함수에 웹서버 주소 하드코딩 돼있음   
Program.cs의 11번째줄, 서버 주소 

웹서버측  appsettings.json에 채팅 서버 주소 
