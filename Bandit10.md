# Bandit10

## Level Goal
The password for the next level is stored in the file data.txt, which contains base64 encoded data

## Commands you may need to solve this level
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

## Helpful Reading Material
Base64 on Wikipedia

## 1. ssh 로 접속하기
`ssh -p 2220 bandit10@bandit.labs.overthewire.org`

`FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey`

## 2. base64 Decoding
### base64 
`base64 [파일명]` : 인코딩
`base64 -d [파일명]` : 디코딩

![alt text](img/image14.png)

> dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
