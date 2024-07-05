# Bandit2

## Level Goal
The password for the next level is stored in a file called spaces in this filename located in the home directory

## Commands you may need to solve this level
ls , cd , cat , file , du , find

## Helpful Reading Material
Google Search for “spaces in filename”
## 1. ssh 로 접속하기
`ssh -p 2220 bandit2@bandit.labs.overthewire.org`

`263JGJPfgU6LtdEvgfWU1XP5yac29mFx`

## 2. ls -al
`spaces in this fileanme` 이라는 파일이 보인다.

공백이 있으므로 그냥 읽으면 cat spaces, cat in, cat this, cat filename와 같은 실행을 하게 되고 파일명을 찾을 수 없다 뜰 것이다.

## 3. 공백있는 파일명가진 파일 읽기
sol1)   그냥 `cat *` 로 전체 파일을 읽어들인다.
![alt text](img/image2.png)

sol2)   띄어쓰기 앞에 `\`역슬래시를 입력해 해당 띄어쓰기가 하나의 문자로 처리되도록 해준다.`cat spaces\ in\ this\ filename`
![alt text](img/image3.png)

>MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx