# 문제 세부 사항
* Windows 빌드 번호 : Microsoft Windows [Version 10.0.18917.1000]
* 내가하고있는 일과 일어나고있는 일 : Windows 10 호스트 컴퓨터에서 실행 중 `ipconfig`
```sh
  IPv4 Address. . . . . . . . . . . : 192.168.1.41
  Subnet Mask . . . . . . . . . . . : 255.255.255.0
  Default Gateway . . . . . . . . . : 192.168.1.1
```
* `ifconfig`우분투 WSL 2에서 실행
```sh
  eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
  inet 172.18.72.60  netmask 255.255.0.0  broadcast 172.18.255.255
```
> Window 호스트에서 172.18.72.60에 액세스해도 작동하지만 네트워크의 다른 시스템에서는이 IP에 액세스 할 수 없습니다.

* 무엇이 잘못 되었습니까? 대신 Ubuntu WSL 2에서 호스트 컴퓨터와 동일한 네트워크에 IP 주소가
있을 것으로 기대 ifconfig합니다.

* ### 문서 검색 :
  WSL 2 네트워킹에 대해 찾은 유일한 세부 사항은 다음과 같습니다. 다음은 해당 IP에 자체 IP가 있고 localhost는 향후 WSL 2에 사용될 것입니다.
  https://docs.microsoft.com/ko-kr/windows/wsl/wsl2-ux-changes
이것은 괜찮습니다. 그러나 IP WSL 2가 로컬 LAN에 설치되기를 원합니다. 브리지 할 가상 NIC.


# 해결 방법
> ## WSL 2 TPC 네트워크 포워딩
## 소개

WSL 2 베타가 도입되면서 Microsoft는 시스템 아키텍처를 변경했습니다.
변경 사항에는 기본 브리지 네트워크 어댑터에서 Hyper-V 가상 네트워크 어댑터로의 변경이 포함됩니다. <br>
베타 프로그램을 시작하는 동안 구현이 완료되지 않았습니다. 이로 인해 WSL 2에서 네트워크 리소스 액세스가 복잡해집니다. <br>
임시 해결책은 WSL 2 서비스의 TCP 포트를 호스트 OS에 전달하는 것입니다.
WSL 2 시스템의 가상 어댑터는 재부팅 중에 IP 주소를 변경하므로 한 번 실행 솔루션을 구현하기가 어렵습니다. <br>
참고로, Windows 방화벽은 리디렉션 된 포트를 차단합니다.

> 해결 방법은 다음을 수행하는 스크립트를 사용하는 것입니다.

* WSL 2 머신의 IP 주소 가져 오기
* 이전 포트 전달 규칙 제거
* 포트 전달 규칙 추가
* 이전에 추가 한 방화벽 규칙 제거
* 새로운 방화벽 규칙 추가

## 구성

스크립트는 가장 높은 권한으로 로그인시 실행되어야하며 Powershell은 외부 소스를 실행할 수 있어야합니다.

### PowerShell 구성

Power Shell이 ​​외부 스크립트를 실행하도록 설정하고 관리자 권한으로 power shell에서 아래 명령을 실행하십시오.

### 방법 :

검색으로 이동하여 작업 스케줄러를 검색하십시오. 오른쪽의 작업 메뉴에서 작업 만들기를 클릭하십시오. <br>
이름을 입력하고 트리거 탭으로 이동하십시오. 로그인 할 때 작업 시작으로 새 트리거를 작성하고 지연 시간을 10 초로 설정하십시오. <br>
조치로 이동하여 스크립트를 추가하십시오. 랩톱을 사용하는 경우 설정으로 이동하여 전원을 켜십시오.

마지막으로 <br>
저는 보안 전문가 나 스크립팅 전문가가 아니며 기술적으로 Windows OS에 익숙하지 않습니다.

### 업데이트
업데이트는 원하지 않는 방화벽 규칙을 제거하는 기능을 추가합니다.
여기 스크립트가 있습니다.

```ps
$remoteport = bash.exe -c "ifconfig eth0 | grep 'inet '"
$found = $remoteport -match '\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}';

if( $found ){
  $remoteport = $matches[0];
} else{
  #echo "The Script Exited, the ip address of WSL 2 cannot be found";
  echo "스크립트 종료, WSL 2의 IP 주소를 찾을 수 없습니다";
  exit;
}

#[Ports]

#All the ports you want to forward separated by coma
#전달하려는 모든 포트는 쉼표로 구분
$ports=@(80,443,10000,3000,5000);


#[Static ip]
#You can change the addr to your ip config to listen to a specific address
#특정 주소를 수신하도록 addr을 ip 설정으로 변경할 수 있습니다
$addr='0.0.0.0';
$ports_a = $ports -join ",";


#Remove Firewall Exception Rules
#방화벽 예외 규칙 제거
iex "Remove-NetFireWallRule -DisplayName 'WSL 2 Firewall Unlock' ";

#adding Exception Rules for inbound and outbound Rules
#인바운드 및 아웃 바운드 규칙에 대한 예외 규칙 추가
iex "New-NetFireWallRule -DisplayName 'WSL 2 Firewall Unlock' -Direction Outbound -LocalPort $ports_a -Action Allow -Protocol TCP";
iex "New-NetFireWallRule -DisplayName 'WSL 2 Firewall Unlock' -Direction Inbound -LocalPort $ports_a -Action Allow -Protocol TCP";

for( $i = 0; $i -lt $ports.length; $i++ ){
  $port = $ports[$i];
  iex "netsh interface portproxy delete v4tov4 listenport=$port listenaddress=$addr";
  iex "netsh interface portproxy add v4tov4 listenport=$port listenaddress=$addr connectport=$port connectaddress=$remoteport";
}
```
