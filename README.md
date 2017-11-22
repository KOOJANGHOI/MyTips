# MyTips


# mac terminal --> ubuntu ssh connection

1. 가상머신 종료
2. vm setting->네트워크 에서 호스트 전용 어댑터 추가
3. 가상머신 setting -> 네트워크 -> 추가적인 어탭터에 호스트전용 어댑터 추가 + 설정
4. 가상머신에서 ifconfig
5. sudo ifup [호스트전용 어탭터 추가시 ip주소]
6. terminal 에서 ssh [hostname]@[ip address]
7. 
