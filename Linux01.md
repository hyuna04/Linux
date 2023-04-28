# 1.Cloud
1. Iaas 는 H/W 역할을 하는 클라우스 서비스
linux는 suse, ubuntu, centos 등등 여러가지 운영체제를 포함하고있다
ubuntu 사용할 것
LTS -> 안정화 된 버전

2. TCP - 규약에 맞게 통신 -> (신뢰성이 높다, 지속적인 서비스)
UDP - 클라이언트에서 일방적으로 보내면 서버에서 알아서 받아야됨 -> (속도가 빠르다, 지속적이지 않다)
Port -> 작업에 따라 포트에 규약이 있다. ex -> 80번: 웹, 22 -> ssh
Natmask - ip주소 필터링 ex -> 127.0.(Natmask) = '127.0.~' 으로 시작하는 ip 허용

# 2.ubuntu
1. ssh 프로그램을 이용해서 서버에 접속
root와 초기 비밀번호를 입력하여 로그인
리눅스 계열의 os에서는 ssh명령어로 로그인 가능
root(사용자명)@test1(호스트):~(위치)#or$(권한)
위치
- ~: 홈 디렉토리
- /: root 디렉토리(최상위 디렉토리)
- .: 현재 위치 디렉토리
- ..: 부모 디렉토리
- #: 관리자
- $: 일반 사용자

2. 명령어
pwd: 현재 위치를 확인
cd: 디렉토리 이동 명령 -> ex: cd .. : 부모 디렉토리로 이동
ls: 현재 디렉토리의 파일 확인

3. id: 사용자 id 확인
uid: 유저 아이디
gid: 그룹 아이디
groups: 해당 유저가 소속된 모든 그룹을 표시

who: 접속되어있는 리눅스 사용자 검색

w: 사용자들에 대한 정보

파란색: 디렉토리
하늘색: 심볼릭링크

tab키를 이용한 자동완성

## 3.사용자 생성
adduser 이름
Adding new group `ubuntu' (1001) ...
// 사용자에 대한 그룹을 만듦
Adding new user `ubuntu' (1001) with group `ubuntu' ...
// 해당 그룹에 사용자 부여
Creating home directory `/home/ubuntu' ...
// 사용자의 홈디렉토리
Copying files from `/etc/skel' ...
// 사용자가 사용할 파일

리눅스에서의 모든 리소스는 파일로 취급할 수 있다.
ex: 사용자, 그룹, 디바이스 ...

프로세스(job[작업]): 실행중인 프로그램
프로세스는 포그라운드, 백그라운드로 나눌 수 있다.
포그라운드: 사용자와 직접적으로 연동될 수 있는 프로세스
백그라운드: 사용자와 직접적으로 연동할 수는 없지만 뒤에서 실행중인 프로세스
사용자에 따라 프로세스를 분류할 수 있다. -> root, user

# 명령어
- ps 사용자에 대한 정보
- -ef: 현재 작동중인 프로세스 조회
htop
image.png
PID: 프로세스의 고유번호
PPID: PID의 부모

SHELL: 프로그램을 실행하여 프로세스화 시키는 프로그램
일반적인 프로세스의 PPID는 SHELL이 된다.
BASH: SHELL의 종류
pkill: 프로세스 종료
kill -9 PID
grep: 조회 명령어에 옵션으로 사용하면 검색한 단어가 포함된 행만 조회된다.
//passwd: 사용자의 아이디와 패스워드를 저장하는 파일
패스워드 uid gid 홈디렉토리 실행되는shell
cat: 파일을 확인하는 명령어
more: 파일을 페이지 별로 확인하 수 있는 명령어
less: 지나간 내용들도 다시 볼 수 있는 명령어

su - (uid): 다른 사용자로 로그인 root에서 사용하면 패스워드 입력없이 로그인 가능
'-'를 제외하면 해당 유저의 권한만 가져옴
su - cat에서 사용자 변경(ex - passwd변경)

cd : (change directory) 이동

