<p align="center"><img src="https://www.kali.org/wp-content/uploads/2020/01/kali-2020.1.png"></p>

# Kali Linux 2020.1 Release
> [virtualbox](https://www.virtualbox.org/)에 [IMAGES](https://www.offensive-security.com/kali-linux-vm-vmware-virtualbox-image-download/#1572305786534-030ce714-cc3b)를 내려받아서 실행하기 때문에 설치 과정은 생략하고 이후 과정부터 작성합니다.
### 최신상태 만들기
```sh
  apt update &&
  apt dist-upgrade -Vy &&
  apt autoremove -y &&
  apt autoclean &&
  apt clean 
```
* [Roadmap to becoming a web developer in 2020](https://github.com/kamranahmedse/developer-roadmap)

* 프로그램 설치 및 설정
  - [한글 글꼴 및 입력기](./install/hangul.md)
  - [chrome 설치](./install/chrome.md)
  - [Visual Studio Code](./install/vscode.md)
  - [NVM (Node Version Manager)](./install/nvm.md)
  - [범용 node.js 설치](./install/nodejs.md)
  - [범용 yarn 설치](./install/yarn.md)
  - Certbot
  - Postfix
  - [composer](./install/composer.md)
  - [DBeaver](./install/DBeaver.md)
  - PhpMyAdmin
  - [golang](./install/golang.md)
  - [php 7.4.3](./install/php.md)

* Server 설정
  - [개인 설정(.bashrc)](./settings/bashrc.md)
  - Nginx 
  - MariaDB