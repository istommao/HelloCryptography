# HDKF


> 对于大多数应用程序，shared_key应将其传递给密钥派生函数。
这允许将附加信息混合到密钥中，派生多个密钥，并破坏可能存在的任何结构。


```python
from cryptography.hazmat.primitives import hashes
from cryptography.hazmat.primitives.asymmetric.x25519 import X25519PrivateKey
from cryptography.hazmat.primitives.kdf.hkdf import HKDF

alice_private_key = X25519PrivateKey.generate()

bob_public_key = X25519PrivateKey.generate().public_key()


shared_key = alice_private_key.exchange(bob_public_key)

derived_key = HKDF(
    algorithm=hashes.SHA256(),
    length=32,
    salt=None,
    info=b'handshake data',
).derive(shared_key)
```