cp: 파일을 복사하는 명령 ex) cp /etc/protocols ~
권한 inode 파일소유자 파일소유그룹 용량 생성날짜or접근날짜
파일명 앞에 .을 붙히면 ls로 보이지 않는다. 확인하기위해선 옵션 필요
-l, -a 두 옵션을 붙여서도 사용 가능

mv: 파일 이동 및 이름 변경 -> mv 변경 및 이동할 파일 이동할 위치 및 변경할 파일명

rm: 파일 삭제 -> rm 파일명
rm -r 디렉토리명

cat으로 txt파일 작성하는 법
cat > 파일명
(내용 작성)
ctrl + d

디렉토리 명령어
mkdir: 디렉토리 생성 -> mkdir 디렉토리명
rmdir: 디렉토리 삭제 - mkfir 디렉토리명 / 디렉토리 안에 내용이 있을 경우 rm -rf 디렉토리명(해당 디렉토리에 모든 파일을 한 번에 다 지워버리는 명령어 -조심히 사용할 것-)

(디렉토리는 rm -r 명령어로도 지울 수 있다.)

# passwd -> root권한으로 pw변경 

https 인증서 ssl??
scp 명령어
형상관리 github

devide and conquer
package management
vi editor
T4GTe8PgNRa

## 권한관리
# 권한(퍼미션)
리눅스에서의 권한관리는 사용자와, 권한으로 나뉜다.
사용자는 user, group, other 권한은 read, write, execute 로 분류할 수 있다.

# user, group, other
Owner: 생성자
User: 사용자(소유자)
Group: 그룹
Other: 그 외 모든 사용자

# read, write, execute
R : read: 읽기
W : write: 쓰기
X : eXecute: 실행
//디렉토리에서의 x권한 -> 해당 디렉토리에 대한 접근 권한

x --- --- ---
   u   g   o
x: 해당 파일의 형태 표시 ex) d,s,x ...
u: 사용자가 가지고 있는 권한 표시
g: 그룹이 가지고 있는 권한 표시
o: 그 외의 사용자가 가지고 있는 권한 표시

# 퍼미션 숫자 표기
- 각 권한들을 2진수의 자릿수로 표기하며, 해당 권한이 있을 경우 1, 없을 경우 0으로 표시할 수 있다.
ex) x rwx r-x --x -> 751
    x rw- --x --- -> 610

# chmod
- 퍼미션을 변경하는 명령어
1. chmod 퍼미션 파일 -> chmod 777 file (file이라는 이름의 파일의 퍼미션을 777로 변경한다.)
2. chmod 사용자'+,-'권한 파일 -> chmod u+r file (file이라는 이름의 파일에 유저의 읽기 권한을 추가한다.)
chmod ugo+rwx file (file이라는 이름의 파일에 user, group,others의 읽기,쓰기,접근 권한을 추가한다.)

나누기 실행하기 완성하기
pipe(파이프 기능 - 연결해줌)
grep : 특수한 입력값에 해당하는 단어를 보여줌

ls -al | grep aaa -> aaa에 해당하는 결과물을 보여줌

redirection > : 화면에 출력될 내용을 파일에 저장할 수 있음
ex) ps -ef > ps.list (ps -ef의 결과물을 ps.list로 이동) (ps -ef : 현재 실행되고있는 모든 프로세스)
cat > test.txt(cat의 결과물을 test파일로 저장)


네클5기 황보석
## 권한관리
# 권한(퍼미션)
리눅스에서의 권한관리는 사용자와, 권한으로 나뉜다.
사용자는 user, group, other 권한은 read, write, execute 로 분류할 수 있다.

# user, group, other
Owner: 생성자
User: 사용자(소유자)
Group: 그룹
Other: 그 외 모든 사용자

# read, write, execute
R : read: 읽기
W : write: 쓰기
X : eXecute: 실행
//디렉토리에서의 x권한 -> 해당 디렉토리에 대한 접근 권한

x --- --- ---
   u   g   o
x: 해당 파일의 형태 표시 ex) d,s,x ...
u: 사용자가 가지고 있는 권한 표시
g: 그룹이 가지고 있는 권한 표시
o: 그 외의 사용자가 가지고 있는 권한 표시

