---
layout: post
keywords: crypto,encode,hash 
description: crypto
title: "crypto,encode,hash"
categories: [crypto]
tags: [crypto,encode,hash]
---
{% include codepiano/setup %}

encrypted

decrypt

HMAC alongside AES (encrypt data)

* AES is encryption; (Advanced Encryption Standard)
  * 对称加密 symmetric-key algorithm,
  * key size of 128, 192, or 256 bits
* DES  Data Encryption Standard (DES)
  * AES 接替 DES


* HMAC is a nice MAC algorithm

* Base64
  * 可逆。decodable/reversible. hash不是
  * encode后的字符串长度不定，受原字符串影响。 hash(md5/SHA1/SHA256...)hash后长度一定

* SHA
   * hash ()
   * Secure Hash Algorithm 
   * SHA-1, SHA-256
   * produce digest
* AES
  * Advanced Encryption Standard
  * 加解密 encrypt/decrypt

* 加解密
    * 原始串 (plaintext)
    * 秘钥 (key)
    * 加密串(ciphertext)
    * AES/DES
* 哈希
    * 原始串
    * 哈希后digest
    * md5/SHA1/SHA256
* 编解码(encode/decode)
    * 原始串
    * 编码串
    * Base64 (公开算法，可编解码)
* 哈希-加盐(salt/key)
    * 不加盐，同一hash算法，hash后的串相同
    * 加盐，同一hash算法，相同原串后的串不同
    * HMAC-SHA1/hmac-md5
    * brute forced/hash collision

* 对称加密(symmetric key) & 非对称加密(asymmetric)
   * 对称：DES/AES/Blowfish/Twofish
   * 非对称：RSA