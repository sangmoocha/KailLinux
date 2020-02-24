[처음으로](../README.md)
### 공용 node.js 설치하기
```sh
kali@kali:~$ curl -sL https://deb.nodesource.com/setup_12.x | sudo bash -
```

> 결과: 
```sh
## Installing the NodeSource Node.js 12.x repo...


## Populating apt-get cache...

+ apt-get update
Hit:1 http://mirrors.neusoft.edu.cn/kali kali-rolling InRelease
Reading package lists... Done                             

## You seem to be using Kali version kali-rolling.
## This maps to Debian "jessie"... Adjusting for you...

## You seem to be using Devuan version jessie.
## This maps to Debian "jessie"... Adjusting for you...

## Confirming "jessie" is supported...

+ curl -sLf -o /dev/null 'https://deb.nodesource.com/node_12.x/dists/jessie/Release'

## Adding the NodeSource signing key to your keyring...

+ curl -s https://deb.nodesource.com/gpgkey/nodesource.gpg.key | apt-key add -
OK

## Creating apt sources list file for the NodeSource Node.js 12.x repo...

+ echo 'deb https://deb.nodesource.com/node_12.x jessie main' > /etc/apt/sources.list.d/nodesource.list
+ echo 'deb-src https://deb.nodesource.com/node_12.x jessie main' >> /etc/apt/sources.list.d/nodesource.list

## Running `apt-get update` for you...

+ apt-get update
Get:1 https://deb.nodesource.com/node_12.x jessie InRelease [4,584 B]
Get:3 https://deb.nodesource.com/node_12.x jessie/main amd64 Packages [765 B]       
Hit:2 http://mirrors.neusoft.edu.cn/kali kali-rolling InRelease    
Fetched 5,349 B in 3s (1,976 B/s)
Reading package lists... Done

## Run `sudo apt-get install -y nodejs` to install Node.js 12.x and npm
## You may also need development tools to build native addons:
     sudo apt-get install gcc g++ make
## To install the Yarn package manager, run:
     curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
     echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
     sudo apt-get update && sudo apt-get install yarn

```

[처음으로](../README.md)