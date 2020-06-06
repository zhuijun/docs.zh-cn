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
ms.openlocfilehash: a28eaf68fe1e6ab3f26592eee5ae2d0f2e7a3256
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155162"
---
# <a name="oidmap-element"></a><span data-ttu-id="bf278-102">\<oidMap> 元素</span><span class="sxs-lookup"><span data-stu-id="bf278-102">\<oidMap> Element</span></span>
<span data-ttu-id="bf278-103">包含与类的 ASN 对象标识符（OID）映射。</span><span class="sxs-lookup"><span data-stu-id="bf278-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidMap>**

## <a name="syntax"></a><span data-ttu-id="bf278-104">语法</span><span class="sxs-lookup"><span data-stu-id="bf278-104">Syntax</span></span>  
  
```xml  
<oidMap>
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf278-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="bf278-105">Attributes and Elements</span></span>  
 <span data-ttu-id="bf278-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bf278-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf278-107">特性</span><span class="sxs-lookup"><span data-stu-id="bf278-107">Attributes</span></span>  
 <span data-ttu-id="bf278-108">无。</span><span class="sxs-lookup"><span data-stu-id="bf278-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bf278-109">子元素</span><span class="sxs-lookup"><span data-stu-id="bf278-109">Child Elements</span></span>  
  
|<span data-ttu-id="bf278-110">元素</span><span class="sxs-lookup"><span data-stu-id="bf278-110">Element</span></span>|<span data-ttu-id="bf278-111">说明</span><span class="sxs-lookup"><span data-stu-id="bf278-111">Description</span></span>|  
|-------------|-----------------|  
|[\<oidEntry>](oidentry-element.md)|<span data-ttu-id="bf278-112">将一个 asn.1 OID 映射到友好名称。</span><span class="sxs-lookup"><span data-stu-id="bf278-112">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bf278-113">父元素</span><span class="sxs-lookup"><span data-stu-id="bf278-113">Parent Elements</span></span>  
  
|<span data-ttu-id="bf278-114">元素</span><span class="sxs-lookup"><span data-stu-id="bf278-114">Element</span></span>|<span data-ttu-id="bf278-115">说明</span><span class="sxs-lookup"><span data-stu-id="bf278-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bf278-116">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="bf278-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="bf278-117">包含加密设置。</span><span class="sxs-lookup"><span data-stu-id="bf278-117">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="bf278-118">包含 `cryptographySettings` 元素。</span><span class="sxs-lookup"><span data-stu-id="bf278-118">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bf278-119">示例</span><span class="sxs-lookup"><span data-stu-id="bf278-119">Example</span></span>  
 <span data-ttu-id="bf278-120">下面的示例演示如何使用元素来 **\<oidMap>** 包含 RIPEMD-160 哈希算法的 OID 到哈希算法的实现的映射。</span><span class="sxs-lookup"><span data-stu-id="bf278-120">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bf278-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="bf278-121">See also</span></span>

- [<span data-ttu-id="bf278-122">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="bf278-122">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="bf278-123">密码设置架构</span><span class="sxs-lookup"><span data-stu-id="bf278-123">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bf278-124">加密服务</span><span class="sxs-lookup"><span data-stu-id="bf278-124">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="bf278-125">配置加密类</span><span class="sxs-lookup"><span data-stu-id="bf278-125">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="bf278-126">将对象标识符映射到加密算法</span><span class="sxs-lookup"><span data-stu-id="bf278-126">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
