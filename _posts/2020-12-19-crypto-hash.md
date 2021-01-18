---
layout: post
keywords: crypto,encode,hash 
description: crypto
title: "crypto,encode,hash"
categories: [crypto]
tags: [crypto,encode,hash]
---
{% include codepiano/setup %}

History of Cryptography

* The earlier Roman method of cryptography, popularly known as the Caesar Shift Cipher
* Steganography:invisible watermarking.

1. Caesar Cipher/Shift Cipher(not a secure cryptosystem)
2. Simple Substitution Cipher
3. Monoalphabetic and Polyalphabetic Cipher
4. Playfair Cipher
5. Vigenere Cipher
6. Variants of Vigenere Cipher
  6.1 One-Time Pad
    6.1.1 Shift Cipher − Easy to Break
    6.1.2 One-time Pad − Impossible to Break
  6.2 Transposition Cipher

Block Ciphers(DES、AES)

* Feistel Block Cipher (DES)
* Encryption/Decryption Process
  * Number of Rounds
  * efficiency–security tradeoff

Stream Ciphers

Evolution of Cryptography

* Vigenere Coding
* the more sophisticated art and science of information security
* Enigma rotor machine
* cryptography and cryptanalysis

Security Services of Cryptography

* Confidentiality
* Data Integrity: 检测数据是否被修改
* Authentication

## cryptography & hash function & encoding

### cryptography

* 加解密
* 加密hash
* Mac-加密hash

Components of a Cryptosystem

* Plaintext
* Encryption Algorithm.
* Ciphertext
* Decryption Algorithm
* Encryption Key
* Decryption Key

Types of Cryptosystems

* Symmetric Key : same keys are used for encrypting and decrypting − Digital Encryption Standard (DES), Triple-DES (3DES), IDEA, and BLOWFISH.
* Asymmetric Key : different keys are used for encrypting and decrypting the information

Challenge of Symmetric Key Cryptosystem

* Key establishment
* Trust Issue

Asymmetric Key Encryption

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

## Cryptographic hash function

* data of arbitrary size (often called the "message") to a bit array of a fixed size (the "hash value", "hash", or "message digest").
* one-way function
* infeasible to invert
* the only way:  brute-force search / use a rainbow table of matched hashes

### properties

* deterministic(确定性)：the same message always results in the same hash
* quick(速度快)
* infeasible to reverse(不可逆，one way)
* infeasible to find two different messages with the same hash value(没有2个数据hash是相同的，实际是很少)
* a small change to a message should change the hash value so extensively(很小的变化，hash value变化很大)

* 对称加密(symmetric key) & 非对称加密(asymmetric)
   * 对称：DES/AES/Blowfish/Twofish
   * 非对称：RSA/DSA/ECDSA/ED25519

* Difference between SALT and KEY. Encryption

message authentication codes (MACs)
digital signatures / 使用private-key签名，使用public-key验证(verify)

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

  * Fixed Length Output (Hash Value) 固定长度输出
  * Efficiency of Operation 速度快，一般都比对称加密快

  * Message Digest (MD)
    * In 2004, collisions were found in MD5.This collision attack resulted in compromised MD5 and hence it is no longer recommended for use.
  * Secure Hash Function (SHA) [14]
    * SHA-0, SHA-1, SHA-2, and SHA-3
    * SHA-1, Secure Socket Layer (SSL) security. In 2005, a method was found for uncovering collisions for SHA-1 within practical time frame making long-term employability of SHA-1 doubtful.
    * SHA-2,  No successful attacks have yet been reported on SHA-2 hash function.
    * In October 2012, the NIST chose the Keccak algorithm as the new SHA-3 standard.
  * RIPEMD
  * Whirlpool

* hash常见应用场景 （Applications of Hash Functions）
  * Password Storage/密码保存
  * Data Integrity Check/数据完整性检查


* Cryptography

* information security / 信息安全
  * data confidentiality / 数据保密
  * data integrity / 数据完整性
  * non-repudiation / 
  * authentication / 认证

* jwt 使用

* MAC
  信息传输、保存后，数据的完整性
  G (key-generator) gives the key k on input 1n, where n is the security parameter.
  S (signing) outputs a tag t on the key k and the input string x.
  V (verifying) outputs accepted or rejected on inputs: the key k, the string x and the tag t.

  * MAC algorithm is a symmetric key cryptographic technique/对称加密技术 [13]

* hash 和 mac主要解决的应用场景
  * sender提供了message和digest。 receiver已经知道digest，只需要验证message是否被修改。[hash]
  * sender提供了message和digest。 receiver不知道digest，也是通过非安全渠道获取到digest的。如果攻击者，同时修改message和digest，那么receiver就不知道了。
  这时使用mac，攻击者如果修改了message，但是不知道key，所以无法修改digest，这样receiver就能验证。[mac]

* Hashing is a one-way function where data is mapped to a fixed-length value. Hashing is primarily used for authentication
* Salting is an additional step during hashing, typically seen in association to hashed passwords, that adds an additional value to the end of the password that changes the hash value produced.

* Difference between salted hash and keyed hashing?

> [difference-encryption-hashing-salting](https://www.thesslstore.com/blog/difference-encryption-hashing-salting)
> [Difference between salted hash and keyed hashing](https://crypto.stackexchange.com/questions/10757/difference-between-salted-hash-and-keyed-hashing)
> [Encryption, hashing, salting – what’s the difference?](https://www.comparitech.com/blog/information-security/encryption-hashing-salting/)
>
> * Keyed hashing is usually used to build message authentication codes (MACs), the most common of which is the hashed-based MAC (HMAC).
>   * secret key
>   * should be as fast as possible
>   * 防篡改
> * Salted hashing are intended to deter brute-force attacks , they are intentionally designed to be slow.
>   * 防暴力攻击(brute-force attacks)
>   * designed to be slow
>   * salts are not assumed to be secret.

* 能不能逆转
* hash 不能
* 加密 能
* 逆转是否使用密码
* 加解密  使用
* 编解码(encoding/decoding) 不使用

Attacks

* Passive Attacks ： “偷看”未授权的信息
* Active Attacks：修改信息

1. [checksum](https://en.wikipedia.org/wiki/Checksum)
2. [hash_function](https://en.wikipedia.org/wiki/Hash_function)
3. [base64](https://en.wikipedia.org/wiki/Base64)
4. [purpose of Base64](https://stackoverflow.com/questions/10315757/what-is-the-real-purpose-of-base64-encodingx)
5. [CryptoJS-online](https://codepen.io/gabrielizalo/pen/oLzaqx)
6. [HMAC](https://en.wikipedia.org/wiki/HMAC#:~:text=In%20cryptography%2C%20an%20HMAC%20(sometimes,and%20a%20secret%20cryptographic%20key.)
7. [blockchain](http://www.ruanyifeng.com/blog/2017/12/blockchain-tutorial.html)
8. [比特币如何运作](https://mp.weixin.qq.com/s/g9Pq2mDl01vfi4a5O_R7vA)
9. [What is Blockchain Hashing?](https://hedgetrade.com/what-is-blockchain-hashing/)
10. [How does a blockchain work - Simply Explained-Youtube](https://www.youtube.com/watch?v=SSo_EIwHSd4)
11. [Cryptographic hash function](https://en.wikipedia.org/wiki/Cryptographic_hash_function)
12. [mac](https://en.wikipedia.org/wiki/Message_authentication_code)
13. [Message Authentication](https://www.tutorialspoint.com/cryptography/message_authentication.htm)
14. [Cryptography Hash functions](https://www.tutorialspoint.com/cryptography/cryptography_hash_functions.htm)