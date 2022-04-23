# TCP(Transmission Control Protocol)
전송 제어 프로토콜은 인터넷 프로토콜 스위트(IP)의 핵심 프로토콜 중 하나로, IP와 함께 TCP/IP라는 명칭으로도 널리 불린다.   

# TCP특징
1. **신뢰성**있는 데이터 통신을 가능하게 한다.   
2. 양방향 통신 (3, 4 way handshake)

3. 순차 전송을 보장

 * TCP는 스트림 기반의 프로토콜이다.
 * 바이트 스트림의 형태로 데이터를 송-수신한다.   
 👉**스트림** : 운영체제에 의해 생성되는 가상의 연결 고리를 의미하며, 중간 매개자 역할을 한다.   

 ![logo](https://t1.daumcdn.net/cfile/tistory/2143A4485586C8DE2F)

4. 흐름 제어 ( Flow control )

* TCP의 Window필드를 사용한다.   
👉Window : 자신의 수신 버퍼 여유용량 크기를 통보하여 얼마만큼의 데이터를 받을 수 있는지 상대방에게 알려주어 흐름제어를 수행하게 되는 필드

* UDP는 흐름제어를 제공하지 않는다.   
👉UDP : 간단한 데이터를 빠른 속도로 전송하고자 비연결지향형 프로토콜이다.
* 양단간 통신에 있어 각 **노드의 성능(처리 속도 차이)** 에 따라 전송중인 데이터의 양을 조절한다.
* 데이터의 과도한 송-수신으로 인한 데이터의 손실을 방지한다.   
* 바이트 단위의 흐름제어를 위하여 번호와 시스템을 이용한다.   
+) stop and wait   
![logo](https://t1.daumcdn.net/cfile/tistory/9981123F5D1C1BF01D)   

송신측 A가 B에게 1개의 프레임을 송신하게 되면 B는 해당 프레임의 에러 유무를 판단하여 A에게 ACK를 보내게 된다.   
Stop and wait 방식은 구현 방식이 단순하며 송신측 내에 최대 프레임 크기의 버퍼를 1개만 잡아도 되지만 송신측이 ACK를 받을 때까지 다음 프레임을 받을 수 없으므로 전송 효율이 떨어지는 단점이다.   

+) sliding window   
수신 측에서 설정한 윈도우 크기만큼 송신 측에서 확인 응답(ACK) 없이 전송할 수 있게 하여 흐름을 동적으로 조절하는 제어 알고리즘
윈도우에 포함되는 모든 패킷을 전송하고, 전송이 확인되는 대로 윈도우를 옆으로 **옮겨(slide)** 다음 패킷들을 전송하는 방식 

![logo](https://blog.kakaocdn.net/dn/bnzBZn/btraJzk0X4D/KXnDLMrHR6rs4zE2fVqZmk/img.png)   

res는 색칠한 값을 다 더한 값의 결과이다.   

5. 혼잡 제어 ( Congestion Control )

* 망의 혼잡도를 고려하여 송신측에서 전송되는 데이터 양이 수신측에 의해서 조절될 수 있다.
* 흐름제어는 end-device간의 성능에 따라 제어되고 혼잡제어는 망 자체의 속도에 따라 제어된다.

6. 오류 감지 ( Error Detection )

* 헤더의 checksum 필드를 이용하여 이상유무를 확인한 후 정상인 경우 ACK 세그먼트를 전송한다.
* 바이트 단위로 오류 제어 매커니즘을 구현한다.
* 세그먼트 단위로 오류 감지를 수행한다.

👉checksum : 네트워크를 통해 전달된 값이 변경되었는지를 검사하는 갑으로 무결성을 제공한다. 

7. TCP의 PDU(Protocol data unit) = 세그먼트

8. TCP Header Flag field = ACK, SYN, FIN... (—TCP 연결 제어 및 데이터 관리)

9. 3 way handshake

* Client가 패킷 송신
* Server에서 ACK 송신
* ACK를 수신하지 못하면 재전송  

![logo](https://velog.velcdn.com/images%2Fseaworld0125%2Fpost%2Fb9018be9-bed1-4025-b9e8-a00eb27a9444%2Fimage.png)   

11. 4 way handshake

* 데이터를 전부 송신한 Client가 FIN 송신
* Server가 ACK 송신
* Server에서 남은 패킷 송신 ( 일정 시간 대기 )
* Server가 FIN 송신
* Client가 ACK 송신

![logo](https://velog.velcdn.com/images%2Fseaworld0125%2Fpost%2F18f493fc-ad2e-476c-aefd-0e4ed366eb86%2Fimage.png)   

12. TCP 헤더  

![logo](https://velog.velcdn.com/images%2Fseaworld0125%2Fpost%2Fbdd78e1a-7178-4bd4-b14f-e9c54cec14b9%2Fimage.png) 

