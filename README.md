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