# 퍼미션 숫자 표기
- 각 권한들을 2진수의 자릿수로 표기하며, 해당 권한이 있을 경우 1, 없을 경우 0으로 표시할 수 있다.
ex) x rwx r-x --x -> 751
    x rw- --x --- -> 610

# chmod
- 퍼미션을 변경하는 명령어
1. chmod 퍼미션 파일 -> chmod 777 file (file이라는 이름의 파일의 퍼미션을 777로 변경한다.)
2. chmod 사용자'+,-'권한 파일 -> chmod u+r file (file이라는 이름의 파일에 user의 읽기 권한을 추가한다.)
                                chmod uo-w file (file이라는 이름의 파일에 user와 other에 쓰기 권한을 삭제한다.)
                                chmod a+x file (file이라는 이름의 파일에 모든(all) 사용자에 실행 권한을 추가한다.)

접근하려는 파일의 퍼미션보다 우선시 되는 권한은 해당 파일가 포함되는 디렉토리의 권한이 필요하다.
home 디렉토리에 권한이 없다면 그 안에 있는 파일에 권한이 있더라도 수정할 수 없다.

## devide and conquer
# pipe(|)
- 명령어에 파이프를 사용하여 다른 명령어를 추가로 실행할 수 있다.
- ex) ls -al | grep aaa -> 파이프를 이용히여 grep명령어 추가 (aaa가 포함된 줄만 조회)
- 최대 256자까지 추가로 명령어를 조합할 수 있다.

# redirecyion(>,>> ...)
- 명령에대 대한 결과물을 입,출력화 하여 파일로 만들 거나 꺼내올 수 있다.
- ex) ps -ef > ps.list (ps -ef의 결과물을 ps.list파일로 만들어 저장한다.)
- 파이프와 리다이렉션을 한 번에 사용 => ex) ps -ef | grep ubuntu > ps.list (모든 프로세스 중에서 'ubuntu'가 포함된 줄을 ps.list에 저장한다.)
- 입출력의 기본값은 cat으로 정의된다. 입력의 경우 ^d(ctrl+d)를 입력하여 입력을 완료할 수 있다.

# vi
- 리눅스의 대표적인 편집기 프로그램으로 다음의 세 가지 모드로 구분되며 각 모드의 변경은 esc,:,옵션(i,a,o,I,A,O)로 변경 가능하다. 
1. 명령모드(명령 실행): 기본상태의 모드.
    - i: 입력모드로 변경
    - (:): 실행모드로 변경
    - dd: 한 줄지우기
    - dw: 한 단어 지우기
    - 숫자: 명령어 뒤에 숫자를 붙히면 그 횟수+1 만큼 명령이 반복 ex) d5 -> 6줄 지우기
    - y: 커서 줄 복사
    - p: 커서 줄에 붙혀넣기
    - w: 단어단위로 커서를 옮김
    - ^,$: 커서 기준의 제일 앞, 뒤로 이동
    - ctrl+r: ctrl+y
    - u: ctrl+z

2. 입력모드(내용입력 및 수정): 텍스트 및 내용을 입력하는 모드

3. 실행모드(특수명령 실행): 저장, 나가기와 같은 특수 명령을 실행하는 모드. 정규표현식 사용이 가능하다.
    - !: 명령 뒤에 !를 붙히면 강제 실행.
    - w: 내용 저장
    - q, quit, exit: vi에디터 나가기
    - set: vi에 저장된 기능들로 set하는 명령어 ex) set num -> 줄번호 추가
4. 기타
    - (/,?): 커서 기준으로 아래, 위로 검색 (다음으로 넘어가려면 n, N(반대방향)) -> 실행모드 : 대신 사용
# job
- : 명령어 뒤에 사용하면 해당 명령을 백그라운드에서 실행시킴
    백그라운드에서 실행되는 프로세스는 출력이 되지 않지만 에러메세지의 경우는 출력될 수 있다.
