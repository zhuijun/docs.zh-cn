---
title: <legacyCorruptedStateExceptionsPolicy> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
ms.openlocfilehash: d1d29a37999a01f3e370897a1052f4f94435a218
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73116462"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a><span data-ttu-id="641bd-102">\<legacyCorruptedStateExceptionsPolicy> 元素</span><span class="sxs-lookup"><span data-stu-id="641bd-102">\<legacyCorruptedStateExceptionsPolicy> Element</span></span>
<span data-ttu-id="641bd-103">指定公共语言运行时是否允许托管代码捕获访问冲突和其他损坏状态异常。</span><span class="sxs-lookup"><span data-stu-id="641bd-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyCorruptedStateExceptionsPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="641bd-104">语法</span><span class="sxs-lookup"><span data-stu-id="641bd-104">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="641bd-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="641bd-105">Attributes and Elements</span></span>  
 <span data-ttu-id="641bd-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="641bd-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="641bd-107">特性</span><span class="sxs-lookup"><span data-stu-id="641bd-107">Attributes</span></span>  
  
|<span data-ttu-id="641bd-108">属性</span><span class="sxs-lookup"><span data-stu-id="641bd-108">Attribute</span></span>|<span data-ttu-id="641bd-109">说明</span><span class="sxs-lookup"><span data-stu-id="641bd-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="641bd-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="641bd-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="641bd-111">指定应用程序将捕获损坏状态异常故障，例如访问冲突。</span><span class="sxs-lookup"><span data-stu-id="641bd-111">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="641bd-112">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="641bd-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="641bd-113">值</span><span class="sxs-lookup"><span data-stu-id="641bd-113">Value</span></span>|<span data-ttu-id="641bd-114">说明</span><span class="sxs-lookup"><span data-stu-id="641bd-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="641bd-115">应用程序不会捕获损坏状态异常故障，例如访问冲突。</span><span class="sxs-lookup"><span data-stu-id="641bd-115">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="641bd-116">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="641bd-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="641bd-117">应用程序将捕获损坏状态异常故障，例如访问冲突。</span><span class="sxs-lookup"><span data-stu-id="641bd-117">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="641bd-118">子元素</span><span class="sxs-lookup"><span data-stu-id="641bd-118">Child Elements</span></span>  
 <span data-ttu-id="641bd-119">无。</span><span class="sxs-lookup"><span data-stu-id="641bd-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="641bd-120">父元素</span><span class="sxs-lookup"><span data-stu-id="641bd-120">Parent Elements</span></span>  
  
|<span data-ttu-id="641bd-121">元素</span><span class="sxs-lookup"><span data-stu-id="641bd-121">Element</span></span>|<span data-ttu-id="641bd-122">描述</span><span class="sxs-lookup"><span data-stu-id="641bd-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="641bd-123">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="641bd-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="641bd-124">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="641bd-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="641bd-125">注解</span><span class="sxs-lookup"><span data-stu-id="641bd-125">Remarks</span></span>  
 <span data-ttu-id="641bd-126">在 .NET Framework 版本3.5 及更早版本中，公共语言运行时允许托管代码捕获由损坏的进程状态引发的异常。</span><span class="sxs-lookup"><span data-stu-id="641bd-126">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="641bd-127">访问冲突就是这种类型的异常的一个示例。</span><span class="sxs-lookup"><span data-stu-id="641bd-127">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="641bd-128">从 .NET Framework 4 开始，托管代码不再在块中捕获这些类型的异常 `catch` 。</span><span class="sxs-lookup"><span data-stu-id="641bd-128">Starting with the .NET Framework 4, managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="641bd-129">不过，你可以通过两种方式重写此更改并保持对损坏状态异常的处理：</span><span class="sxs-lookup"><span data-stu-id="641bd-129">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
- <span data-ttu-id="641bd-130">将 `<legacyCorruptedStateExceptionsPolicy>` 元素的 `enabled` 属性设置为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="641bd-130">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="641bd-131">此配置设置将应用 processwide 并影响所有方法。</span><span class="sxs-lookup"><span data-stu-id="641bd-131">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="641bd-132">-或-</span><span class="sxs-lookup"><span data-stu-id="641bd-132">-or-</span></span>  
  
- <span data-ttu-id="641bd-133">将特性应用于 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> 包含异常块的方法 `catch` 。</span><span class="sxs-lookup"><span data-stu-id="641bd-133">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="641bd-134">此配置元素仅在 .NET Framework 4 及更高版本中可用。</span><span class="sxs-lookup"><span data-stu-id="641bd-134">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="641bd-135">示例</span><span class="sxs-lookup"><span data-stu-id="641bd-135">Example</span></span>  
 <span data-ttu-id="641bd-136">下面的示例演示如何指定应用程序应恢复到 .NET Framework 4 之前的行为，并捕获所有损坏状态异常错误。</span><span class="sxs-lookup"><span data-stu-id="641bd-136">The following example shows how to specify that the application should revert to the behavior before the .NET Framework 4, and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="641bd-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="641bd-137">See also</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [<span data-ttu-id="641bd-138">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="641bd-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="641bd-139">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="641bd-139">Configuration File Schema</span></span>](../index.md)
