---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: a8ee23ac6facaea18cd7f1820616cb9b16afa336
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189846"
---
# \<customCookieHandler>

<span data-ttu-id="9b771-101">设置自定义 cookie 处理程序类型。</span><span class="sxs-lookup"><span data-stu-id="9b771-101">Sets the custom cookie handler type.</span></span> <span data-ttu-id="9b771-102">仅当 `mode` 元素的属性 `<cookieHandler>` 为 "Custom" 时，此元素才能存在。</span><span class="sxs-lookup"><span data-stu-id="9b771-102">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="9b771-103">自定义类型必须派生自 <xref:System.IdentityModel.Services.CookieHandler> 类。</span><span class="sxs-lookup"><span data-stu-id="9b771-103">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customCookieHandler>**  
  
## <a name="syntax"></a><span data-ttu-id="9b771-104">语法</span><span class="sxs-lookup"><span data-stu-id="9b771-104">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Custom">  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" >  
      </customCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b771-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="9b771-105">Attributes and Elements</span></span>  

 <span data-ttu-id="9b771-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9b771-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b771-107">特性</span><span class="sxs-lookup"><span data-stu-id="9b771-107">Attributes</span></span>  
  
|<span data-ttu-id="9b771-108">属性</span><span class="sxs-lookup"><span data-stu-id="9b771-108">Attribute</span></span>|<span data-ttu-id="9b771-109">说明</span><span class="sxs-lookup"><span data-stu-id="9b771-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9b771-110">type</span><span class="sxs-lookup"><span data-stu-id="9b771-110">type</span></span>|<span data-ttu-id="9b771-111">指定从类派生的自定义类型 <xref:System.IdentityModel.Services.CookieHandler> 。</span><span class="sxs-lookup"><span data-stu-id="9b771-111">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="9b771-112">有关如何指定属性的详细信息 `type` ，请参阅 [自定义类型引用](../windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9b771-112">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9b771-113">子元素</span><span class="sxs-lookup"><span data-stu-id="9b771-113">Child Elements</span></span>  

 <span data-ttu-id="9b771-114">无</span><span class="sxs-lookup"><span data-stu-id="9b771-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9b771-115">父元素</span><span class="sxs-lookup"><span data-stu-id="9b771-115">Parent Elements</span></span>  
  
|<span data-ttu-id="9b771-116">元素</span><span class="sxs-lookup"><span data-stu-id="9b771-116">Element</span></span>|<span data-ttu-id="9b771-117">描述</span><span class="sxs-lookup"><span data-stu-id="9b771-117">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="9b771-118">配置用于 <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> 读取和写入 cookie 的。</span><span class="sxs-lookup"><span data-stu-id="9b771-118">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b771-119">备注</span><span class="sxs-lookup"><span data-stu-id="9b771-119">Remarks</span></span>  

 <span data-ttu-id="9b771-120">如果通过将元素的属性设置为 "Custom" 来指定自定义 cookie 处理程序 `mode` `<cookieHandler>` ，则必须通过包含 `<customCookieHandler>` 引用 cookie 处理程序类型的子元素来指定自定义 cookie 处理程序的类型。</span><span class="sxs-lookup"><span data-stu-id="9b771-120">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="9b771-121">当 `mode` 特性设置为 "分块" 或 "Default" 时，不能指定此元素。</span><span class="sxs-lookup"><span data-stu-id="9b771-121">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="9b771-122">自定义 cookie 处理程序必须派生自 <xref:System.IdentityModel.Services.CookieHandler> 类。</span><span class="sxs-lookup"><span data-stu-id="9b771-122">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="9b771-123">`<customCookieHandler>`元素由 <xref:System.IdentityModel.Configuration.CustomTypeElement> 类表示。</span><span class="sxs-lookup"><span data-stu-id="9b771-123">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b771-124">示例</span><span class="sxs-lookup"><span data-stu-id="9b771-124">Example</span></span>  

 <span data-ttu-id="9b771-125">下面的示例将 SAM 配置为使用类型的自定义 cookie 处理程序 `MyNamespace.MyCustomCookieHandler` 。</span><span class="sxs-lookup"><span data-stu-id="9b771-125">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b771-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="9b771-126">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>
