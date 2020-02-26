[처음으로](../README.md)
#### .bashrc 아래  스크립트 추가
  ```sh
  # enable color support of ls and also add handy aliases
  if [ -x /usr/bin/dircolors ]; then
      test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
      alias ls='ls --color=auto'
      alias ll='ls --color=always -rthla' # 추가 
  fi
  
  # server 최신 상태 만들기
  function apt-updater {
      sudo apt update &&
      sudo apt dist-upgrade -Vy &&
      sudo apt autoremove -y &&
      sudo apt autoclean &&
      sudo apt clean
  }
  ```
  > ls 명령은 이제 -l, -a, -t, -h 및 -r 인자를 자동으로 사용한다. 이 모든 인자들은 ls가 목록화(-l) 형식을 사용하고, 숨김 파일을 포함한 모든 파일(-a)을 나열하고, 파일 크기를 사람이 읽을 수 있는 형식(e.g., 1K, 234M, 5G)으로 보여준다. <br>
  또한 수정 시간(-t)을 기준으로 출력을 정렬하고, 목록의 순서를 역순으로 수정(-r)하여 최근에 수정한 파일을 터미널 맨 아래쪽에 표시한다. 이러한 인자의 모음은 자신의 스타일에 맞게 수정할 수 있다.

[처음으로](../README.md)