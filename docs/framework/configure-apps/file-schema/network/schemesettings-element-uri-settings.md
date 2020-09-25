---
title: <schemeSettings> 元素（Uri 设置）
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: 5a146b854239fd516125e66e05312e27b90c73ec
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91187012"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="5f21a-102">\<schemeSettings> 元素（Uri 设置）</span><span class="sxs-lookup"><span data-stu-id="5f21a-102">\<schemeSettings> Element (Uri Settings)</span></span>

<span data-ttu-id="5f21a-103">指定如何分析特定方案的 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="5f21a-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<schemeSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="5f21a-104">语法</span><span class="sxs-lookup"><span data-stu-id="5f21a-104">Syntax</span></span>  
  
```xml  
<schemeSettings>
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f21a-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="5f21a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="5f21a-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5f21a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f21a-107">特性</span><span class="sxs-lookup"><span data-stu-id="5f21a-107">Attributes</span></span>  

 <span data-ttu-id="5f21a-108">无</span><span class="sxs-lookup"><span data-stu-id="5f21a-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5f21a-109">子元素</span><span class="sxs-lookup"><span data-stu-id="5f21a-109">Child Elements</span></span>  
  
|<span data-ttu-id="5f21a-110">**元素**</span><span class="sxs-lookup"><span data-stu-id="5f21a-110">**Element**</span></span>|<span data-ttu-id="5f21a-111">**说明**</span><span class="sxs-lookup"><span data-stu-id="5f21a-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5f21a-112">add</span><span class="sxs-lookup"><span data-stu-id="5f21a-112">add</span></span>](add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="5f21a-113">为方案名称添加方案设置。</span><span class="sxs-lookup"><span data-stu-id="5f21a-113">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="5f21a-114">clear</span><span class="sxs-lookup"><span data-stu-id="5f21a-114">clear</span></span>](clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="5f21a-115">清除所有现有方案设置。</span><span class="sxs-lookup"><span data-stu-id="5f21a-115">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="5f21a-116">remove</span><span class="sxs-lookup"><span data-stu-id="5f21a-116">remove</span></span>](remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="5f21a-117">删除方案名称的方案设置。</span><span class="sxs-lookup"><span data-stu-id="5f21a-117">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5f21a-118">父元素</span><span class="sxs-lookup"><span data-stu-id="5f21a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5f21a-119">**元素**</span><span class="sxs-lookup"><span data-stu-id="5f21a-119">**Element**</span></span>|<span data-ttu-id="5f21a-120">**说明**</span><span class="sxs-lookup"><span data-stu-id="5f21a-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5f21a-121">uri</span><span class="sxs-lookup"><span data-stu-id="5f21a-121">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="5f21a-122">包含指定 .NET Framework 如何处理使用统一资源标识符 (Uri) 表示的 web 地址的设置。</span><span class="sxs-lookup"><span data-stu-id="5f21a-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f21a-123">备注</span><span class="sxs-lookup"><span data-stu-id="5f21a-123">Remarks</span></span>  

 <span data-ttu-id="5f21a-124">默认情况下，在 <xref:System.Uri?displayProperty=nameWithType> 执行路径压缩之前，类会取消转义编码的路径分隔符。</span><span class="sxs-lookup"><span data-stu-id="5f21a-124">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="5f21a-125">这是作为一种安全机制实现的，针对以下攻击：</span><span class="sxs-lookup"><span data-stu-id="5f21a-125">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="5f21a-126">如果将此 URI 向下传递到模块，而不是正确处理百分号编码字符，则可能会导致服务器执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="5f21a-126">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="5f21a-127">出于此原因， <xref:System.Uri?displayProperty=nameWithType> 类首先取消转义路径分隔符，然后应用路径压缩。</span><span class="sxs-lookup"><span data-stu-id="5f21a-127">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="5f21a-128">将上述恶意 URL 传递到 <xref:System.Uri?displayProperty=nameWithType> 类构造函数的结果将生成以下 URI：</span><span class="sxs-lookup"><span data-stu-id="5f21a-128">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="5f21a-129">使用特定方案的 schemeSettings 配置选项，可以将此默认行为修改为不取消转义百分号编码的路径分隔符。</span><span class="sxs-lookup"><span data-stu-id="5f21a-129">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5f21a-130">配置文件</span><span class="sxs-lookup"><span data-stu-id="5f21a-130">Configuration Files</span></span>  

 <span data-ttu-id="5f21a-131">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="5f21a-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f21a-132">示例</span><span class="sxs-lookup"><span data-stu-id="5f21a-132">Example</span></span>  

 <span data-ttu-id="5f21a-133">下面的示例演示类使用的配置 <xref:System.Uri> ，以支持不转义 http 方案的百分号编码的路径分隔符。</span><span class="sxs-lookup"><span data-stu-id="5f21a-133">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="5f21a-134">元素信息</span><span class="sxs-lookup"><span data-stu-id="5f21a-134">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="5f21a-135">命名空间</span><span class="sxs-lookup"><span data-stu-id="5f21a-135">Namespace</span></span>|<span data-ttu-id="5f21a-136">系统</span><span class="sxs-lookup"><span data-stu-id="5f21a-136">System</span></span>|  
|<span data-ttu-id="5f21a-137">架构名称</span><span class="sxs-lookup"><span data-stu-id="5f21a-137">Schema Name</span></span>||  
|<span data-ttu-id="5f21a-138">验证文件</span><span class="sxs-lookup"><span data-stu-id="5f21a-138">Validation File</span></span>||  
|<span data-ttu-id="5f21a-139">可以为空</span><span class="sxs-lookup"><span data-stu-id="5f21a-139">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="5f21a-140">请参阅</span><span class="sxs-lookup"><span data-stu-id="5f21a-140">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="5f21a-141">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="5f21a-141">Network Settings Schema</span></span>](index.md)
