# MyTips


# mac terminal --> ubuntu ssh connection

1. 가상머신 종료
2. vm setting->네트워크 에서 호스트 전용 어댑터 추가
3. 가상머신 setting -> 네트워크 -> 추가적인 어탭터에 호스트전용 어댑터 추가 + 설정
4. 가상머신에서 ifconfig
5. sudo ifup [호스트전용 어탭터 추가시 ip주소]
6. terminal 에서 ssh [hostname]@[ip address]



- sudo apt-get update
- sudo apt-get install openssh-server openssh-client & sudo apt-get install ssh
- 위 메뉴얼의 1~4.
- enp0s8 ip가 검색되지 않으면 /etc/network/interfaces 에 다음을 추가

auto enp0s8
iface enp0s8 inet static
address 192.168.x.101
netmask 255.255.255.0
network 192.168.x.0

- sudo /etc/init.d/networking restart && sudo ssh restart
- ifconfig 하면 ip가 192.168.x.101 으로 나올것.
- terminal 에서 ssh [hostname]@[host ip address] & enter password
- 만약 host key varified failed 가 뜨면 ssh-keygen -R [host ip address]
