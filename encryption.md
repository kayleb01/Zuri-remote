# Encryption of a String

OpenSSL is one of the Cryptography Extensions in PHP

```
class EncryptString
{
     const METHOD = 'aes-256-ctr';

     public function encrypt($message, $key, $encode = false) {
        $opsl = openssl_cipher_iv_length(self::METHOD);
        $nonce = openssl_random_pseudo_bytes($opsl);
        
        $ciphertext = openssl_encrypt(
            $message,
            self::METHOD,
            $key,
            OPENSSL_RAW_DATA,
            $nonce
        );
        
        if ($encode) {
            return base64_encode($nonce.$ciphertext);
        }
        return $nonce.$ciphertext;

     }
}
```