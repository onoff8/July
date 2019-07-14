# EIGRP

## 24장 EIGRP

EIGRP

    Link  -  state 

1.Link 변화시 인접성을 맺은 모든 router 에게 변화된 내용만 update 를 한다 (네트워크 변화시, triggered basis)

-update 를 위한 대역폭 소비량이 적다
-update 를 위한 CPU 소모율이 적다
-구조가 복잡 (인접성)
-확장성이 좋다
-변화에 적응이 빠르다

2.classless routing protocol 
-VLSM,CIDR 지원

3. multicast  update  (224.0.0.5... ospf 5 ripv2 9 eigrp 10 요렇게 3가지 방식만 멀티캐스트 업데이트를 함)

OSPF  :  224.0.0.5 ~ 6

6.AD : 5(summary)  90(internal)   170(external)

7.균등,비균등 로드 분산 둘다 지원
(기본은 균등 로드 부산만 지원 , 비균등 로드 분산을 하려면 variance 값을 조절해줘야 한다 ,기본값 1이고 1은 균등 분산이며 비균등 범위는 2 ~ 128 )


[참고]
비균등 로드 분산을 하려면 2가지의 조건이 만족 되어야 한다

1>variance 값을 이용해서 최적 경로의 metric 보다 비균등 로드 분산 하려는 경로의 metric 을 작게 만들어 준다

2>최적 경로의 FD 보다 작은 AD 값을 가지고 있어야 한다(후속 경로)

8.metric 

-K metric : K-value , K상수

  K1=1  , K2=0 , K3=1 , K4=0 , K5=0 

-Vector metric

 bandwidth  : 대역폭 (차선 즉 속도) 최소 bandwidth 가용밴드위드스
 delay         : 지연
 Reliability   : 신뢰성 
 Load          : 과부하
 MTU          : 전송 최대 크기 유닛 maximum transmission unit (max 1500byte)


(K1 x Bandwidth) + [(K2 x Bandwidth) / (256 - Load)] + (K3 x Delay)


결과적으로 Bandwidth , Delay만 사용함.

10^7/bw * 256 + Delay/10 * 256 = 32bit

 BW  : 최소 BW
delay : 합


###
9.인접성

Hello : 인접성을 맺고 유지(인접성의 조건:K-value , AS -number,인증) 
           유지 시간이 3배 (hold : hello 수신 대기 시간)
           router eigrp ? -- as no
           router bgp  --- as no

Update : 정보를 update 할때 

Query : 네트워크에 장애가 생겼을 경우 정보를 요청 
+update 를 준 router에게만 Query 를 요청 

Reply : Query 에 대한 응답

Ack : 수신 확인 , 승인


인접성이 해지 되는 경우

1.hold 시간 안에 hello 를 수신하지 못하는 경우는 인접성을 해지 한다

2.update , Query ,Reply 는 ack 를 수신해야 한다
   수신하지 못하면 16번을 재전송을 하고 그래도 수신하지 못하면 인접성을 해지 한다

3,Query 를 보내면 reply 를 수신해야 한다
   수신하지 못하면 SIA(Stuck In Active) 로 3분이 지나면 인접성이 해지가 된다

10. 3개의 table 

Neighbor  table  : 네이버에 관한 정보(인접성을 맺은 router 의 정보)   :  sh  ip eigrp nei

Topology  table : 네이버에게 받은 정보 (인접성을 맺은 router 를 통해서 들어오는 network 정보)  : sh ip eigrp to

Routing table  : 최적 경로가 등록된 table  : sh ip route


FD = Metric :출발지 router 부터 목적지 router 까지의 경로값 
feasible distance

AD = Source Metric :출발지 router랑 인접성을 맺은router부터 목적지router까지의 경로값 advertized distance 광고거리


S(최적 경로) 와 FS (후속 경로) 선출 기준

1.FD 값이 가장 작은 경로가 S(최적 경로) 가 된다

2.FS (후속 경로)는 S(최적 경로) 의 FD 값보다 작은 AD 값을 가진 경로
![](./attatched/capture2.png)

11.Network type
                            Hello          Hold 
                      
point-to-point           5              15 
broadcast                  5              15
nonbroadcast           60            180

###
12.설정

classful 하게 설정

172.16.1.0 /24
13.13.10.0 /24
13.13.12.0 /24

router eigrp 100
net 172.16.0.0
net 13.0.0.0
no au


classless 하게 설정

172.16.1.0 /24
13.13.10.0 /24
13.13.12.0 /24

router eigrp 100
net 172.16.1.0 0.0.0.255
net 13.13.10.0 0.0.0.255
net 13.13.12.0 0.0.0.255  -- Wildcard Mask (EIGRP , OSPF , ACL) => 설정을 최소화 
no au

[설정과 동작은 별개]

Wildcard Mask (EIGRP , OSPF , ACL)
=> 설정을 최소화 

Wildcard Mask  와 Subnetmask 의 공통점

=> ip 를 규정해준다

1.표기법의 차이
Wildcard Mask 를 구하는 방법
=>  공통된 부분(공통bit) 는 0 으로 고정
      공통된 부분(공통bit)가 아니면 1로 안고정

2.bit 의 불연속 가능 유무
S    불가능 

W    가능
**** 이진수 10진수를 바꾸는 방법은 각 각을 더하지만 공통된 부분은 1로하는 것으로 하는 반면 와일드카드의 공통부분은 0으로 처리한다는 점을 명심하자

192.168.0.0 /24 ~ 192.168.255.0 /24 에서 각각의 네트워크 ip 중에서 사용할수 있는 첫번째 ip만 지정하여라

subnet mask 인터넷 강의 듣고 할것

192.168.0.1 255.255.255.255
192.168.1.1 255.255.255.255
192.168.3.1 255.255.255.255

192.168.255.1 255.255.255.255
0. 0. 255.0  0 . 0 . 255. 0


192.168.1.1  0.0.0.254    => 홀수만 지정


192.168.1.00000000
192.168.1.00000010
192.168.1.00000100
~~~~~~~~~~~~~~
192.168.1.255 255.255.255.255
192.168.1.11111110

0 .0 .0. 0 0.0.0.254


192.168.1.0  0.0.0.254  => 짝수만 지정



192.168.1.129  /24 ~ 192.168.1.131  /24 

192.168.1.10000001
192.168.1.10000010
192.168.1.10000011

192.168.1.128  0.0.0.3
0.0.0.11111110  0.0.0.254
192.168.1.0


192.168.1.129  /24 , 192.168.1.131  /24


192.168.1.100000 0 1
192.168.1.100000 1 1

192.168.1.129  0.0.0.2

[주의]
단 ACL 에서만 bit 의 불연속이 가능하다 eigrp 와 ospf 는 불가능하다