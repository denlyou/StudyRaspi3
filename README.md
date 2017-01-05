:octocat: [denlyou/StudyRaspi3](https://github.com/denlyou/StudyRaspi3)
# Rasberry pi 3 구매 후 공부

### OS 설치
- RASPBIAN 설치 (https://www.raspberrypi.org/downloads/)
  - 윈도우 (https://sourceforge.net/projects/win32diskimager/)
  - MAC 에선 (https://github.com/RayViljoen/Raspberry-PI-SD-Installer-OS-X)
- 초기 유저는 `pi`에 패스워드 `raspberry`

### 기본 설정
- `raspi-config` 이용
  - 패스워드 변경
  - ssh 사용 설정

### swap 설정
> swap 파티션 : http://sonhc.tistory.com/434

- swap 파일 : http://www.spacek.xyz/mle/?p=375

```shell
$ sudo su
$ dd if=/dev/zero of=/mnt/1Gb.swap bs=1M count=1024
$ mkswap /mnt/1Gb.swap
$ chmod 600 /mnt/1Gb.swap
$ swapon /mnt/1Gb.swap
$ free

# /etc/fstab 파일 (재부팅시 자동 인식)
proc            /proc           proc    defaults          0       0
/dev/mmcblk0p2  /               ext4    defaults,noatime  0       1
/dev/mmcblk0p1  /boot/firmware  vfat    defaults          0       2
/mnt/1Gb.swap   none            swap    sw                0       0
```

### 무선 설정
> http://blog.xcoda.net/84

- 무선 설정 관련

```shell
$ iwlist wlan0 scan
$ sudo vi /ect/network/interfaces
```
```shell
allow-hotplug wlan0
iface wlan0 inet dhcp
        wpa-ssid "ssid"
        wpa-psk "password"
```
```shell
$ ifdown wlan0
$ ifup wlan0
```

### 원격 설정
- ssh는 `raspi-config`
- 원격데스크탑을 `apt-get instll xrdp`로 설치후 접속

### nodejs
- 라즈베리파이2이상은 ARMv7 그 이하는 ARMv6버전으로 설치

> 컴파일 버전은 하루종일 해도 끝날 기미가 안보임..
> http://blog.xcoda.net/86

- GPIO 제어
  - onoff 모듈 => https://github.com/fivdi/onoff


### postfix 메일서버와 gmail연동
- 메일발송 서버 만들기 : http://blog.saltfactory.net/ubuntu/relay-mail-to-gmail-via-postfix-on-ubuntu.html

### gitlab-ce설치
- RASPBIAN 전용 설치 방법이 친절하게도 따로 있음 => https://about.gitlab.com/downloads/#raspberrypi2
