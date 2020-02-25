[처음으로](../README.md)
<p align="center"><img src="https://getcomposer.org/img/logo-composer-transparent2.png"></p>

> 설치 프로그램을 현재 디렉토리로 다운로드
```php
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
```
> 설치 관리자 SHA-384를 [확인](https://getcomposer.org/download/) 하십시오. 설치 프로그램의 모든 버전에 따라 변경됩니다. 따라서 아래 코드는 사이트에 있는 코드를 사용 하십시요
```php
php -r "if (hash_file('sha384', 'composer-setup.php') === 'e0012edf3e80b6978849f5eff0d4b4e4c79ff1609dd1e613307e16318854d24ae64f26d17af3ef0bf7cfb710ca74755a') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
```
> 설치 프로그램을 실행
```php
php composer-setup.php
```
> 설치 프로그램 제거
```php
php -r "unlink('composer-setup.php');"
```
> 전역에서 사용가능하게 파일을 이동 시칸다. php composer.phar로 실행하는 대신 composer로 실행하면 된다
```sh
$ sudo mv composer.phar /usr/local/bin/composer
```
[처음으로](../README.md)