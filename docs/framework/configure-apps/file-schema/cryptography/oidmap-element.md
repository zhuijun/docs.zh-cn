---
title: <oidMap> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidMap
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap
helpviewer_keywords:
- <oidMap> element
- oidMap element
ms.assetid: 7f0c2246-c070-4748-b96a-2f66a296c539
ms.openlocfilehash: 6c57810389acbd58e6d2e05277a6f26fa0aac8c6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149512"
---
# <a name="oidmap-element"></a><span data-ttu-id="b7a94-102">\<oidMap> 元素</span><span class="sxs-lookup"><span data-stu-id="b7a94-102">\<oidMap> Element</span></span>

<span data-ttu-id="b7a94-103">包含) 映射到类 (OID 对象标识符。</span><span class="sxs-lookup"><span data-stu-id="b7a94-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidMap>**

## <a name="syntax"></a><span data-ttu-id="b7a94-104">语法</span><span class="sxs-lookup"><span data-stu-id="b7a94-104">Syntax</span></span>  
  
```xml  
<oidMap>
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7a94-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="b7a94-105">Attributes and Elements</span></span>  

 <span data-ttu-id="b7a94-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b7a94-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7a94-107">特性</span><span class="sxs-lookup"><span data-stu-id="b7a94-107">Attributes</span></span>  

 <span data-ttu-id="b7a94-108">无。</span><span class="sxs-lookup"><span data-stu-id="b7a94-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b7a94-109">子元素</span><span class="sxs-lookup"><span data-stu-id="b7a94-109">Child Elements</span></span>  
  
|<span data-ttu-id="b7a94-110">元素</span><span class="sxs-lookup"><span data-stu-id="b7a94-110">Element</span></span>|<span data-ttu-id="b7a94-111">描述</span><span class="sxs-lookup"><span data-stu-id="b7a94-111">Description</span></span>|  
|-------------|-----------------|  
|[\<oidEntry>](oidentry-element.md)|<span data-ttu-id="b7a94-112">将一个 asn.1 OID 映射到友好名称。</span><span class="sxs-lookup"><span data-stu-id="b7a94-112">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b7a94-113">父元素</span><span class="sxs-lookup"><span data-stu-id="b7a94-113">Parent Elements</span></span>  
  
|<span data-ttu-id="b7a94-114">元素</span><span class="sxs-lookup"><span data-stu-id="b7a94-114">Element</span></span>|<span data-ttu-id="b7a94-115">描述</span><span class="sxs-lookup"><span data-stu-id="b7a94-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b7a94-116">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="b7a94-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="b7a94-117">包含加密设置。</span><span class="sxs-lookup"><span data-stu-id="b7a94-117">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="b7a94-118">包含 `cryptographySettings` 元素。</span><span class="sxs-lookup"><span data-stu-id="b7a94-118">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b7a94-119">示例</span><span class="sxs-lookup"><span data-stu-id="b7a94-119">Example</span></span>  

 <span data-ttu-id="b7a94-120">下面的示例演示如何使用元素来 **\<oidMap>** 包含 RIPEMD-160 哈希算法的 OID 到哈希算法的实现的映射。</span><span class="sxs-lookup"><span data-stu-id="b7a94-120">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"  name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b7a94-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="b7a94-121">See also</span></span>

- [<span data-ttu-id="b7a94-122">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="b7a94-122">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b7a94-123">加密设置架构</span><span class="sxs-lookup"><span data-stu-id="b7a94-123">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b7a94-124">加密服务</span><span class="sxs-lookup"><span data-stu-id="b7a94-124">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="b7a94-125">配置加密类</span><span class="sxs-lookup"><span data-stu-id="b7a94-125">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="b7a94-126">将对象标识符映射到加密算法</span><span class="sxs-lookup"><span data-stu-id="b7a94-126">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