- ^z 포그라운드에서 실행중인 프로세스 일시 정지
- bg: 일시정지된 프로세스를 백그라운드로 이동
- fg: 백그라운드의 프로세스를 포그라운드로 이동
- jobs: 실행중인 프로세스 조회
- kill: 프로세스 종료 ex) kill -9 PID(PID에 해당하는 프로세스 종료)
                         kill -9 %4(4번째 프로세스 종료)
                         killall -9 sleep(sleep 프로세스 모두 종료)

# 압축
- gzip
- gunzip
- tar
multi user
multi task
package management
vi editor


    http protocol

    hyper
    text
    transfer
    protocol

    web server

    http://
    https://

    /(최상위root)
    /bin/(binary : 시스템에 일반적으로 사용할 수 있음)
    /boot/
    /dev/
    /etc/( : 설정)
    /home/
    /lib/
    /media/
    /mnt/(mount : 붙임)
    /opt/(optional : 오라클db등.. 큰 파일들을 관리하기위해 opt 디렉토리 사용)
    /root/
    /sbin/
    /srv/
    /tmp/
    /usr/( : 참조) 
        -/bin/
        -/include/
        -/lib/
        -/sbin/
    /var/( : 가변적인, 임시로 만드는 프로그램에 사용)
        -/cache/
        -/log/
        -/spool/
        -/tmp/

## 패키지

# 패키지 설치 및 권한
wget: wget url 을 입력하면 해당 url에 있는 파일을 리눅스 서버로 다운로드 할 수 있다. 
sudo: root권한을 바로 가져올 수 있는 명령어
sudoers: sudo 명령에 대한 정보와 설정을 할 수 있는 파일. 사용자 ALL=(ALL:ALL) ALL 을 사용하면 sudo명령어를 사용할 수 있는 사용자를 설정할 수 있다.

# 웹 서버
- 웹서버는 서버와 클라이언트로 나눌 수 있다.
    - 클라이언트가 서버에게 request를 요청하면 서버에서는 작업 후 respons를 보낸다.
    - 각각 요청하는 데이터는 url+uri에 담겨서 전송된다.
    - http -> https 암호화 하여 키값을 보낸다
    - 80   -> 443 (포트 번호)
- IPv4: xxx.xxx.xxx.xxx 로 표기되는 방식의 ip주소
- IPv6: xx::xx으로 표기되는 방식의 ip주소(16진수) IPv4의 갯수 제한 때문에 이용된다.
- 웹의 기본 포트는 80번으로 규약되어있기 때문에 다른 포트를 ACG설정을 통해 열어놓는다.(80번 포트는 다른 포트로 이동만 시켜준다.)
- 가상호스트: 하나의 서버를 다수의 서버처럼 사용할 수 있도록 사용하는 사용되는 url에 따라 다른 웹페이지와 데이터를 표시할 수 있다.

# 도메인
- 도메인 종류(.com, kr, co.kr ...)
- DNS: 도메인과 ip주소를 연동시켜주는 서버
- MX: 도메인 메일 주소

# 압축
- 종류 : tarball(tar + zip) / gzip,gzip2 / bzip,bzip2 등 존재
- tar로 여러 파일들을 하나로 묶주고, zip으로 압축한 형태의 파일, 프로그램, 패키지 

# nginx
- systemctl: 시스템 동작을 컨트롤 하는 명령어
- apt: 패키지를 설치하는 명령어. ex) apt install nginx-full

# link & inode
- inode: 링크와 파일을 묶어주는 역할. 하나의 파일에 여러 개의 링크가 있다면 해당 링크를 하나의 inode로 묶고 해당 inode는 파일을 가르킨다.
- 하드링크: 복사와 유사하지만 같은 파일이 두개가 되어, 한 쪽이 수정된다면 다른 한 쪽도 수정되는 방식으로, 원본 파일이나 하드링크 파일이 삭제되어도 하나 이상 남아있다면 (inode가 남아있다면) 나머지 파일은 삭제되지 않는다.
- 심볼릭링크: 바로가기와 같은 개념으로, 원본파일에 연결할 수 있는 링크를 생성하는 방식으로, inode가 가르키는 파일은 원본파일의 주소를 가르킨다. 때문에 링크파일이 삭제 되어도 원본 파일은 그대로 남아있지만 원본 파일이 삭제된다면 파일의 심볼릭링크들은 사용할 수 없다.

