[처음으로](../README.md)
<p align="center"><img src="https://t1.daumcdn.net/cfile/tistory/226DC33F57E368F615"></p>

### 크롬 설치
  ```sh
    wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
  ```
  > 크롬 웹 브라우저 패키지를 설치하기 위해 필요한 인증키를 등록합니다. 
  ```sh
    sudo sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
  ```  
  > 크롬 웹 브라우저 패키지를 다운로드 받을 PPA를 sources.list.d에 추가합니다. 
  ```sh
    sudo apt update
  ```
  > 추가한 PPA로부터 설치 가능할 크롬 웹브라우저 패키지 정보를 가져오기 위해 패키지 리스트를 업데이트합니다.
  ```sh
    sudo apt install google-chrome-stable
  ```
  > 이제 크롬 웹 브라우저를 설치 합니다.

[처음으로](../README.md)  