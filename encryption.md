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

$message = 'encrypt this string';
$key = hex2bin('000102030405060708090a0b0c0d0e0f101112131415161718191a1b1c1d1e1f');

$encrypted = EncryptString::encrypt($message, $key);
```