---
title: <uri> 元素（Uri 设置）
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: 2f22d70407d10dbb38f0cb8d3a8ac74ff3fe8763
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190197"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="66200-102">\<uri> 元素（Uri 设置）</span><span class="sxs-lookup"><span data-stu-id="66200-102">\<uri> Element (Uri Settings)</span></span>

<span data-ttu-id="66200-103">包含指定 .NET Framework 如何处理使用统一资源标识符 (Uri) 表示的 web 地址的设置。</span><span class="sxs-lookup"><span data-stu-id="66200-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<uri>**  
  
## <a name="syntax"></a><span data-ttu-id="66200-104">语法</span><span class="sxs-lookup"><span data-stu-id="66200-104">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66200-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="66200-105">Attributes and Elements</span></span>  

 <span data-ttu-id="66200-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="66200-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66200-107">特性</span><span class="sxs-lookup"><span data-stu-id="66200-107">Attributes</span></span>  

 <span data-ttu-id="66200-108">无。</span><span class="sxs-lookup"><span data-stu-id="66200-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="66200-109">子元素</span><span class="sxs-lookup"><span data-stu-id="66200-109">Child Elements</span></span>  
  
|<span data-ttu-id="66200-110">**元素**</span><span class="sxs-lookup"><span data-stu-id="66200-110">**Element**</span></span>|<span data-ttu-id="66200-111">**说明**</span><span class="sxs-lookup"><span data-stu-id="66200-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="66200-112">idn</span><span class="sxs-lookup"><span data-stu-id="66200-112">idn</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="66200-113">指定是否对域名应用国际化域名 (IDN) 分析。</span><span class="sxs-lookup"><span data-stu-id="66200-113">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="66200-114">Iriparsing></span><span class="sxs-lookup"><span data-stu-id="66200-114">iriParsing</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="66200-115">指定是否将国际化资源标识符 (IRI) 分析应用到 <xref:System.Uri> ，以及是否应该应用 iri 分析规则。</span><span class="sxs-lookup"><span data-stu-id="66200-115">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="66200-116">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="66200-116">schemeSettings</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="66200-117">指定如何分析特定方案的 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="66200-117">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="66200-118">父元素</span><span class="sxs-lookup"><span data-stu-id="66200-118">Parent Elements</span></span>  
  
|<span data-ttu-id="66200-119">**元素**</span><span class="sxs-lookup"><span data-stu-id="66200-119">**Element**</span></span>|<span data-ttu-id="66200-120">**说明**</span><span class="sxs-lookup"><span data-stu-id="66200-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="66200-121">configuration</span><span class="sxs-lookup"><span data-stu-id="66200-121">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="66200-122">包含所有命名空间的设置。</span><span class="sxs-lookup"><span data-stu-id="66200-122">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66200-123">备注</span><span class="sxs-lookup"><span data-stu-id="66200-123">Remarks</span></span>  

 <span data-ttu-id="66200-124">`uri`元素包含 <xref:System.Uri> 由命名空间中的类使用的类的成员设置 <xref:System.Net> 。</span><span class="sxs-lookup"><span data-stu-id="66200-124">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="66200-125">设置配置对 IRI 和 IDN 的支持。</span><span class="sxs-lookup"><span data-stu-id="66200-125">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66200-126">示例</span><span class="sxs-lookup"><span data-stu-id="66200-126">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="66200-127">描述</span><span class="sxs-lookup"><span data-stu-id="66200-127">Description</span></span>  

 <span data-ttu-id="66200-128">下面的示例演示类使用的配置， <xref:System.Uri> 以支持 IRI 分析和 IDN 名称。</span><span class="sxs-lookup"><span data-stu-id="66200-128">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="66200-129">该示例还会清除所有方案设置，然后添加对 http 方案不转义百分号编码路径分隔符的支持。</span><span class="sxs-lookup"><span data-stu-id="66200-129">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="66200-130">代码</span><span class="sxs-lookup"><span data-stu-id="66200-130">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="66200-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="66200-131">See also</span></span>

- [<span data-ttu-id="66200-132">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="66200-132">Network Settings Schema</span></span>](index.md)
