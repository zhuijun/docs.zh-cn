---
title: 将对象标识符映射到加密算法
ms.date: 03/30/2017
helpviewer_keywords:
- digital signatures
- identifiers, mapping object identifiers
- cryptographic algorithms
- mapping object identifiers
- cryptography, mapping object identifiers
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
ms.openlocfilehash: a5aebac2d392d4540581dfe7c7afff0819968ac0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "69912544"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a><span data-ttu-id="32df6-102">将对象标识符映射到加密算法</span><span class="sxs-lookup"><span data-stu-id="32df6-102">Mapping Object Identifiers to Cryptography Algorithms</span></span>
<span data-ttu-id="32df6-103">数字签名确保在将数据从一个程序发送到另一个程序时，数据不会被篡改。</span><span class="sxs-lookup"><span data-stu-id="32df6-103">Digital signatures ensure that data is not tampered with when it is sent from one program to another.</span></span> <span data-ttu-id="32df6-104">通常通过将数学函数应用于要签名的数据的哈希来计算数字签名。</span><span class="sxs-lookup"><span data-stu-id="32df6-104">Typically the digital signature is computed by applying a mathematical function to the hash of the data to be signed.</span></span> <span data-ttu-id="32df6-105">设置要签名的哈希值的格式时，某些数字签名算法会在格式设置操作过程中追加一个 "ASN. 1" 对象标识符（OID）。</span><span class="sxs-lookup"><span data-stu-id="32df6-105">When formatting a hash value to be signed, some digital signature algorithms append an ASN.1 Object Identifier (OID) as part of the formatting operation.</span></span> <span data-ttu-id="32df6-106">OID 标识用于计算哈希的算法。</span><span class="sxs-lookup"><span data-stu-id="32df6-106">The OID identifies the algorithm that was used to compute the hash.</span></span> <span data-ttu-id="32df6-107">可以将算法映射到对象标识符，以将加密机制扩展为使用自定义算法。</span><span class="sxs-lookup"><span data-stu-id="32df6-107">You can map algorithms to object identifiers to extend the cryptography mechanism to use custom algorithms.</span></span> <span data-ttu-id="32df6-108">下面的示例演示如何将对象标识符映射到新的哈希算法。</span><span class="sxs-lookup"><span data-stu-id="32df6-108">The following example shows how to map an object identifier to a new hash algorithm.</span></span>  
  
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
  
 <span data-ttu-id="32df6-109">[ \<oidEntry> 元素](./file-schema/cryptography/oidentry-element.md)包含两个属性。</span><span class="sxs-lookup"><span data-stu-id="32df6-109">The [\<oidEntry> element](./file-schema/cryptography/oidentry-element.md) contains two attributes.</span></span> <span data-ttu-id="32df6-110">**OID**特性是对象标识符号。</span><span class="sxs-lookup"><span data-stu-id="32df6-110">The **OID** attribute is the object identifier number.</span></span> <span data-ttu-id="32df6-111">**Name**属性是[ \<nameEntry> 元素](./file-schema/cryptography/nameentry-element.md)中**name**属性的值。</span><span class="sxs-lookup"><span data-stu-id="32df6-111">The **name** attribute is the value of the **name** attribute from the [\<nameEntry> element](./file-schema/cryptography/nameentry-element.md).</span></span> <span data-ttu-id="32df6-112">在将对象标识符映射到简单名称之前，必须先将算法名称映射到类。</span><span class="sxs-lookup"><span data-stu-id="32df6-112">There must be a mapping from an algorithm name to a class before an object identifier can be mapped to a simple name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32df6-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="32df6-113">See also</span></span>

- [<span data-ttu-id="32df6-114">配置加密类</span><span class="sxs-lookup"><span data-stu-id="32df6-114">Configuring Cryptography Classes</span></span>](configure-cryptography-classes.md)
- [<span data-ttu-id="32df6-115">加密服务</span><span class="sxs-lookup"><span data-stu-id="32df6-115">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)
