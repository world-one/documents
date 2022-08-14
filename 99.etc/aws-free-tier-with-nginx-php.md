## AWS Free tier with nginx, php
aws 프리티어 설정은 여러번 했지만 기억에 남을 만큼 자주 쓰진 않았다.
그래서 매번 할때마다 구글링을 통해 더듬더듬 해왔었다.
이번 기회에 다시금 정리해두려 한다.

### AWS
Amazon Web Services(AWS), 아마존의 자회사로 클라우드 서비스를 주력으로 한다.
전에 얼핏 보긴 했지만 네이버에도 비슷한 서비스가 있는 걸 봤다.

#### Amazon Machine Image(AMI)
소프트웨어를 선택하는 단계다.
쭉 우분투를 사용했기에 최신버전으로 선택했다.

```
Ubuntu Server 18.04 LTS (HVM), SSD Volume Type
```

#### 인스턴스 유형
가상 서버의 성능을 선택하는 단계로, 프리티어로 선택가능한 유형은 하나뿐이다.

```
t2.micro 메모리 1GB, vCPUs 1
```

#### 시작하기
시작하게 되면 키페어를 생성하게 된다.
OOO.pem 파일을 다운로드 받고 시작하게 되면 인스턴스(서버)가 준비되며 구동한다.

#### 접속하기
pem파일을 통해 서버에 접속할 수 있다. 우선 pem파일의 권한을 바꿔줘야 한다. 
chmod 600 000.pem ssh -i 000.pem ubuntu@123.123.123.21 이런식으로 접속 가능하다. 또는 sh파일을 만들어두면 쉽게 접속 가능하다.

#### 웹 서버 세팅
웹서버 세팅을 위해 그 동안 써왔던 apache를 설치를 하려했으나
이번 기회에 nginx를 써보려한다. 좀 더 가볍고 동시접속처리를 잘한다나..
둘의 차이점은 나중에 한번 정리해봐야겠다.

#### 패키지 갱신
```
apt-get update
apt-get upgrade
apt autoremove
```
운영체제 설치 후 가장 먼저 패키지 갱신을 한다.
autoremove로 설치중에 생긴 불필요한 파일을 제거한다.

#### 시간 설정
```
dpkg-reconfigure tzdata
or
ln -sf /usr/share/zoneinfo/Asia/Seoul /etc/localtime
```
원하는 지역을 선택하여 시간을 설정한다.

#### nginx 설치
그냥 설치하면 최신버전으로 설치가 되질 않는다.

```
vi /etc/apt/sources.list.d/nginx.list
```
아래 내용을 추가한 뒤 파일을 생성한다.

```
# Nginx
deb [arch=amd64,arm64] http://nginx.org/packages/mainline/ubuntu/ bionic nginx
deb-src http://nginx.org/packages/mainline/ubuntu/ bionic nginx
```
nginx 저장소 인증키 추가
```
curl -sS http://nginx.org/keys/nginx_signing.key | apt-key add -
```
저장소 내용일 추가되었는지 확인한다. apt-key list
```
apt-get update

apt install nginx
service restart nginx
nginx -v
```
해당 아이피로 접속하여 제대로 동작하는지 확인한다.

#### php-fpm 설치
nginx는 php-fpm를 통해 Php를 해석할 수 있다고 한다.
```
apt install php7.3-fpm

php -v
php-fpm7.3 -v
```

#### php 모듈 설치
```
apt install php7.3-mbstring
apt install php7.3-gd
apt install php7.3-curl php7.3-xml
apt install php7.3-bcmath
apt install php7.3-mysql
apt install composer
```

#### php 시간 설정
```
vi /etc/php/7.3/fpm/php.ini
vi /etc/php/7.3/cli/php.ini
```
찾아서 주석 해제 후 내용 추가 data.timezone = Asia/Seoul

```
service php7.3-fpm restart
```

#### nginx 권한 설정
php-fpm과 사용자 권한 일치시키기

```
user  nginx; -> user  www-data;
worker_processes 1; -> worker_processes auto;
service nginx restart
```

#### nginx, php-fpm 파라미터 연동
```
vi /etc/nginx/fastcgi_params
fastcgiparam SCRIPTFILENAME document_rootdocumentr​ootfastcgiscriptname; fastcgiparam PATHTRANSLATED document_rootdocumentr​ootfastcgipathinfo; fastcgiparam PATHINFO $fastcgipathinfo;
```

#### 도메인 설정 위치
```
/etc/nginx/conf.d
```

#### ipv6 설정
켜두면 문제가 생길 수 있다고 하니 끄도록 하자

```
vi /etc/sysctl.conf
```
상단에 내용을 추가한다. 
```
net.ipv6.conf.all.disableipv6 = 1 net.ipv6.conf.default.disableipv6 = 1 net.ipv6.conf.lo.disable_ipv6 = 1
```

```
sysctl -p
cat /proc/sys/net/ipv6/conf/all/disable_ipv6
```

해당 내용은 아래 포스팅을 보며 따라한 것을 필요한 것만 정리해둔 것입니다.
https://blog.lael.be/post/8319

