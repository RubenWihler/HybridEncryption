# EncryptionManager Class Documentation

## Overview

The `EncryptionManager` class provides a set of methods for performing combined RSA and AES encryption and decryption in C#. This class enables the generation of RSA key pairs, encryption of text using a combination of RSA and AES, and subsequent decryption of the encrypted text.

## Table of Contents

1. [RSA Key Generation](#rsa-key-generation)
2. [Text Encryption](#text-encryption)
3. [Text Decryption](#text-decryption)
4. [Private Methods](#private-methods)

## RSA Key Generation <a name="rsa-key-generation"></a>

```csharp
public static (string publicKey, string privateKey) GenerateRSAKeys()
```

### `GenerateRSAKeys` Method

#### Description

Generates a pair of private and public RSA keys and returns them as XML strings.

#### Signature

```csharp
public static (string publicKey, string privateKey) GenerateRSAKeys()
```

#### Parameters

None

#### Returns

- `publicKey`: The public RSA key in XML format.
- `privateKey`: The private RSA key in XML format.

#### Example

```csharp
var keys = EncryptionManager.GenerateRSAKeys();
var publicKey = keys.publicKey;
var privateKey = keys.privateKey;
```

## Text Encryption <a name="text-encryption"></a>

```csharp
public static (string text, string aesKey, string aesIV) Encrypt(string text, string publicKey)
```

### `Encrypt` Method

#### Description

Encrypts a given text using a combination of RSA and AES. It generates AES key and IV, encrypts them with the provided RSA public key, and then encrypts the text using AES.

#### Signature

```csharp
public static (string text, string aesKey, string aesIV) Encrypt(string text, string publicKey)
```

#### Parameters

- `text`: The text to be encrypted.
- `publicKey`: The target RSA public key in XML format.

#### Returns

- `text`: The encrypted text in Base64 format.
- `aesKey`: The encrypted AES key in Base64 format.
- `aesIV`: The encrypted AES initialization vector (IV) in Base```

#### Example

```csharp
var encryptionResult = EncryptionManager.Encrypt("Hello, World!", publicKey);
var encryptedText = encryptionResult.text;
var encryptedAESKey = encryptionResult.aesKey;
var encryptedAESIV = encryptionResult.aesIV;
```

## Text Decryption <a name="text-decryption"></a>

```csharp
public static string Decrypt(string encryptedText, string aesKey, string aesIV, string privateKey)
```

### `Decrypt` Method

#### Description

Decrypts the provided encrypted text. It decrypts the AES key and IV with the private RSA key and then uses them to decrypt the text.

#### Signature

```csharp
public static string Decrypt(string encryptedText, string aesKey, string aesIV, string privateKey)
```

#### Parameters

- `encryptedText`: The encrypted text in Base64 format.
- `aesKey`: The encrypted AES key in Base64 format.
- `aesIV`: The encrypted AES initialization vector (IV) in Base64 format.
- `privateKey`: The private RSA key in XML format.

#### Returns

- The decrypted text.

#### Example

```csharp
var decryptedText = EncryptionManager.Decrypt(encryptedText, encryptedAESKey, encryptedAESIV, privateKey);
```

## Private Methods <a name="private-methods"></a>

```csharp
private static byte[] RsaEncrypt(string data, string publicKey)
```

### `RsaEncrypt` Method

#### Description

Encrypts data using RSA encryption with the provided RSA public key.

#### Signature

```csharp
private static byte[] RsaEncrypt(string data, string publicKey)
```

#### Parameters

- `data`: The data to be encrypted in Base64 format.
- `publicKey`: The RSA public key in XML format.

#### Returns

- The encrypted data.

```csharp
private static byte[] RsaDecrypt(string data, string privateKey)
```

### `RsaDecrypt` Method

#### Description

Decrypts data using RSA decryption with the provided RSA private key.

#### Signature

```csharp
private static byte[] RsaDecrypt(string data, string privateKey)
```

#### Parameters

- `data`: The data to be decrypted in Base64 format.
- `privateKey`: The RSA private key in XML format.

#### Returns

- The decrypted data.

```csharp
private static byte[] AesEncrypt(string data, byte[] key, byte[] IV)
```

### `AesEncrypt` Method

#### Description

Encrypts data using AES encryption with the provided AES key and initialization vector (IV).

#### Signature

```csharp
private static byte[] AesEncrypt(string data, byte[] key, byte[] IV)
```

#### Parameters

- `data`: The data to be encrypted.
- `key`: The AES key.
- `IV`: The AES initialization vector (IV).

#### Returns

- The encrypted data.

```csharp
private static string AesDecrypt(byte[] cipherText, byte[] key, byte[] IV)
```

### `AesDecrypt` Method

#### Description

Decrypts data using AES decryption with the provided AES key and initialization vector (IV).

#### Signature

```csharp
private static string AesDecrypt(byte[] cipherText, byte[] key, byte[] IV)
```

#### Parameters

- `cipherText`: The encrypted data.
- `key`: The AES key.
- `IV`: The AES initialization vector (IV).

#### Returns

- The decrypted data.

```csharp
private static (byte[] key, byte[] IV) GenerateAESKey()
```

### `GenerateAESKey` Method

#### Description

Generates a pair of AES key and initialization vector (IV).

#### Signature

```csharp
private static (byte[] key, byte[] IV) GenerateAESKey()
```

#### Parameters

None

#### Returns

- `key`: The generated AES key.
- `IV`: The generated AES initialization vector (IV).
