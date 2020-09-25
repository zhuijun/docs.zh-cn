---
title: <oidEntry> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
ms.openlocfilehash: 2207c934f5864890d9b7a5e22c43a1d53e29aaa5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91187103"
---
# <a name="oidentry-element"></a><span data-ttu-id="cf66b-102">\<oidEntry> 元素</span><span class="sxs-lookup"><span data-stu-id="cf66b-102">\<oidEntry> Element</span></span>

<span data-ttu-id="cf66b-103">将 ASN.1 对象标识符 (OID) 映射到友好名称。</span><span class="sxs-lookup"><span data-stu-id="cf66b-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidEntry>**

## <a name="syntax"></a><span data-ttu-id="cf66b-104">语法</span><span class="sxs-lookup"><span data-stu-id="cf66b-104">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf66b-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="cf66b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="cf66b-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cf66b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf66b-107">特性</span><span class="sxs-lookup"><span data-stu-id="cf66b-107">Attributes</span></span>  
  
|<span data-ttu-id="cf66b-108">属性</span><span class="sxs-lookup"><span data-stu-id="cf66b-108">Attribute</span></span>|<span data-ttu-id="cf66b-109">描述</span><span class="sxs-lookup"><span data-stu-id="cf66b-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cf66b-110">**OID**</span><span class="sxs-lookup"><span data-stu-id="cf66b-110">**OID**</span></span>|<span data-ttu-id="cf66b-111">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="cf66b-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="cf66b-112">指定与您的类实现的算法相对应的第1个 OID。</span><span class="sxs-lookup"><span data-stu-id="cf66b-112">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="cf66b-113">name</span><span class="sxs-lookup"><span data-stu-id="cf66b-113">**name**</span></span>|<span data-ttu-id="cf66b-114">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="cf66b-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="cf66b-115">指定标记中 **name** 属性的值 [\<nameEntry>](nameentry-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="cf66b-115">Specifies the value for the **name** attribute in the [\<nameEntry>](nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf66b-116">子元素</span><span class="sxs-lookup"><span data-stu-id="cf66b-116">Child Elements</span></span>  

 <span data-ttu-id="cf66b-117">无。</span><span class="sxs-lookup"><span data-stu-id="cf66b-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cf66b-118">父元素</span><span class="sxs-lookup"><span data-stu-id="cf66b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="cf66b-119">元素</span><span class="sxs-lookup"><span data-stu-id="cf66b-119">Element</span></span>|<span data-ttu-id="cf66b-120">描述</span><span class="sxs-lookup"><span data-stu-id="cf66b-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cf66b-121">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="cf66b-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="cf66b-122">包含加密设置。</span><span class="sxs-lookup"><span data-stu-id="cf66b-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="cf66b-123">包含 `cryptographySettings` 元素。</span><span class="sxs-lookup"><span data-stu-id="cf66b-123">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="cf66b-124">包含) 映射到类 (OID 对象标识符。</span><span class="sxs-lookup"><span data-stu-id="cf66b-124">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf66b-125">备注</span><span class="sxs-lookup"><span data-stu-id="cf66b-125">Remarks</span></span>  

 <span data-ttu-id="cf66b-126">ASN. 1 对象标识符以某些加密格式标识算法。</span><span class="sxs-lookup"><span data-stu-id="cf66b-126">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="cf66b-127">将对象标识符映射到要标识的算法的友好名称。</span><span class="sxs-lookup"><span data-stu-id="cf66b-127">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf66b-128">示例</span><span class="sxs-lookup"><span data-stu-id="cf66b-128">Example</span></span>  

 <span data-ttu-id="cf66b-129">下面的示例演示如何使用元素将 **\<oidEntry>** RIPEMD-160 哈希算法的对象标识符映射到该哈希算法的实现。</span><span class="sxs-lookup"><span data-stu-id="cf66b-129">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf66b-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="cf66b-130">See also</span></span>

- [<span data-ttu-id="cf66b-131">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="cf66b-131">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="cf66b-132">加密设置架构</span><span class="sxs-lookup"><span data-stu-id="cf66b-132">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cf66b-133">加密服务</span><span class="sxs-lookup"><span data-stu-id="cf66b-133">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="cf66b-134">配置加密类</span><span class="sxs-lookup"><span data-stu-id="cf66b-134">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="cf66b-135">将对象标识符映射到加密算法</span><span class="sxs-lookup"><span data-stu-id="cf66b-135">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
