---
layout: post
keywords: crypto,encode,hash 
description: crypto
title: "crypto,encode,hash"
categories: [crypto]
tags: [crypto,encode,hash]
---
{% include codepiano/setup %}

## cryptography & hash function & encoding

### cryptography

* 加解密
* 加密hash
* Mac-加密hash

### hash function

* 普通的hash (Non-cryptographic hash functions)  MurMurHash. It's not difficult to reverse from digest to message
* 加密hash (Unkeyed cryptographic hash functions)  MD5/SHA1/SHA256...
* (Keyed cryptographic hash functions)  HMAC

### encoding

* encoding/decoding  Base64

encrypted
decrypt

HMAC alongside AES (encrypt data)

* AES is encryption; (Advanced Encryption Standard)
  * 对称加密 symmetric-key algorithm, meaning the same key is used for both encrypting and decrypting the data.
  * key size of 128, 192, or 256 bits
  * original name Rijndael
* DES  Data Encryption Standard (DES)
  * AES 接替 DES

* cipher

> In cryptography, a block cipher is a deterministic algorithm operating on fixed-length groups of bits, called blocks. It uses an unvarying transformation, that is, it uses a symmetric key. 

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
    * md5/SHA1/SHA256/SHA224
* 哈希-加盐(salt/key)
    * 不加盐，同一hash算法，hash后的串相同
    * 加盐，同一hash算法，相同原串后的串不同
    * HMAC-SHA1/HMAC-md5/HMAC-xxx
    * brute forced/hash collision
* 编解码(encode/decode)
    * 原始串
    * 编码串
    * Base64 (公开算法，可编解码)


* 对称加密(symmetric key) & 非对称加密(asymmetric)
   * 对称：DES/AES/Blowfish/Twofish
   * 非对称：RSA/DSA/ECDSA/ED25519

* Difference between SALT and KEY. Encryption

message authentication codes (MACs)
digital signatures

The ideal cryptographic hash function has six main properties:

* Deterministic: the same message always results in the same hash;
* Quick: it is quick to compute the hash value for any given message;
* One-way function: it is infeasible to generate a message from its hash value except by trying all possible messages;
* Avalanche effect: a small change to a message should change the hash value so extensively that the new hash value appears uncorrelated with the old hash value;
* Collision resistant: it is infeasible to find two different messages with the same hash value
* Pre-image attack resistant: a pre-image attack on cryptographic hash functions tries to find a message that has a specific hash value. A cryptographic hash function should resist attacks on its pre-image.

* hash 分类

  * 普通的hash (Non-cryptographic hash functions)  MurMurHash. It's not difficult to reverse from digest to message
  * 加密hash (Unkeyed cryptographic hash functions)  MD5/SHA1/SHA256...
  * (Keyed cryptographic hash functions)  HMAC

* Cryptography

* information security / 信息安全
  * data confidentiality / 数据保密
  * data integrity / 数据完整性
  * non-repudiation / 
  * authentication / 认证

* jwt 使用

* MAC
  信息传输、保存后，数据的完整性

* Hashing is a one-way function where data is mapped to a fixed-length value. Hashing is primarily used for authentication
* Salting is an additional step during hashing, typically seen in association to hashed passwords, that adds an additional value to the end of the password that changes the hash value produced.

* Difference between salted hash and keyed hashing?

> [difference-encryption-hashing-salting](https://www.thesslstore.com/blog/difference-encryption-hashing-salting)
> [Difference between salted hash and keyed hashing](https://crypto.stackexchange.com/questions/10757/difference-between-salted-hash-and-keyed-hashing)
> [Difference-between salted hash and keyed hashing](https://crypto.stackexchange.com/questions/10757/difference-between-salted-hash-and-keyed-hashing)
>
> * Keyed hashing is usually used to build message authentication codes (MACs), the most common of which is the hashed-based MAC (HMAC).
>   * secret key
>   * should be as fast as possible
>   * 防篡改
> * Salted hashing are intended to deter brute-force attacks , they are intentionally designed to be slow.
>   * 防暴力攻击(brute-force attacks)
>   * designed to be slow
>   * salts are not assumed to be secret.
> 

* 能不能逆转
* hash 不能
* 加密 能
* 逆转是否使用密码
* 加解密  使用
* 编解码(encoding/decoding) 不使用