:octocat: [denlyou/StudyRaspi3](https://github.com/denlyou/StudyRaspi3)
# Rasberry pi 3 구매 후 공부

### OS 설치
- RASPBIAN 설치 (https://www.raspberrypi.org/downloads/)
  - 윈도우 (https://sourceforge.net/projects/win32diskimager/)
  - MAC 에선 (https://github.com/RayViljoen/Raspberry-PI-SD-Installer-OS-X)
- 초기 유저는 `pi`에 패스워드 `raspberry`

### 기본 설정
- `raspi-config` 이용

### 무선 설정
> http://blog.xcoda.net/84

- 무선 설정 관련

```shell
iwlist wlan0 scan
sudo vi /ect/network/interfaces
```
```shell
allow-hotplug wlan0
iface wlan0 inet dhcp
        wpa-ssid "ssid"
        wpa-psk "password"
```
```shell
ifdown wlan0
ifup wlan0
```

### 원격 설정
- ssh는 `raspi-config`
- 원격데스크탑을 `apt-get instll xrdp`로 설치후 접속

### nodejs
- 라즈베리파이2이상은 ARMv7 그 이하는 ARMv6버전으로 설치
> 컴파일 버전은 하루종일 해도 끝날 기미가 안보임..
> http://blog.xcoda.net/86
