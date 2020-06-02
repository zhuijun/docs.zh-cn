---
title: .NET Framework 加密模型
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET Framework], model
- encryption [.NET Framework], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
ms.openlocfilehash: c2d28abacd34736764b69be750a850a0f2e8db85
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288376"
---
# <a name="net-framework-cryptography-model"></a>.NET Framework 加密模型

.NET Framework 提供了许多标准加密算法的实现。 这些算法易于使用且具有最安全的可能默认属性。 此外，对象继承、流设计和配置的 .NET Framework 加密模型完全可扩展。

## <a name="object-inheritance"></a>对象继承

.NET Framework 安全系统实现派生类继承的可扩展模式。 层次结构如下所示：

- 算法类型类，如 <xref:System.Security.Cryptography.SymmetricAlgorithm>、<xref:System.Security.Cryptography.AsymmetricAlgorithm> 或 <xref:System.Security.Cryptography.HashAlgorithm>。 此级别是抽象的。

- 从算法类型类继承的算法类；例如，<xref:System.Security.Cryptography.Aes>、<xref:System.Security.Cryptography.RC2> 或 <xref:System.Security.Cryptography.ECDiffieHellman>。 此级别是抽象的。

- 从算法类继承的算法类实现；例如，<xref:System.Security.Cryptography.AesManaged>、<xref:System.Security.Cryptography.RC2CryptoServiceProvider> 或 <xref:System.Security.Cryptography.ECDiffieHellmanCng>。 此级别已完全实现。

使用此模式派生类，可轻松添加新算法或现有算法的新实现。 例如，要创建新的公共密钥算法，你会继承 <xref:System.Security.Cryptography.AsymmetricAlgorithm> 类。 要创建特定算法的新实现，将需要创建该算法的非抽象派生类。

## <a name="how-algorithms-are-implemented-in-the-net-framework"></a>算法在 .NET Framework 中的实现方式

作为可用于一种算法的不同实现的示例，请考虑对称算法。 所有对称算法都基于 <xref:System.Security.Cryptography.SymmetricAlgorithm>，它由以下算法继承：

* <xref:System.Security.Cryptography.Aes>
* <xref:System.Security.Cryptography.DES>
* <xref:System.Security.Cryptography.RC2>
* <xref:System.Security.Cryptography.Rijndael>
* <xref:System.Security.Cryptography.TripleDES>

<xref:System.Security.Cryptography.Aes> 由两个类继承：<xref:System.Security.Cryptography.AesCryptoServiceProvider> 和 <xref:System.Security.Cryptography.AesManaged>。 <xref:System.Security.Cryptography.AesCryptoServiceProvider> 类是围绕 Aes 的 Windows 加密 API (CAPI) 实现的包装器，而 <xref:System.Security.Cryptography.AesManaged> 类完全用托管代码编写。 除托管和 CAPI 实现外，还有第三种类型的实现，即下一代加密技术 (CNG)。 CNG 算法的一个示例是 <xref:System.Security.Cryptography.ECDiffieHellmanCng>。 CNG 算法在 Windows Vista 和更高版本中都可用。

你可以选择最适合自己的实现。 托管实现在支持 .NET Framework 的所有平台上可用。 CAPI 实现在较早版本的操作系统上可用，不再进行开发。 CNG 是要在其中进行新开发的最新实现。 但是，托管实现未获得美国联邦信息处理标准 (FIPS) 认证，并且可能比包装器类更慢。

## <a name="stream-design"></a>流设计

公共语言运行时使用面向流的设计实现对称算法和哈希算法。 这种设计的核心是 <xref:System.Security.Cryptography.CryptoStream> 类，该类派生自 <xref:System.IO.Stream> 类。 基于流的加密对象支持用于处理对象的数据传输部分的单个标准接口 (`CryptoStream`)。 由于所有对象都基于标准接口，因此可以将多个对象（例如，一个哈希对象后跟一个加密对象）链接起来，且无需任何中间存储来对数据执行多个操作。 使用流模型还可以从更小的对象生成对象。 例如，尽管该对象可能从一组流对象中生成，组合的加密和哈希算法仍可视为单个流对象。

## <a name="cryptographic-configuration"></a>加密配置

使用加密配置可将算法的特定实现解析为算法名称，从而允许 .NET Framework 加密类扩展性。 可以添加自己算法的硬件或软件实现，并将该实现映射到所选择的算法名称。 如果配置文件中未指定算法，则使用默认设置。 有关加密配置的详细信息，请参阅[配置加密类](../../framework/configure-apps/configure-cryptography-classes.md)。

## <a name="choosing-an-algorithm"></a>选择算法

可以出于各种原因选择一种算法：例如，为了保护数据完整性，为了保护数据隐私或为了生成密钥。 为了保护完整性（防止更改）或保护隐私（防止查看），对称算法和哈希算法用于保护数据。 哈希算法主要用于保护数据完整性。

下面是按应用程序分类的建议算法列表：

- 数据隐私：
  - <xref:System.Security.Cryptography.Aes>
- 数据完整性：
  - <xref:System.Security.Cryptography.HMACSHA256>
  - <xref:System.Security.Cryptography.HMACSHA512>
- 数字签名：
  - <xref:System.Security.Cryptography.ECDsa>
  - <xref:System.Security.Cryptography.RSA>
- 密钥交换：
  - <xref:System.Security.Cryptography.ECDiffieHellman>
  - <xref:System.Security.Cryptography.RSA>
- 随机数生成：
  - <xref:System.Security.Cryptography.RNGCryptoServiceProvider>
- 从密码生成密钥：
  - <xref:System.Security.Cryptography.Rfc2898DeriveBytes>

## <a name="see-also"></a>另请参阅

- [加密服务](cryptographic-services.md)
- [使用 C 中的 Bruce Schneier 应用加密协议、算法和源代码](https://www.schneier.com/books/applied_cryptography/)
