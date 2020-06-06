---
title: <uri> 元素（Uri 设置）
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: a492baf9951466383ca0277a2927b8554e5bb332
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697439"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="7ecea-102">\<uri> 元素（Uri 设置）</span><span class="sxs-lookup"><span data-stu-id="7ecea-102">\<uri> Element (Uri Settings)</span></span>
<span data-ttu-id="7ecea-103">包含指定 .NET Framework 如何处理使用统一资源标识符（Uri）表示的 web 地址的设置。</span><span class="sxs-lookup"><span data-stu-id="7ecea-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<uri>**  
  
## <a name="syntax"></a><span data-ttu-id="7ecea-104">语法</span><span class="sxs-lookup"><span data-stu-id="7ecea-104">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ecea-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="7ecea-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7ecea-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7ecea-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ecea-107">特性</span><span class="sxs-lookup"><span data-stu-id="7ecea-107">Attributes</span></span>  
 <span data-ttu-id="7ecea-108">无。</span><span class="sxs-lookup"><span data-stu-id="7ecea-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7ecea-109">子元素</span><span class="sxs-lookup"><span data-stu-id="7ecea-109">Child Elements</span></span>  
  
|<span data-ttu-id="7ecea-110">**元素**</span><span class="sxs-lookup"><span data-stu-id="7ecea-110">**Element**</span></span>|<span data-ttu-id="7ecea-111">**描述**</span><span class="sxs-lookup"><span data-stu-id="7ecea-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7ecea-112">idn</span><span class="sxs-lookup"><span data-stu-id="7ecea-112">idn</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="7ecea-113">指定是否对域名应用国际化域名 (IDN) 分析。</span><span class="sxs-lookup"><span data-stu-id="7ecea-113">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="7ecea-114">Iriparsing></span><span class="sxs-lookup"><span data-stu-id="7ecea-114">iriParsing</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="7ecea-115">指定是否将国际化资源标识符（IRI）分析应用到 <xref:System.Uri> ，以及是否应该应用 IRI 分析规则。</span><span class="sxs-lookup"><span data-stu-id="7ecea-115">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="7ecea-116">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="7ecea-116">schemeSettings</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="7ecea-117">指定如何分析特定方案的 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="7ecea-117">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7ecea-118">父元素</span><span class="sxs-lookup"><span data-stu-id="7ecea-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7ecea-119">**元素**</span><span class="sxs-lookup"><span data-stu-id="7ecea-119">**Element**</span></span>|<span data-ttu-id="7ecea-120">**描述**</span><span class="sxs-lookup"><span data-stu-id="7ecea-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7ecea-121">configuration</span><span class="sxs-lookup"><span data-stu-id="7ecea-121">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="7ecea-122">包含所有命名空间的设置。</span><span class="sxs-lookup"><span data-stu-id="7ecea-122">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ecea-123">注解</span><span class="sxs-lookup"><span data-stu-id="7ecea-123">Remarks</span></span>  
 <span data-ttu-id="7ecea-124">`uri`元素包含 <xref:System.Uri> 由命名空间中的类使用的类的成员设置 <xref:System.Net> 。</span><span class="sxs-lookup"><span data-stu-id="7ecea-124">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="7ecea-125">设置配置对 IRI 和 IDN 的支持。</span><span class="sxs-lookup"><span data-stu-id="7ecea-125">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ecea-126">示例</span><span class="sxs-lookup"><span data-stu-id="7ecea-126">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="7ecea-127">说明</span><span class="sxs-lookup"><span data-stu-id="7ecea-127">Description</span></span>  
 <span data-ttu-id="7ecea-128">下面的示例演示类使用的配置， <xref:System.Uri> 以支持 IRI 分析和 IDN 名称。</span><span class="sxs-lookup"><span data-stu-id="7ecea-128">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="7ecea-129">该示例还会清除所有方案设置，然后添加对 http 方案不转义百分号编码路径分隔符的支持。</span><span class="sxs-lookup"><span data-stu-id="7ecea-129">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7ecea-130">代码</span><span class="sxs-lookup"><span data-stu-id="7ecea-130">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7ecea-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7ecea-131">See also</span></span>

- [<span data-ttu-id="7ecea-132">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="7ecea-132">Network Settings Schema</span></span>](index.md)
