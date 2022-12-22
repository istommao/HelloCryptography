---
comments: true
---


# 对称密码学 - AES


=== "JavaScript"

    ```js
    const StringToArrayBuffer = (str: string) => {
      let buf = new ArrayBuffer(str.length);
      let bufView = new Uint8Array(buf);
      for (var i = 0, strLen = str.length; i < strLen; i++) {
        bufView[i] = str.charCodeAt(i);
      }
      return buf;
    };

    const ImportSecretKey = async (rawKey: any, aesName: string) => {
      return await window.crypto.subtle.importKey('raw', rawKey, aesName, true, ['encrypt', 'decrypt']);
    };

    const AesEncrypt = async (
      aesName: string,
      keyStr: string,
      keySize: number,
      iv: string,
      encoded: Uint8Array,
    ) => {
      const alg = {
        name: aesName,
        iv: StringToArrayBuffer(atob(iv)),
        length: keySize,
      };
      let key = await ImportSecretKey(StringToArrayBuffer(atob(keyStr)), aesName);
      let result = await window.crypto.subtle.encrypt(alg, key, encoded);
      return result;
    };


    const AesGCMEncrypt = async (keyStr: string, iv: string, inputByteData: Uint8Array) => {
        const keySize = 256;
        return await aesEncrypt('AES-GCM', keyStr, keySize, iv, inputByteData);
    };
    ```


=== "Python"

    ```bash title="Install cryptography"
    pip install cryptography
    ```

    ```python
    import base64

    from cryptography.hazmat.primitives import padding
    from cryptography.hazmat.primitives.ciphers import Cipher, algorithms, modes
    from cryptography.hazmat.backends import default_backend


    class AESCrypto(object):
        """AESCrypto."""

        def __init__(self, aes_key, aes_iv):
            if not isinstance(aes_key, bytes):
                aes_key = aes_key.encode()

            if not isinstance(aes_iv, bytes):
                aes_iv = aes_iv.encode()

            self.aes_key = aes_key
            self.aes_iv = aes_iv


        def gcm_encrypt(self, data):
            encryptor = Cipher(
                algorithms.AES(self.aes_key),
                modes.GCM(self.aes_iv),
                backend=default_backend()
            ).encryptor()

            # associated_data will be authenticated but not encrypted,
            # it must also be passed in on decryption.
            # encryptor.authenticate_additional_data(associated_data)

            if isinstance(data, str):
                data = data.encode("utf-8")

            ciphertext = encryptor.update(data) + encryptor.finalize()

            result = ciphertext + encryptor.tag
            return result

        def gcm_decrypt(self, bytes_data):
            tag = bytes_data[-16:]
            ciphertext = bytes_data[:-16]

            decryptor = Cipher(
                algorithms.AES(self.aes_key),
                modes.GCM(self.aes_iv, tag),
                backend=default_backend()
            ).decryptor()

            # We put associated_data back in or the tag will fail to verify
            # when we finalize the decryptor.
            # decryptor.authenticate_additional_data(associated_data)

            result = decryptor.update(ciphertext) + decryptor.finalize()

            return result.decode("utf-8")



    aes = AESCrypto(key, iv)
    byte_data = aes.gcm_encrypt("hello".encode("utf-8"))

    text = aes.gcm_decrypt(byte_data)
    ```

=== "Golang"

    ```bash
    go install cryptography
    ```
