---
title: <iriParsing> 元素（Uri 设置）
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: ec2610e47957d5560bc7f51e0641afc9ba60c814
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158885"
---
# <a name="iriparsing-element-uri-settings"></a><span data-ttu-id="cd036-102">\<iriParsing> 元素（Uri 设置）</span><span class="sxs-lookup"><span data-stu-id="cd036-102">\<iriParsing> Element (Uri Settings)</span></span>

<span data-ttu-id="cd036-103">指定是否对 <xref:System.Uri> 应用国际资源标识符 (IRI) 分析以及是否应该应用 IRI 分析规则。</span><span class="sxs-lookup"><span data-stu-id="cd036-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<iriParsing>**  
  
## <a name="syntax"></a><span data-ttu-id="cd036-104">语法</span><span class="sxs-lookup"><span data-stu-id="cd036-104">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd036-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="cd036-105">Attributes and Elements</span></span>  

 <span data-ttu-id="cd036-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cd036-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd036-107">特性</span><span class="sxs-lookup"><span data-stu-id="cd036-107">Attributes</span></span>  
  
|<span data-ttu-id="cd036-108">**元素**</span><span class="sxs-lookup"><span data-stu-id="cd036-108">**Element**</span></span>|<span data-ttu-id="cd036-109">**说明**</span><span class="sxs-lookup"><span data-stu-id="cd036-109">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="cd036-110">指定是否启用 IRI 分析。</span><span class="sxs-lookup"><span data-stu-id="cd036-110">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="cd036-111">默认值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="cd036-111">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd036-112">子元素</span><span class="sxs-lookup"><span data-stu-id="cd036-112">Child Elements</span></span>  

 <span data-ttu-id="cd036-113">无</span><span class="sxs-lookup"><span data-stu-id="cd036-113">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cd036-114">父元素</span><span class="sxs-lookup"><span data-stu-id="cd036-114">Parent Elements</span></span>  
  
|<span data-ttu-id="cd036-115">**元素**</span><span class="sxs-lookup"><span data-stu-id="cd036-115">**Element**</span></span>|<span data-ttu-id="cd036-116">**说明**</span><span class="sxs-lookup"><span data-stu-id="cd036-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="cd036-117">uri</span><span class="sxs-lookup"><span data-stu-id="cd036-117">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="cd036-118">包含指定 .NET Framework 如何处理使用统一资源标识符 (Uri) 表示的 web 地址的设置。</span><span class="sxs-lookup"><span data-stu-id="cd036-118">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd036-119">备注</span><span class="sxs-lookup"><span data-stu-id="cd036-119">Remarks</span></span>  

 <span data-ttu-id="cd036-120">已 <xref:System.Uri> 在 .NET Framework 3.5 中扩展了现有的类。</span><span class="sxs-lookup"><span data-stu-id="cd036-120">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="cd036-121">3.0 SP1 和 2.0 SP1， (IRI) 和国际化域名 (IDN) 提供对国际资源标识符的支持。</span><span class="sxs-lookup"><span data-stu-id="cd036-121">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="cd036-122">当前用户将看不到 .NET Framework 2.0 行为中的任何更改，除非它们专门启用 IRI 和 IDN 支持。</span><span class="sxs-lookup"><span data-stu-id="cd036-122">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="cd036-123">这确保了 NET Framework 以前版本的应用程序兼容性。</span><span class="sxs-lookup"><span data-stu-id="cd036-123">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="cd036-124">若要启用对 IRI 的支持，需要以下两项更改：</span><span class="sxs-lookup"><span data-stu-id="cd036-124">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="cd036-125">将以下行添加到 .NET Framework 2.0 目录下的 machine.config 文件</span><span class="sxs-lookup"><span data-stu-id="cd036-125">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="cd036-126">指定是否应该应用 IRI 分析规则。</span><span class="sxs-lookup"><span data-stu-id="cd036-126">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="cd036-127">这可以在 machine.config 或应用配置文件中完成。</span><span class="sxs-lookup"><span data-stu-id="cd036-127">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="cd036-128">启用 IRI 分析 (Iriparsing> enabled = `true`) 将根据 RFC 3987 中的最新 IRI 规则执行规范化和字符检查。</span><span class="sxs-lookup"><span data-stu-id="cd036-128">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="cd036-129">默认值为 `false` ，将根据 rfc 2396 和 rfc 3986 (为 IPv6 文本) 执行规范化和字符检查。</span><span class="sxs-lookup"><span data-stu-id="cd036-129">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="cd036-130">配置文件</span><span class="sxs-lookup"><span data-stu-id="cd036-130">Configuration Files</span></span>  

 <span data-ttu-id="cd036-131">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="cd036-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd036-132">示例</span><span class="sxs-lookup"><span data-stu-id="cd036-132">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="cd036-133">描述</span><span class="sxs-lookup"><span data-stu-id="cd036-133">Description</span></span>  

 <span data-ttu-id="cd036-134">下面的示例演示类使用的配置， <xref:System.Uri> 以支持 IRI 分析和 IDN 名称。</span><span class="sxs-lookup"><span data-stu-id="cd036-134">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="cd036-135">代码</span><span class="sxs-lookup"><span data-stu-id="cd036-135">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd036-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="cd036-136">See also</span></span>

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="cd036-137">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="cd036-137">Network Settings Schema</span></span>](index.md)
