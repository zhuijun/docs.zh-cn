---
ms.openlocfilehash: 32030698c12de87daef5e1d8851a0f55ec36d688
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720934"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a>Pkcs8PrivateKeyInfo 构造函数中更好的参数验证

从 .NET Core 3.0 预览版 9 开始，`Pkcs8PrivateKeyInfo` 构造函数将 `algorithmParameters` 参数作为单一 BER 编码值进行验证。

#### <a name="change-description"></a>更改描述

在 .NET Core 3.0 预览版 9 之前，[`Pkcs8PrivateKeyInfo` 构造函数](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))不验证 `algorithmParameters` 参数。  如果此参数表示的值无效，构造函数仍会成功，但对任何 <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>、<xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>、<xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A> 或 <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> 方法的调用将引发 <xref:System.ArgumentException>（对于其不接受的参数）(`preEncodedValue`) 或 <xref:System.Security.Cryptography.CryptographicException>。

如果运行 .NET Core 3.0 预览版 9 之前的版本，则以下代码仅在调用 <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> 方法时引发异常：

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

从 .NET Core 3.0 预览版 9 开始，参数在构造函数中进行验证，无效值导致方法引发 <xref:System.Security.Cryptography.CryptographicException>。 此更改使异常更接近数据错误源。 例如：

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a>引入的版本

3.0 预览版 9

#### <a name="recommended-action"></a>建议操作

请确保只提供有效的 `algorithmParameters` 值，否则对 `Pkcs8PrivateKeyInfo` 构造函数的调用既测试 <xref:System.ArgumentException> 也测试 <xref:System.Security.Cryptography.CryptographicException>（如果需要异常处理）。

#### <a name="category"></a>类别

密码

#### <a name="affected-apis"></a>受影响的 API

- [Pkcs8PrivateKeyInfo 构造函数](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
