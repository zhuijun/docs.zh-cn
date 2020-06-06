---
title: <cryptographySettings> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
ms.openlocfilehash: fe6de09213c6f980e8eb205a318aae50033b2a84
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155227"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="3af32-102">\<cryptographySettings> 元素</span><span class="sxs-lookup"><span data-stu-id="3af32-102">\<cryptographySettings> Element</span></span>
<span data-ttu-id="3af32-103">包含加密设置。</span><span class="sxs-lookup"><span data-stu-id="3af32-103">Contains cryptography settings.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptographySettings>**

## <a name="syntax"></a><span data-ttu-id="3af32-104">语法</span><span class="sxs-lookup"><span data-stu-id="3af32-104">Syntax</span></span>  
  
```xml  
      <cryptographySettings>
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3af32-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="3af32-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3af32-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3af32-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3af32-107">特性</span><span class="sxs-lookup"><span data-stu-id="3af32-107">Attributes</span></span>  
 <span data-ttu-id="3af32-108">无。</span><span class="sxs-lookup"><span data-stu-id="3af32-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3af32-109">子元素</span><span class="sxs-lookup"><span data-stu-id="3af32-109">Child Elements</span></span>  
  
|<span data-ttu-id="3af32-110">元素</span><span class="sxs-lookup"><span data-stu-id="3af32-110">Element</span></span>|<span data-ttu-id="3af32-111">说明</span><span class="sxs-lookup"><span data-stu-id="3af32-111">Description</span></span>|  
|-------------|-----------------|  
|[\<cryptoNameMapping>](cryptonamemapping-element.md)|<span data-ttu-id="3af32-112">包含类到友好名称的映射。</span><span class="sxs-lookup"><span data-stu-id="3af32-112">Contains mappings of classes to friendly names.</span></span>|  
|[\<oidMap>](oidmap-element.md)|<span data-ttu-id="3af32-113">包含与类的 ASN 对象标识符（OID）映射。</span><span class="sxs-lookup"><span data-stu-id="3af32-113">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3af32-114">父元素</span><span class="sxs-lookup"><span data-stu-id="3af32-114">Parent Elements</span></span>  
  
|<span data-ttu-id="3af32-115">元素</span><span class="sxs-lookup"><span data-stu-id="3af32-115">Element</span></span>|<span data-ttu-id="3af32-116">说明</span><span class="sxs-lookup"><span data-stu-id="3af32-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3af32-117">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="3af32-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="3af32-118">包含 `cryptographySettings` 元素。</span><span class="sxs-lookup"><span data-stu-id="3af32-118">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3af32-119">示例</span><span class="sxs-lookup"><span data-stu-id="3af32-119">Example</span></span>  
 <span data-ttu-id="3af32-120">下面的示例演示如何使用 **\<cryptographySettings>** 元素包含加密名称映射和 OID 映射。</span><span class="sxs-lookup"><span data-stu-id="3af32-120">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="3af32-121">此示例将配置运行时，以便 <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> 返回 `MyHashClass` 对象， `MyCryptoClass` 类映射到对象标识符1.3.36.2.1。</span><span class="sxs-lookup"><span data-stu-id="3af32-121">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyHash="MyHashClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MyHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3af32-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="3af32-122">See also</span></span>

- [<span data-ttu-id="3af32-123">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="3af32-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="3af32-124">密码设置架构</span><span class="sxs-lookup"><span data-stu-id="3af32-124">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3af32-125">加密服务</span><span class="sxs-lookup"><span data-stu-id="3af32-125">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
