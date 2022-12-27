---
comments: true
---

# MD5

!!! Message-Digest-Algorithm

    MD5消息摘要算法（英语：MD5 Message-Digest Algorithm），一种被广泛使用的密码散列函数，可以产生出一个128位（16个字符(BYTES)）的散列值（hash value），用于确保信息传输完整一致。

    **——— wikipedia**

!!! 历史
    MD5由美国密码学家罗纳德·李维斯特（Ronald Linn Rivest）设计，于`1992`年公开，用以取代MD4算法。这套算法的程序在 RFC 1321 中被加以规范。



=== "JavaScript"

    ```bash
    npm install js-md5
    ```

    ```js
    // md5('Message to hash');

    var hash = md5.create();
    hash.update('Message to hash');
    hash.hex();
    ```


=== "Python"

    ```python
    import hashlib

    result = hashlib.md5("Hello Cryptography".encode())
    print(result.hexdigest())
    ```


=== "Golang"


    ```go
    package main

    import (
        "crypto/md5"
        "fmt"
        "io"
    )

    func main() {
        h := md5.New()
        io.WriteString(h, "Hello Cryptography")
        fmt.Printf("%x", h.Sum(nil))
    }
    ```

