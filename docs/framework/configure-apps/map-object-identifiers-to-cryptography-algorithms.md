---
title: 将对象标识符映射到加密算法
description: 请参阅如何使用 XML 配置文件中的 y 和 y 元素将对象标识符（OID）映射到 .NET 中的加密算法。
ms.date: 03/30/2017
helpviewer_keywords:
- digital signatures
- identifiers, mapping object identifiers
- cryptographic algorithms
- mapping object identifiers
- cryptography, mapping object identifiers
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
ms.openlocfilehash: e22510014071455b83ba28cd82690b5ecdce9bc9
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141999"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a><span data-ttu-id="66fd6-103">将对象标识符映射到加密算法</span><span class="sxs-lookup"><span data-stu-id="66fd6-103">Mapping Object Identifiers to Cryptography Algorithms</span></span>
<span data-ttu-id="66fd6-104">数字签名确保在将数据从一个程序发送到另一个程序时，数据不会被篡改。</span><span class="sxs-lookup"><span data-stu-id="66fd6-104">Digital signatures ensure that data is not tampered with when it is sent from one program to another.</span></span> <span data-ttu-id="66fd6-105">通常通过将数学函数应用于要签名的数据的哈希来计算数字签名。</span><span class="sxs-lookup"><span data-stu-id="66fd6-105">Typically the digital signature is computed by applying a mathematical function to the hash of the data to be signed.</span></span> <span data-ttu-id="66fd6-106">设置要签名的哈希值的格式时，某些数字签名算法会在格式设置操作过程中追加一个 "ASN. 1" 对象标识符（OID）。</span><span class="sxs-lookup"><span data-stu-id="66fd6-106">When formatting a hash value to be signed, some digital signature algorithms append an ASN.1 Object Identifier (OID) as part of the formatting operation.</span></span> <span data-ttu-id="66fd6-107">OID 标识用于计算哈希的算法。</span><span class="sxs-lookup"><span data-stu-id="66fd6-107">The OID identifies the algorithm that was used to compute the hash.</span></span> <span data-ttu-id="66fd6-108">可以将算法映射到对象标识符，以将加密机制扩展为使用自定义算法。</span><span class="sxs-lookup"><span data-stu-id="66fd6-108">You can map algorithms to object identifiers to extend the cryptography mechanism to use custom algorithms.</span></span> <span data-ttu-id="66fd6-109">下面的示例演示如何将对象标识符映射到新的哈希算法。</span><span class="sxs-lookup"><span data-stu-id="66fd6-109">The following example shows how to map an object identifier to a new hash algorithm.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MyNewHash="MyNewHashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="NewHash" class="MyNewHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.14.33.42.46"  name="NewHash"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 <span data-ttu-id="66fd6-110">[ \<oidEntry> 元素](./file-schema/cryptography/oidentry-element.md)包含两个属性。</span><span class="sxs-lookup"><span data-stu-id="66fd6-110">The [\<oidEntry> element](./file-schema/cryptography/oidentry-element.md) contains two attributes.</span></span> <span data-ttu-id="66fd6-111">**OID**特性是对象标识符号。</span><span class="sxs-lookup"><span data-stu-id="66fd6-111">The **OID** attribute is the object identifier number.</span></span> <span data-ttu-id="66fd6-112">**Name**属性是[ \<nameEntry> 元素](./file-schema/cryptography/nameentry-element.md)中**name**属性的值。</span><span class="sxs-lookup"><span data-stu-id="66fd6-112">The **name** attribute is the value of the **name** attribute from the [\<nameEntry> element](./file-schema/cryptography/nameentry-element.md).</span></span> <span data-ttu-id="66fd6-113">在将对象标识符映射到简单名称之前，必须先将算法名称映射到类。</span><span class="sxs-lookup"><span data-stu-id="66fd6-113">There must be a mapping from an algorithm name to a class before an object identifier can be mapped to a simple name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66fd6-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="66fd6-114">See also</span></span>

- [<span data-ttu-id="66fd6-115">配置加密类</span><span class="sxs-lookup"><span data-stu-id="66fd6-115">Configuring Cryptography Classes</span></span>](configure-cryptography-classes.md)
- [<span data-ttu-id="66fd6-116">加密服务</span><span class="sxs-lookup"><span data-stu-id="66fd6-116">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)
