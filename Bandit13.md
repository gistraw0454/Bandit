# Bandit13

## Level Goal
The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on

## Commands you may need to solve this level
ssh, telnet, nc, openssl, s_client, nmap

## Helpful Reading Material
SSH/OpenSSH/Keys

## 1. ssh 로 접속하기
`ssh -p 2220 bandit13@bandit.labs.overthewire.org`

`FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn`

## 2. ls 확인
`cat sshkey.private` 
```
MIIEpAIBAAKCAQEAxkkOE83W2cOT7IWhFc9aPaaQmQDdgzuXCv+ppZHa++buSkN+
gg0tcr7Fw8NLGa5+Uzec2rEg0WmeevB13AIoYp0MZyETq46t+jk9puNwZwIt9XgB
ZufGtZEwWbFWw/vVLNwOXBe4UWStGRWzgPpEeSv5Tb1VjLZIBdGphTIK22Amz6Zb
ThMsiMnyJafEwJ/T8PQO3myS91vUHEuoOMAzoUID4kN0MEZ3+XahyK0HJVq68KsV
ObefXG1vvA3GAJ29kxJaqvRfgYnqZryWN7w3CHjNU4c/2Jkp+n8L0SnxaNA+WYA7
jiPyTF0is8uzMlYQ4l1Lzh/8/MpvhCQF8r22dwIDAQABAoIBAQC6dWBjhyEOzjeA
J3j/RWmap9M5zfJ/wb2bfidNpwbB8rsJ4sZIDZQ7XuIh4LfygoAQSS+bBw3RXvzE
pvJt3SmU8hIDuLsCjL1VnBY5pY7Bju8g8aR/3FyjyNAqx/TLfzlLYfOu7i9Jet67
xAh0tONG/u8FB5I3LAI2Vp6OviwvdWeC4nOxCthldpuPKNLA8rmMMVRTKQ+7T2VS
nXmwYckKUcUgzoVSpiNZaS0zUDypdpy2+tRH3MQa5kqN1YKjvF8RC47woOYCktsD
o3FFpGNFec9Taa3Msy+DfQQhHKZFKIL3bJDONtmrVvtYK40/yeU4aZ/HA2DQzwhe
ol1AfiEhAoGBAOnVjosBkm7sblK+n4IEwPxs8sOmhPnTDUy5WGrpSCrXOmsVIBUf
laL3ZGLx3xCIwtCnEucB9DvN2HZkupc/h6hTKUYLqXuyLD8njTrbRhLgbC9QrKrS
M1F2fSTxVqPtZDlDMwjNR04xHA/fKh8bXXyTMqOHNJTHHNhbh3McdURjAoGBANkU
1hqfnw7+aXncJ9bjysr1ZWbqOE5Nd8AFgfwaKuGTTVX2NsUQnCMWdOp+wFak40JH
PKWkJNdBG+ex0H9JNQsTK3X5PBMAS8AfX0GrKeuwKWA6erytVTqjOfLYcdp5+z9s
8DtVCxDuVsM+i4X8UqIGOlvGbtKEVokHPFXP1q/dAoGAcHg5YX7WEehCgCYTzpO+
xysX8ScM2qS6xuZ3MqUWAxUWkh7NGZvhe0sGy9iOdANzwKw7mUUFViaCMR/t54W1
GC83sOs3D7n5Mj8x3NdO8xFit7dT9a245TvaoYQ7KgmqpSg/ScKCw4c3eiLava+J
3btnJeSIU+8ZXq9XjPRpKwUCgYA7z6LiOQKxNeXH3qHXcnHok855maUj5fJNpPbY
iDkyZ8ySF8GlcFsky8Yw6fWCqfG3zDrohJ5l9JmEsBh7SadkwsZhvecQcS9t4vby
9/8X4jS0P8ibfcKS4nBP+dT81kkkg5Z5MohXBORA7VWx+ACohcDEkprsQ+w32xeD
qT1EvQKBgQDKm8ws2ByvSUVs9GjTilCajFqLJ0eVYzRPaY6f++Gv/UVfAPV4c+S0
kAWpXbv5tbkkzbS0eaLPTKgLzavXtQoTtKwrjpolHKIHUz6Wu+n4abfAIRFubOdN
/+aLoRQ0yBDRbdXMsZN/jvY44eM+xRLdRVyMmdPtP8belRi2E2aEzA==
```
### public and private keys
- private key는 로그인하는 컴퓨터에 보관
- public key는 로그인하려는 모든 컴퓨터의 .ssh/authorized_keys 파일에 저장
- 컴퓨터에 로그인할때, SSH는 public Key로 Private key로만 잠금해제할수있는 방식으로 잠근다.
- **키 기반 SSH 로그인** : RSA 또는 DSA 키를 사용할 수 있다.
    - RSA KEY 생성
        ```bash
        # client에서 public/private ssh key 만들기
        mkdir ~/.ssh
        chmod 700 ~/.ssh
        ssh-keygen -t rsa
        ```
        를 치면 아래와 같은 화면이 나온다.
        ```bash
        Generating public/private rsa key pair.
        Enter file in which to save the key (/home/b/.ssh/id_rsa):
        Enter passphrase (empty for no passphrase):
        Enter same passphrase again:
        Your identification has been saved in /home/b/.ssh/id_rsa.
        Your public key has been saved in /home/b/.ssh/id_rsa.pub.
        ```
        이제 public key를 .ssh/id_rsa.pub로 사용할 수 있다.

## 3. 그냥 이렇게하자.
```
ssh -i sshkey.private bandit14@localhost -p 2220
```
**RSA 인증을 위한 비밀키를 읽는 아이덴티티 파일을 선택 할 수 있다.**

이렇게하면 bandit14 user가되어 /etc/bandit_pass/bandit14를 읽을 수 있는 권한이 생긴다.

![alt text](img/image17.png)


>MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS

