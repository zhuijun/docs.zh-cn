---
title: <cryptoNameMapping> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
ms.openlocfilehash: d31c5cd52ffe0e2a6eb5784735e76436d216444b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155214"
---
# <a name="cryptonamemapping-element"></a><span data-ttu-id="16313-102">\<cryptoNameMapping> 元素</span><span class="sxs-lookup"><span data-stu-id="16313-102">\<cryptoNameMapping> Element</span></span>
<span data-ttu-id="16313-103">包含类到友好名称的映射。</span><span class="sxs-lookup"><span data-stu-id="16313-103">Contains mappings of classes to friendly names.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoNameMapping>**

## <a name="syntax"></a><span data-ttu-id="16313-104">语法</span><span class="sxs-lookup"><span data-stu-id="16313-104">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16313-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="16313-105">Attributes and Elements</span></span>  
 <span data-ttu-id="16313-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="16313-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16313-107">特性</span><span class="sxs-lookup"><span data-stu-id="16313-107">Attributes</span></span>  
 <span data-ttu-id="16313-108">无。</span><span class="sxs-lookup"><span data-stu-id="16313-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="16313-109">子元素</span><span class="sxs-lookup"><span data-stu-id="16313-109">Child Elements</span></span>  
  
|<span data-ttu-id="16313-110">元素</span><span class="sxs-lookup"><span data-stu-id="16313-110">Element</span></span>|<span data-ttu-id="16313-111">说明</span><span class="sxs-lookup"><span data-stu-id="16313-111">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="16313-112">包含加密类的列表，这些类具有到元素中的友好名称的映射 **\<nameEntry>** 。</span><span class="sxs-lookup"><span data-stu-id="16313-112">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="16313-113">将类名称映射到友好算法名称，允许一个类具有多个友好名称。</span><span class="sxs-lookup"><span data-stu-id="16313-113">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="16313-114">父元素</span><span class="sxs-lookup"><span data-stu-id="16313-114">Parent Elements</span></span>  
  
|<span data-ttu-id="16313-115">元素</span><span class="sxs-lookup"><span data-stu-id="16313-115">Element</span></span>|<span data-ttu-id="16313-116">说明</span><span class="sxs-lookup"><span data-stu-id="16313-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="16313-117">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="16313-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="16313-118">包含加密设置。</span><span class="sxs-lookup"><span data-stu-id="16313-118">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="16313-119">包含类到友好名称的映射。</span><span class="sxs-lookup"><span data-stu-id="16313-119">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="16313-120">包含 \<cryptographySettings> 元素。</span><span class="sxs-lookup"><span data-stu-id="16313-120">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="16313-121">示例</span><span class="sxs-lookup"><span data-stu-id="16313-121">Example</span></span>  
 <span data-ttu-id="16313-122">下面的示例演示如何使用 **\<cryptoNameMapping>** 元素来引用加密类并配置运行时。</span><span class="sxs-lookup"><span data-stu-id="16313-122">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="16313-123">然后，你可以将字符串 "RSA" 传递给 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> 方法，并使用 <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> 方法返回 `MyCryptoRSAClass` 对象。</span><span class="sxs-lookup"><span data-stu-id="16313-123">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="16313-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="16313-124">See also</span></span>

- [<span data-ttu-id="16313-125">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="16313-125">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="16313-126">密码设置架构</span><span class="sxs-lookup"><span data-stu-id="16313-126">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="16313-127">加密服务</span><span class="sxs-lookup"><span data-stu-id="16313-127">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="16313-128">配置加密类</span><span class="sxs-lookup"><span data-stu-id="16313-128">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
