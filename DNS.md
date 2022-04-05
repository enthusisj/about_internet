# DNS란?
>도메인 네임 시스템(Domain Name System, DNS)은 호스트의 도메인 이름을 호스트의 네트워크 주소로 바꾸거나 그 반대의 변환을 수행할 수 있도록 위해 개발되었다.

예를 들면, 우리가 자주 접하는 naver.com, google.com, 모두 DNS을 가진 **DN(Domain Name)** 이라고 할 수 있다. -> 문자열의 탈을 쓴 IP라고 볼 수 있다.    

---------------------------------

>## **Domain Name의 정의**    
: 넓은 의미로는 네트워크상에서 컴퓨터를 식별하는 **호스트 명** 가리키며, 좁은 의미에서는 **도메인 레지스트리** 에게서 등록된 이름을 의미    

*도메인 레지스트리: 최상위 도메인에 등록된 모든 도메인 네임의 데이터베이스

## Domain Name의 구조
![logo](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fc1vqg8%2FbtqDcxNaGM9%2Fmk3I8siV0qoGEWg8GXm4QK%2Fimg.jpg)

 ###### 출처: 생활코딩   


도메인 네임은 위와 같이 구성되어 있다.    
Top-Level에 해당 하는 com은 상업적인 목적의 도메인을 뜻한다.   
이외에도 국가를 뜻하는 kr이나 공인된 단체를 뜻하는 org 등이 있다.

--------------------------------
## DNS의 작동원리
![logo](https://media.vlpt.us/images/goban/post/5717ceb7-79f2-41d3-86e5-7e48bfd6ac58/DNSLogic.png)

1. 웹 브라우저에 www.naver.com을 입력하면 먼저 Local DNS에게 "www.naver.com"이라는 hostname"에 대한 IP 주소를 질의하여 Local DNS에 없으면 다른 DNS name 서버 정보를 받음(**Root DNS** 정보 전달 받음)

### Root DNS란?
> 루트 네임서버는 인터넷의 도메인 네임 시스템의 루트 존이다. 루트 존의 레코드의 요청에 직접 응답하고 적절한 최상위 도메인에 대해 권한이 있는 네임 서버 목록을 반환함으로써 다른 요청에 응답한다. 전 세계에 961개의 루트 DNS가 운영되고 있다.   

2.Root DNS 서버에 "www.naver.com" 질의   

3.Root DNS 서버로 부터 "com 도메인"을 관리하는 TLD (Top-Level Domain) 이름 서버 정보 전달 받음   
> 여기서 TLD는 .com을 관리하는 서버를 칭한다.

4.TLD에 "www.naver.com"질의   

5.TLD에서 "name.com"관리하는 DNS 정보 전달

6."naver.com" 도메인을 관리하는 DNS 서버에 "www.naver.com" 호스트네임에 대한 IP 주소 질의   

7.Local DNS 서버에게 "응! www.naver.com에 대한 IP주소는 222.122.195.6 응답   

8.Local DNS는 www.naver.com에 대한 IP 주소를 캐싱을 하고 IP 주소 정보 전달

----------------------------
### 링크
[google](https://minemanemo.tistory.com/80)   
[naver](https://velog.io/@goban/DNS%EC%99%80-%EC%9E%91%EB%8F%99%EC%9B%90%EB%A6%AC)

