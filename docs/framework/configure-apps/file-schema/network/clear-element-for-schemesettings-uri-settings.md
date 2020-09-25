---
title: schemeSettings 的 <clear> 元素（Uri 设置）
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 17069a56a8647871e98d70826a97a8fe407a0887
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205056"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a><span data-ttu-id="34d8b-102">schemeSettings 的 \<clear> 元素（Uri 设置）</span><span class="sxs-lookup"><span data-stu-id="34d8b-102">\<clear> Element for schemeSettings (Uri Settings)</span></span>

<span data-ttu-id="34d8b-103">清除所有现有方案设置。</span><span class="sxs-lookup"><span data-stu-id="34d8b-103">Clears all existing scheme settings.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="34d8b-104">语法</span><span class="sxs-lookup"><span data-stu-id="34d8b-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34d8b-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="34d8b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="34d8b-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="34d8b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34d8b-107">特性</span><span class="sxs-lookup"><span data-stu-id="34d8b-107">Attributes</span></span>  

 <span data-ttu-id="34d8b-108">无。</span><span class="sxs-lookup"><span data-stu-id="34d8b-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="34d8b-109">子元素</span><span class="sxs-lookup"><span data-stu-id="34d8b-109">Child Elements</span></span>  

 <span data-ttu-id="34d8b-110">无。</span><span class="sxs-lookup"><span data-stu-id="34d8b-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="34d8b-111">父元素</span><span class="sxs-lookup"><span data-stu-id="34d8b-111">Parent Elements</span></span>  
  
|<span data-ttu-id="34d8b-112">元素</span><span class="sxs-lookup"><span data-stu-id="34d8b-112">Element</span></span>|<span data-ttu-id="34d8b-113">描述</span><span class="sxs-lookup"><span data-stu-id="34d8b-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34d8b-114">\<schemeSettings> 元素 (Uri 设置) </span><span class="sxs-lookup"><span data-stu-id="34d8b-114">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="34d8b-115">指定如何分析特定方案的 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="34d8b-115">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34d8b-116">备注</span><span class="sxs-lookup"><span data-stu-id="34d8b-116">Remarks</span></span>  

 <span data-ttu-id="34d8b-117">默认情况下，在 <xref:System.Uri?displayProperty=nameWithType> 执行路径压缩之前，类会取消转义编码的路径分隔符。</span><span class="sxs-lookup"><span data-stu-id="34d8b-117">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="34d8b-118">这是作为一种安全机制实现的，针对以下攻击：</span><span class="sxs-lookup"><span data-stu-id="34d8b-118">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="34d8b-119">如果将此 URI 向下传递到模块，而不是正确处理百分号编码字符，则可能会导致服务器执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="34d8b-119">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="34d8b-120">出于此原因， <xref:System.Uri?displayProperty=nameWithType> 类首先取消转义路径分隔符，然后应用路径压缩。</span><span class="sxs-lookup"><span data-stu-id="34d8b-120">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="34d8b-121">将上述恶意 URL 传递到 <xref:System.Uri?displayProperty=nameWithType> 类构造函数的结果将生成以下 URI：</span><span class="sxs-lookup"><span data-stu-id="34d8b-121">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="34d8b-122">使用特定方案的 schemeSettings 配置选项，可以将此默认行为修改为不取消转义百分号编码的路径分隔符。</span><span class="sxs-lookup"><span data-stu-id="34d8b-122">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="34d8b-123">配置文件</span><span class="sxs-lookup"><span data-stu-id="34d8b-123">Configuration Files</span></span>  

 <span data-ttu-id="34d8b-124">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="34d8b-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="34d8b-125">示例</span><span class="sxs-lookup"><span data-stu-id="34d8b-125">Example</span></span>  

 <span data-ttu-id="34d8b-126">下面的示例演示了类使用的配置 <xref:System.Uri> ，该配置将清除所有方案设置，并添加了对不转义 http 方案的百分号编码路径分隔符的支持。</span><span class="sxs-lookup"><span data-stu-id="34d8b-126">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="34d8b-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="34d8b-127">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="34d8b-128">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="34d8b-128">Network Settings Schema</span></span>](index.md)
