# SHA

## SHA家族

- SHA1
- SHA2
- SHA3



=== "Python"

    ```python
    import hashlib

    result = hashlib.sha256("Hello Cryptography".encode()).hexdigest()
    print(result)
    ```

=== "JavaScript"

    ```bash title="npm install"
    npm install js-sha256
    ```

    ```js
    import { sha256 } from 'js-sha256';

    var hash = sha256.create();
    hash.update("Hello Cryptography");
    hash.hex();
    ```

=== "Golang"

    ```go
    package main

    import (
        "crypto/sha256"
        "fmt"
    )

    func main() {
        h := sha256.New()
        h.Write([]byte("Hello Cryptography"))
        fmt.Printf("%x", h.Sum(nil))
    }
    ```
