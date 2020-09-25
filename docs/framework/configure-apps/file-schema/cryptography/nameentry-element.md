---
title: <nameEntry> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
ms.openlocfilehash: 4341b1fcd3762e5aa55f0ba988f7f49d4b5cacd6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201767"
---
# <a name="nameentry-element"></a><span data-ttu-id="38b80-102">\<nameEntry> 元素</span><span class="sxs-lookup"><span data-stu-id="38b80-102">\<nameEntry> Element</span></span>

<span data-ttu-id="38b80-103">将类名称映射到友好算法名称，允许一个类具有多个友好名称。</span><span class="sxs-lookup"><span data-stu-id="38b80-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameEntry>**  
  
## <a name="syntax"></a><span data-ttu-id="38b80-104">语法</span><span class="sxs-lookup"><span data-stu-id="38b80-104">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38b80-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="38b80-105">Attributes and Elements</span></span>  

 <span data-ttu-id="38b80-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="38b80-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38b80-107">特性</span><span class="sxs-lookup"><span data-stu-id="38b80-107">Attributes</span></span>  
  
|<span data-ttu-id="38b80-108">属性</span><span class="sxs-lookup"><span data-stu-id="38b80-108">Attribute</span></span>|<span data-ttu-id="38b80-109">描述</span><span class="sxs-lookup"><span data-stu-id="38b80-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38b80-110">name</span><span class="sxs-lookup"><span data-stu-id="38b80-110">**name**</span></span>|<span data-ttu-id="38b80-111">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="38b80-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="38b80-112">指定密码类实现的算法的友好名称。</span><span class="sxs-lookup"><span data-stu-id="38b80-112">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="38b80-113">**class**</span><span class="sxs-lookup"><span data-stu-id="38b80-113">**class**</span></span>|<span data-ttu-id="38b80-114">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="38b80-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="38b80-115">指定元素中 **name** 属性的值 [\<cryptoClass>](cryptoclass-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="38b80-115">Specifies the value for the **name** attribute in the [\<cryptoClass>](cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38b80-116">子元素</span><span class="sxs-lookup"><span data-stu-id="38b80-116">Child Elements</span></span>  

 <span data-ttu-id="38b80-117">无。</span><span class="sxs-lookup"><span data-stu-id="38b80-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38b80-118">父元素</span><span class="sxs-lookup"><span data-stu-id="38b80-118">Parent Elements</span></span>  
  
|<span data-ttu-id="38b80-119">元素</span><span class="sxs-lookup"><span data-stu-id="38b80-119">Element</span></span>|<span data-ttu-id="38b80-120">描述</span><span class="sxs-lookup"><span data-stu-id="38b80-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="38b80-121">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="38b80-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="38b80-122">为 ASP.NET 配置节指定根元素。</span><span class="sxs-lookup"><span data-stu-id="38b80-122">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38b80-123">备注</span><span class="sxs-lookup"><span data-stu-id="38b80-123">Remarks</span></span>  

 <span data-ttu-id="38b80-124">**Name**属性可以是在命名空间中找到的某个抽象类的名称 <xref:System.Security.Cryptography> 。</span><span class="sxs-lookup"><span data-stu-id="38b80-124">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="38b80-125">对抽象加密类调用 **Create** 方法时，会将抽象类名称传递给 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="38b80-125">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="38b80-126">**Cryptoconfig.createfromname** 返回 **类** 特性指示的类型的实例。</span><span class="sxs-lookup"><span data-stu-id="38b80-126">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="38b80-127">如果 **name** 属性是一个短名称，例如 RSA，则可以在调用 **cryptoconfig.createfromname** 方法时使用该名称。</span><span class="sxs-lookup"><span data-stu-id="38b80-127">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38b80-128">示例</span><span class="sxs-lookup"><span data-stu-id="38b80-128">Example</span></span>  

 <span data-ttu-id="38b80-129">下面的示例演示如何使用 **\<nameEntry>** 元素来引用加密类并配置运行时。</span><span class="sxs-lookup"><span data-stu-id="38b80-129">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="38b80-130">然后，你可以将字符串 "RSA" 传递给 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> 方法，并使用 <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> 方法返回 `MyCryptoRSAClass` 对象。</span><span class="sxs-lookup"><span data-stu-id="38b80-130">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="38b80-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="38b80-131">See also</span></span>

- [<span data-ttu-id="38b80-132">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="38b80-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="38b80-133">加密设置架构</span><span class="sxs-lookup"><span data-stu-id="38b80-133">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="38b80-134">加密服务</span><span class="sxs-lookup"><span data-stu-id="38b80-134">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="38b80-135">配置加密类</span><span class="sxs-lookup"><span data-stu-id="38b80-135">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