- symboliclink 
(원본파일이나 디렉토리를 가리키는 참조역할)
ex)  ubuntu@test:~$ ln -s ./test ./test22 
 -> ln : 링크생성 명령어
    -s : 심볼릭 링크 생성하도록 지정
    ./test : 현재 디렉토리에 있는 파일이나 디렉토리를 가리키는 링크생성
    ./test22 : 새로 생성할 심볼릭 링크의 이름을 지정
symboliclink -> 주소
(원본의 내용을 갖고있지 않기 때문에 원본파일이 삭제되지 않는 한 원본파일이 손상될 일 없음.
원본파일이 삭제되면 링크도 더이상 유효하지 않음.
symboliclink가 삭제되더라도 원본파일은 그대로 유지됨.)

- hardlink
ex) ubuntu@test:~$ ln /var/log/syslog /home/user/syslog
 -> /var/log/syslog 파일을 /home/user/syslog 이라는 이름의 하드링크로 연결
 /var/log/syslog : 원본파일의 경로
 /home/user/syslog : 생성될 하드링크의 경로
 hardlink -> (파일)내용
 (hardlink는 원본과 같은 inode를 가지기 때문에 원본파일과 하드링크를 구분할 수 없음.
 원본파일이 삭제되더라도 하드링크가 존재하는 한 계속해서 접근가능.)

- inode : 파일수
ex) 
ubuntu@test:~$ ll -> 전체파일보기
ubuntu@test:~$ mkdir new -> new파일 생성
ubuntu@test:~$ cd new -> new파일로 가기
ubuntu@test:~/new$ ll -> new의 inode는2
                        .
                        ..
                        이 포함되어있기 때문
ubuntu@test:~/new$ mkdir sub -> new파일안에
                                sub파일 생성
ubuntu@test:~/new$ ll -> sub포함 3갠

# 1. RunLevel
(시스템 관리를 용이하게 하기 위함)
- 0~6(총 7개의 런 레벨이 있음)
    0 (halt) 
        : 시스템 중지, 기본값으로 설정 불가
    1 (single user mode) 
        : 단일 사용자 모드
    2 (multiuser,without NFS) 
        : 네트워크를 사용하지 않는 다중 사용자 모드
    3 (Full multiuser mode)
        : 네트워크를 지원하는 다중 사용자 모드
    4 (Unused)
        : 사용되지 않는 런레벨이지만 사용자가 정의해서 사용 가능
    5 (Xll)
        : X Window를 사용하는 다중 사용자 모드(그래픽 인터페이스)
    6 (Reboot)
        : 시스템을 재기동할 때 사용, 기본값으로 설정불가
- ftpd
- sshd
- httpd

# 2. 리눅스 네트워크
# 3. Http Web Server
# 4. Shall Script
# 5. crontap
. rc (run command : 실행명령)
. Front End Framework
. 디자인 패턴

# 실습해보기
## 리눅스 서버구축하기
- 기본 사용자 생성(sudo사용)
- 웹 서버 설치
- 도메인 연결

# FrontEnd
- HTML
    - React.js
    -> javascript 라이브러리
    - React 사용자 인터페이스 만들기
- JS(자바 스크립트)
- CSS(문자 스타일 디자인)
    - tailwindcss 라이브러리 참조하기

- 도메인 인증 하는 법
하나의 도메인 인증할 때 : ubuntu@linux:/etc/nginx/sites-enabled$ sudo certbot --nginx -d 도메인주소 
여러개 인증할 때 : ubuntu@linux:/etc/nginx/sites-enabled$ sudo certbot --nginx -d 도메인주소 -d 도메인주소 -d 도메인주소...

- crontab 
 ex) ubuntu@linux:~$ sudo crontab -l
-> 
MAILTO=""
30 06 * * * /usr/sbin/nsight_updater > /tmp/.nu.log 2> /tmp/.nu_err.log