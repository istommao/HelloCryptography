# 对称密码学

常见的对称加密算法有

- AES
- ChaCha20
- 3DES
- DES
- Salsa20
- Blowfish
- IDEA
- RC5
- RC6
- Camellia


## 对称密码学

> 对称密码学又分为两种 分组加密或称为块密码（Block cipher）和流密码（Stream cipher）


### 分组加密 Block cipher

> 分组加密将明文分成多个等长的模块（block)，使用确定的算法和对称密钥对每组分别加密解密


### 流密码（Stream cipher）


> 明文数据每次与密钥数据流顺次对应加密，得到密文数据流。实践中数据通常是一个位（bit）并用异或（xor）操作加密。

