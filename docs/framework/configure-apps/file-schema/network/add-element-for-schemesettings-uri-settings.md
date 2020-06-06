---
title: schemeSettings 的 <add> 元素（Uri 设置）
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: ed40098e8d4c2d1298771e67a618b8d04f59c912
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087716"
---
# <a name="add-element-for-schemesettings-uri-settings"></a><span data-ttu-id="fd9f8-102">schemeSettings 的 \<add> 元素（Uri 设置）</span><span class="sxs-lookup"><span data-stu-id="fd9f8-102">\<add> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="fd9f8-103">为方案名称添加方案设置。</span><span class="sxs-lookup"><span data-stu-id="fd9f8-103">Adds a scheme setting for a scheme name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="fd9f8-104">语法</span><span class="sxs-lookup"><span data-stu-id="fd9f8-104">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd9f8-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="fd9f8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="fd9f8-106">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fd9f8-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd9f8-107">特性</span><span class="sxs-lookup"><span data-stu-id="fd9f8-107">Attributes</span></span>  
  
|<span data-ttu-id="fd9f8-108">属性</span><span class="sxs-lookup"><span data-stu-id="fd9f8-108">Attribute</span></span>|<span data-ttu-id="fd9f8-109">说明</span><span class="sxs-lookup"><span data-stu-id="fd9f8-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fd9f8-110">name</span><span class="sxs-lookup"><span data-stu-id="fd9f8-110">name</span></span>|<span data-ttu-id="fd9f8-111">应用此设置的方案名称。</span><span class="sxs-lookup"><span data-stu-id="fd9f8-111">The scheme name for which this setting applies.</span></span> <span data-ttu-id="fd9f8-112">唯一受支持的值为 name = "http" 和 name = "https"。</span><span class="sxs-lookup"><span data-stu-id="fd9f8-112">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="fd9f8-113">{Attribute name}Attribute</span><span class="sxs-lookup"><span data-stu-id="fd9f8-113">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="fd9f8-114">值</span><span class="sxs-lookup"><span data-stu-id="fd9f8-114">Value</span></span>|<span data-ttu-id="fd9f8-115">说明</span><span class="sxs-lookup"><span data-stu-id="fd9f8-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fd9f8-116">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="fd9f8-116">genericUriParserOptions</span></span>|<span data-ttu-id="fd9f8-117">此方案的分析器选项。</span><span class="sxs-lookup"><span data-stu-id="fd9f8-117">The parser options for this scheme.</span></span> <span data-ttu-id="fd9f8-118">唯一受支持的值为 genericUriParserOptions = "DontUnescapePathDotsAndSlashes"。</span><span class="sxs-lookup"><span data-stu-id="fd9f8-118">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd9f8-119">子元素</span><span class="sxs-lookup"><span data-stu-id="fd9f8-119">Child Elements</span></span>  
 <span data-ttu-id="fd9f8-120">无</span><span class="sxs-lookup"><span data-stu-id="fd9f8-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd9f8-121">父元素</span><span class="sxs-lookup"><span data-stu-id="fd9f8-121">Parent Elements</span></span>  
  
|<span data-ttu-id="fd9f8-122">元素</span><span class="sxs-lookup"><span data-stu-id="fd9f8-122">Element</span></span>|<span data-ttu-id="fd9f8-123">描述</span><span class="sxs-lookup"><span data-stu-id="fd9f8-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd9f8-124">\<schemeSettings>元素（Uri 设置）</span><span class="sxs-lookup"><span data-stu-id="fd9f8-124">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="fd9f8-125">指定如何分析特定方案的 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="fd9f8-125">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd9f8-126">注解</span><span class="sxs-lookup"><span data-stu-id="fd9f8-126">Remarks</span></span>  
 <span data-ttu-id="fd9f8-127">默认情况下，在 <xref:System.Uri?displayProperty=nameWithType> 执行路径压缩之前，类会取消转义编码的路径分隔符。</span><span class="sxs-lookup"><span data-stu-id="fd9f8-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="fd9f8-128">这是作为一种安全机制实现的，针对以下攻击：</span><span class="sxs-lookup"><span data-stu-id="fd9f8-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="fd9f8-129">如果将此 URI 向下传递到模块，而不是正确处理百分号编码字符，则可能会导致服务器执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="fd9f8-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="fd9f8-130">出于此原因， <xref:System.Uri?displayProperty=nameWithType> 类首先取消转义路径分隔符，然后应用路径压缩。</span><span class="sxs-lookup"><span data-stu-id="fd9f8-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="fd9f8-131">将上述恶意 URL 传递到 <xref:System.Uri?displayProperty=nameWithType> 类构造函数的结果将生成以下 URI：</span><span class="sxs-lookup"><span data-stu-id="fd9f8-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="fd9f8-132">使用特定方案的 schemeSettings 配置选项，可以将此默认行为修改为不取消转义百分号编码的路径分隔符。</span><span class="sxs-lookup"><span data-stu-id="fd9f8-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="fd9f8-133">配置文件</span><span class="sxs-lookup"><span data-stu-id="fd9f8-133">Configuration Files</span></span>  
 <span data-ttu-id="fd9f8-134">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="fd9f8-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd9f8-135">示例</span><span class="sxs-lookup"><span data-stu-id="fd9f8-135">Example</span></span>  
 <span data-ttu-id="fd9f8-136">下面的示例演示类使用的配置 <xref:System.Uri> ，以支持不转义 http 方案的百分号编码的路径分隔符。</span><span class="sxs-lookup"><span data-stu-id="fd9f8-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd9f8-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fd9f8-137">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="fd9f8-138">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="fd9f8-138">Network Settings Schema</span></span>](index.md)
