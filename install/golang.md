[처음으로](../README.md)
<p align="center"><img src="https://golang.org/lib/godoc/images/go-logo-blue.svg"></p>

> 설치
```sh
  sudo apt-get install golang-go
```
> 환경 설정 보기
```sh
kali@kali:~$ go env
```
> 결과
```sh
GO111MODULE=""
GOARCH="amd64"
GOBIN=""
GOCACHE="/home/kali/.cache/go-build"
GOENV="/home/kali/.config/go/env"
GOEXE=""
GOFLAGS=""
GOHOSTARCH="amd64"
GOHOSTOS="linux"
GONOPROXY=""
GONOSUMDB=""
GOOS="linux"
GOPATH="/home/kali/go"
GOPRIVATE=""
GOPROXY="https://proxy.golang.org,direct"
GOROOT="/usr/lib/go-1.13"
GOSUMDB="sum.golang.org"
GOTMPDIR=""
GOTOOLDIR="/usr/lib/go-1.13/pkg/tool/linux_amd64"
GCCGO="gccgo"
AR="ar"
CC="gcc"
CXX="g++"
CGO_ENABLED="1"
GOMOD=""
CGO_CFLAGS="-g -O2"
CGO_CPPFLAGS=""
CGO_CXXFLAGS="-g -O2"
CGO_FFLAGS="-g -O2"
CGO_LDFLAGS="-g -O2"
PKG_CONFIG="pkg-config"
GOGCCFLAGS="-fPIC -m64 -pthread -fmessage-length=0 -fdebug-prefix-map=/tmp/go-build862568650=/tmp/go-build -gno-record-gcc-switches"
```
> GOPATH의 디렉토리는 기본적으로 생성 되지 않는다. 따라서 임의로 디렉토리를 생성해 주어야 한다.
```sh
  cd ~
  madir -p go/workspaces/hello/src
  cd go/workspaces/hello/src
  code .
```
> vscode를 실행하여 src 디렉토리에 hello.go 파일을 생성하면 프러그인을 설치하겠다고 한다. 그럼 모두 설치하면 된다.
```sh
go.toolsGopath setting is not set. Using GOPATH /home/kali/go
Installing 17 tools at /home/kali/go/bin in module mode.
  gocode
  gopkgs
  go-outline
  go-symbols
  guru
  gorename
  gotests
  gomodifytags
  impl
  fillstruct
  goplay
  godoctor
  dlv
  gocode-gomod
  godef
  goreturns
  golint

Installing github.com/mdempsky/gocode SUCCEEDED
Installing github.com/uudashr/gopkgs/cmd/gopkgs FAILED
Installing github.com/ramya-rao-a/go-outline SUCCEEDED

... 중간 생략

0-20191024034442-58e9141cd7d6
go get: github.com/uudashr/gopkgs/cmd/gopkgs@v0.0.0-20191024034442-58e9141cd7d6 requires
	github.com/uudashr/gopkgs/v2@v2.1.0 requires
	github.com/uudashr/gopkgs@v0.0.0: reading github.com/uudashr/gopkgs/go.mod at revision v0.0.0: unknown revision v0.0.0
```
> hello.go
```go
package main

import "fmt"

func main() {
	fmt.Println("Hello, 世界, 안녕하세요")
}
```
> 디버깅없이 실행(ctrl + F5)을 클릭하여 디버그 콘설에 아래와 같이 출력 되면 정상 설치된 것이다.
```sh
API server listening at: 127.0.0.1:31170
Hello, 世界, 안녕하세요
```

[처음으로](../README.md)