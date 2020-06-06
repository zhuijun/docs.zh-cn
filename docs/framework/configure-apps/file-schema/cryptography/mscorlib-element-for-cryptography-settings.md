---
title: Cryptography 设置的 <mscorlib> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
ms.openlocfilehash: d1d805f7154c18dba2dcd4eb7228cc200d8da811
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155176"
---
# <a name="mscorlib-element-for-cryptography-settings"></a><span data-ttu-id="25785-102">Cryptography 设置的 \<mscorlib> 元素</span><span class="sxs-lookup"><span data-stu-id="25785-102">\<mscorlib> Element for Cryptography Settings</span></span>
<span data-ttu-id="25785-103">包含[ \<cryptographySettings> 元素](cryptographysettings-element.md)。</span><span class="sxs-lookup"><span data-stu-id="25785-103">Contains the [\<cryptographySettings> element](cryptographysettings-element.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<mscorlib>**  
  
## <a name="syntax"></a><span data-ttu-id="25785-104">语法</span><span class="sxs-lookup"><span data-stu-id="25785-104">Syntax</span></span>  
  
```xml  
      <mscorlib>
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25785-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="25785-105">Attributes and Elements</span></span>  
 <span data-ttu-id="25785-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="25785-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25785-107">特性</span><span class="sxs-lookup"><span data-stu-id="25785-107">Attributes</span></span>  
 <span data-ttu-id="25785-108">无。</span><span class="sxs-lookup"><span data-stu-id="25785-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="25785-109">子元素</span><span class="sxs-lookup"><span data-stu-id="25785-109">Child Elements</span></span>  
  
|<span data-ttu-id="25785-110">元素</span><span class="sxs-lookup"><span data-stu-id="25785-110">Element</span></span>|<span data-ttu-id="25785-111">说明</span><span class="sxs-lookup"><span data-stu-id="25785-111">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="25785-112">包含加密设置。</span><span class="sxs-lookup"><span data-stu-id="25785-112">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="25785-113">父元素</span><span class="sxs-lookup"><span data-stu-id="25785-113">Parent Elements</span></span>  
  
|<span data-ttu-id="25785-114">元素</span><span class="sxs-lookup"><span data-stu-id="25785-114">Element</span></span>|<span data-ttu-id="25785-115">说明</span><span class="sxs-lookup"><span data-stu-id="25785-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="25785-116">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="25785-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="25785-117">示例</span><span class="sxs-lookup"><span data-stu-id="25785-117">Example</span></span>  
 <span data-ttu-id="25785-118">下面的示例演示如何使用 **\<mscorlib>** 元素来引用加密类并配置运行时。</span><span class="sxs-lookup"><span data-stu-id="25785-118">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="25785-119">然后，你可以将字符串 "RSA" 传递给 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> 方法，并使用 <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> 方法返回 `MyCryptoRSAClass` 对象。</span><span class="sxs-lookup"><span data-stu-id="25785-119">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="25785-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="25785-120">See also</span></span>

- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="25785-121">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="25785-121">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="25785-122">密码设置架构</span><span class="sxs-lookup"><span data-stu-id="25785-122">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="25785-123">加密服务</span><span class="sxs-lookup"><span data-stu-id="25785-123">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="25785-124">配置加密类</span><span class="sxs-lookup"><span data-stu-id="25785-124">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
