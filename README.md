# MyTips

# ubuntu simple setting

- jdk : $ apt-get install openjdk-8-jdk & java -version
- maven : $ apt-get install maven & mvn -version
- zookeeper
    - $wget http://apache.mirror.cdnetworks.com/zookeeper/stable/zookeeper-3.4.10.tar.gz
    - $tar zxvf zookeeper-3.4.10.tar.gz
    - $cp -Rf zookeeper-3.4.10 /usr/local/zookeeper
    - $cd /usr/local/zookeeper
    - $cp conf/zoo_sample.cfg conf/zoo.cfg
    - zoo.cfg 파일 수정
        - http://novicecoder.tistory.com/entry/Zookeeper설치
    - 서버 구동
        - ./bin/zkServer.sh start
        - or
        - sudo bash zkServer.sh start

----

# sql file import

- [db name] 으로 database 미리 생성
- $ cd {where .sql file located}
- mysql -u root -p [db name] < dump.sql

----

# 22번 포트 열기
- sudo systemsetup -setremotelogin on
- 확인 : $tcping 127.0.0.1 [port]

----

# mac terminal --> ubuntu ssh connection

# 방법 1
- 가상머신 종료
- vm setting->네트워크 에서 호스트 전용 어댑터 추가
- 가상머신 setting -> 네트워크 -> 추가적인 어탭터에 호스트전용 어댑터 추가 + 설정
- 가상머신에서 ifconfig
- sudo ifup [호스트전용 어탭터 추가시 ip주소]
- terminal 에서 ssh [hostname]@[ip address]

# 방법 2

- sudo apt-get update
- sudo apt-get install openssh-server openssh-client & sudo apt-get install ssh
- 위 메뉴얼의 1~4.
- ifconfig 에서 ip가 나오지 않는 이름 : enp0s8(다를 수 있음)

- $sudo vi /etc/network/interfaces & 다음을 추가
  - auto enp0s8
  - iface enp0s8 inet static
  - address 192.168.x.101 (192.168.x.x ==> 우분투 설정에 나온 ip)
  - netmask 255.255.255.0
  - network 192.168.x.0
  
- 가상머신 reboot
- $sudo /etc/init.d/networking restart or $sudo service ssh start/restart
- ifconfig 하면 ip가 192.168.x.101 으로 나올것.
- terminal 에서 ssh [hostname]@[host ip address] & enter password
- 만약 host key varified failed 가 뜨면 ssh-keygen -R [host ip address]

# 방법 3
https://m.blog.naver.com/PostView.nhn?blogId=fewus28&logNo=221071674293&proxyReferer=https%3A%2F%2Fwww.google.co.kr%2F
이게 

----

# vimrc
sudo vi ~/.vimrc

set hlsearch " 검색어 하이라이팅
set nu " 줄번호
set autoindent " 자동 들여쓰기
set scrolloff=2
set wildmode=longest,list
set ts=4 "tag select
set sts=4 "st select
set sw=1 " 스크롤바 너비
set autowrite " 다른 파일로 넘어갈 때 자동 저장
set autoread " 작업 중인 파일 외부에서 변경됬을 경우 자동으로 불러옴
set cindent " C언어 자동 들여쓰기
set bs=eol,start,indent
set history=256
set laststatus=2 " 상태바 표시 항상
"set paste " 붙여넣기 계단현상 없애기
set shiftwidth=4 " 자동 들여쓰기 너비 설정
set showmatch " 일치하는 괄호 하이라이팅
set smartcase " 검색시 대소문자 구별
set smarttab
set smartindent
set softtabstop=4
set tabstop=4
set ruler " 현재 커서 위치 표시
set incsearch
set statusline=\ %<%l:%v\ [%P]%=%a\ %h%m%r\ %F\
" 마지막으로 수정된 곳에 커서를 위치함
au BufReadPost *
\ if line("'\"") > 0 && line("'\"") <= line("$") |
\ exe "norm g`\"" |
\ endif
" 파일 인코딩을 한국어로
if $LANG[0]=='k' && $LANG[1]=='o'
set fileencoding=korea
endif
" 구문 강조 사용
if has("syntax")
 syntax on
endif
" 컬러 스킴 사용
colorscheme jellybeans

----
