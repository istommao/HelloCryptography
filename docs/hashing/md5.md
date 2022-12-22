---
comments: true
---

# MD5



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

    ```

