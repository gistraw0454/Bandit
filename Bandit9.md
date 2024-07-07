# Bandit8

## Level Goal
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

## Commands you may need to solve this level
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

## 1. ssh 로 접속하기
`ssh -p 2220 bandit9@bandit.labs.overthewire.org`

`4CKMh1JI91bUIZZPXDqGanal4xvAg0JM`

## 2. data.txt 에서 ==여러개로 시작된 문자열이있는 줄 찾기
처음엔, `grep == data.txt` 로 찾아봤다. 결과가 나오긴했는데 읽을수없는 문자들도 많이 나와 불편했다.
![alt text](image12.png)

### strings 
- binary 파일의 ASCII 문자를 찾아 화면에 출력해준다.
- 모든 인쇄가능한 문자열을 추출하여 출력하므로, 분석할 때 많은 도움이 된다.

`strings data.txt | grep ==` 로 사람이 읽을 수 있는 형태로 문자열들을 출력하며, ==가 포함된 줄을 출력해보면

![alt text](image13.png)

> FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
