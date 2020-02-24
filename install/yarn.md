[처음으로](../README.md)
### 공용 yarn 설치
```sh
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
```
```sh
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
```
```sh
sudo apt update
```
```sh
sudo apt install yarn
```
[처음으로](../README.md)