# DH (Diffie-Hellman) 迪菲—赫尔曼密钥交换

!!!迪菲—赫尔曼密钥交换

    迪菲—赫尔曼密钥交换 (Diffie–Hellman key exchange，缩写为DH) 是一种保密通信协议


> 1976年 Diffie 和 Hellman发布 迪菲—赫尔曼密钥交换，最早思想由Hellman的博士研究生瑞夫·墨克 (Ralph Merkle) 提出。
> 而后 Hellman和研究助理Diffie共同发明了 迪菲—赫尔曼密钥交换协议。

## 数学原理

> DH基于数论，整数模 n 乘法群及其原根的模幂运算。



1. Alice 和 Bob公开同意使用模数p = 23和基数g = 5（即原根模数 23）。

2. Alice 选择一个秘密整数a = 4，然后发送给 $$ Bob A = g^{a} mod p$$
    $$ A = 5^{4}  mod 23 = 4$$（在此示例中， A和a的值相同，均为 4，但通常情况并非如此）

3. Bob 选择一个秘密整数b = 3，然后发送给 Alice B = g b mod p
 B = 5 3模23 = 10

4. 爱丽丝计算s = B a mod p
s =10 4模23=18

5. Bob 计算s = A b mod p
s =4 3模23=18

6. 爱丽丝和鲍勃现在共享一个秘密（数字 18）




## 3XDH

1997 年，Simon Blake-Wilson、Don Johnson、Alfred Menezes提出了一种三重DH的实现。
