[처음으로](../README.md)
### NVM 설치 

공식 [github](https://github.com/nvm-sh/nvm) 페이지의 안내를 따라 설치하는 과정을 간단히 소개한다.
쉘에서 다음 명령어를 입력하면 설치가 진행된다.
```sh
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.2/install.sh | bash
or
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.2/install.sh | bash
```
결과
```sh
kali@kali:~$ curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.2/install.sh | bash
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--   0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:-- 100 13527  100 13527    0     0  17144      0 --:--:-- --:--:-- --:--:-- 17122
=> Downloading nvm from git to '/home/kali/.nvm'
=> Cloning into '/home/kali/.nvm'...
remote: Enumerating objects: 288, done.
remote: Counting objects: 100% (288/288), done.
remote: Compressing objects: 100% (258/258), done.
remote: Total 288 (delta 35), reused 95 (delta 18), pack-reused 0
Receiving objects: 100% (288/288), 146.70 KiB | 386.00 KiB/s, done.
Resolving deltas: 100% (35/35), done.
=> Compressing and cleaning up git repository

=> Appending nvm source string to /home/kali/.bashrc
=> Appending bash_completion source string to /home/kali/.bashrc
=> Close and reopen your terminal to start using nvm or run the following to use it now:

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```
> 위 명령이 할 일을 끝내면 $HOME 디렉토리에 .nvm이라는 폴더가 생성되어 있을 것이다.<br>
이렇게 생성된 .nvm 폴더를 운영체제 계정의 프로필에 등록하면 된다. 
```sh
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh" # This loads nvm
```
> 다시 $HOME 디렉터리에서 .bashrc 파일 가장 마지막 줄에 다음 코드가 추가된다.<br>
이제 터미널을 새로 열어서 nvm을 입력해보자. 별 다른 이상 없이 NVM 도움말이 나오면 설치가 완료된 것이다.

```sh
kali@kali:~$ nvm

Node Version Manager (v0.35.2)

Note: <version> refers to any version-like string nvm understands. This includes:
  - full or partial version numbers, starting with an optional "v" (0.10, v0.1.2, v1)
  - default (built-in) aliases: node, stable, unstable, iojs, system
  - custom aliases you define with `nvm alias foo`

 Any options that produce colorized output should respect the `--no-colors` option.

Usage:
  nvm --help                                Show this message
  ......
  ......
 Example:
  nvm install 8.0.0                     Install a specific version number
  nvm use 8.0                           Use the latest available 8.0.x release
  nvm run 6.10.3 app.js                 Run app.js using node 6.10.3
  nvm exec 4.8.3 node app.js            Run `node app.js` with the PATH pointing to node 4.8.3
  nvm alias default 8.1.0               Set default node version on a shell
  nvm alias default node                Always default to the latest available node version on a shell

Note:
  to remove, delete, or uninstall nvm - just remove the `$NVM_DIR` folder (usually `~/.nvm`) 
```

#### 목록 보기: ls
> 우선 리눅스에서 ls를 무의식적으로 사용하듯이 ls 명령을 입력해보겠다.
```sh
kali@kali:~$ nvm ls
            N/A
iojs -> N/A (default)
unstable -> N/A (default)
```
> 기본적으로 Kali linux(2020.1)에는 node js가 설치 되어있지 않다.


#### 설치

[처음으로](../README.md)