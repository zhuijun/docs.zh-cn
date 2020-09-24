---
title: schemeSettings 的 <remove> 元素（Uri 设置）
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: 018a08693a39bb297bdaa468ba59d4bf097f6922
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151384"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="244c3-102">schemeSettings 的 \<remove> 元素（Uri 设置）</span><span class="sxs-lookup"><span data-stu-id="244c3-102">\<remove> Element for schemeSettings (Uri Settings)</span></span>

<span data-ttu-id="244c3-103">删除方案名称的方案设置。</span><span class="sxs-lookup"><span data-stu-id="244c3-103">Removes a scheme setting for a scheme name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="244c3-104">语法</span><span class="sxs-lookup"><span data-stu-id="244c3-104">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="244c3-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="244c3-105">Attributes and Elements</span></span>  

 <span data-ttu-id="244c3-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="244c3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="244c3-107">特性</span><span class="sxs-lookup"><span data-stu-id="244c3-107">Attributes</span></span>  
  
|<span data-ttu-id="244c3-108">属性</span><span class="sxs-lookup"><span data-stu-id="244c3-108">Attribute</span></span>|<span data-ttu-id="244c3-109">说明</span><span class="sxs-lookup"><span data-stu-id="244c3-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="244c3-110">name</span><span class="sxs-lookup"><span data-stu-id="244c3-110">name</span></span>|<span data-ttu-id="244c3-111">应用此设置的方案名称。</span><span class="sxs-lookup"><span data-stu-id="244c3-111">The scheme name for which this setting applies.</span></span> <span data-ttu-id="244c3-112">唯一受支持的值为 name = "http" 和 name = "https"。</span><span class="sxs-lookup"><span data-stu-id="244c3-112">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="244c3-113">子元素</span><span class="sxs-lookup"><span data-stu-id="244c3-113">Child Elements</span></span>  

 <span data-ttu-id="244c3-114">无。</span><span class="sxs-lookup"><span data-stu-id="244c3-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="244c3-115">父元素</span><span class="sxs-lookup"><span data-stu-id="244c3-115">Parent Elements</span></span>  
  
|<span data-ttu-id="244c3-116">元素</span><span class="sxs-lookup"><span data-stu-id="244c3-116">Element</span></span>|<span data-ttu-id="244c3-117">描述</span><span class="sxs-lookup"><span data-stu-id="244c3-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="244c3-118">\<schemeSettings> 元素 (Uri 设置) </span><span class="sxs-lookup"><span data-stu-id="244c3-118">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="244c3-119">指定如何分析特定方案的 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="244c3-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="244c3-120">备注</span><span class="sxs-lookup"><span data-stu-id="244c3-120">Remarks</span></span>  

 <span data-ttu-id="244c3-121">默认情况下，在 <xref:System.Uri?displayProperty=nameWithType> 执行路径压缩之前，类会取消转义编码的路径分隔符。</span><span class="sxs-lookup"><span data-stu-id="244c3-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="244c3-122">这是作为一种安全机制实现的，针对以下攻击：</span><span class="sxs-lookup"><span data-stu-id="244c3-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="244c3-123">如果将此 URI 向下传递到模块，而不是正确处理百分号编码字符，则可能会导致服务器执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="244c3-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="244c3-124">出于此原因， <xref:System.Uri?displayProperty=nameWithType> 类首先取消转义路径分隔符，然后应用路径压缩。</span><span class="sxs-lookup"><span data-stu-id="244c3-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="244c3-125">将上述恶意 URL 传递到 <xref:System.Uri?displayProperty=nameWithType> 类构造函数的结果将生成以下 URI：</span><span class="sxs-lookup"><span data-stu-id="244c3-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="244c3-126">使用特定方案的 schemeSettings 配置选项，可以将此默认行为修改为不取消转义百分号编码的路径分隔符。</span><span class="sxs-lookup"><span data-stu-id="244c3-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="244c3-127">配置文件</span><span class="sxs-lookup"><span data-stu-id="244c3-127">Configuration Files</span></span>  

 <span data-ttu-id="244c3-128">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="244c3-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="244c3-129">示例</span><span class="sxs-lookup"><span data-stu-id="244c3-129">Example</span></span>  

 <span data-ttu-id="244c3-130">下面的示例演示了类使用的配置 <xref:System.Uri> ，该配置删除了 http 方案的任何方案设置。</span><span class="sxs-lookup"><span data-stu-id="244c3-130">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="244c3-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="244c3-131">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="244c3-132">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="244c3-132">Network Settings Schema</span></span>](index.md)
