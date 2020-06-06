---
title: <etwEnable> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
ms.openlocfilehash: 14cea171a4a25e148ea32f75a8ef09b83a4ec8ad
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117396"
---
# <a name="etwenable-element"></a><span data-ttu-id="989c0-102">\<etwEnable> 元素</span><span class="sxs-lookup"><span data-stu-id="989c0-102">\<etwEnable> Element</span></span>
<span data-ttu-id="989c0-103">指定是否为公共语言运行时事件启用 Windows 事件跟踪 (ETW)。</span><span class="sxs-lookup"><span data-stu-id="989c0-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<etwEnabled>**  
  
## <a name="syntax"></a><span data-ttu-id="989c0-104">语法</span><span class="sxs-lookup"><span data-stu-id="989c0-104">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="989c0-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="989c0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="989c0-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="989c0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="989c0-107">特性</span><span class="sxs-lookup"><span data-stu-id="989c0-107">Attributes</span></span>  
  
|<span data-ttu-id="989c0-108">属性</span><span class="sxs-lookup"><span data-stu-id="989c0-108">Attribute</span></span>|<span data-ttu-id="989c0-109">说明</span><span class="sxs-lookup"><span data-stu-id="989c0-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="989c0-110">已启用</span><span class="sxs-lookup"><span data-stu-id="989c0-110">enabled</span></span>|<span data-ttu-id="989c0-111">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="989c0-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="989c0-112">指定是否应启用 ETW。</span><span class="sxs-lookup"><span data-stu-id="989c0-112">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="989c0-113">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="989c0-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="989c0-114">值</span><span class="sxs-lookup"><span data-stu-id="989c0-114">Value</span></span>|<span data-ttu-id="989c0-115">说明</span><span class="sxs-lookup"><span data-stu-id="989c0-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="989c0-116">true</span><span class="sxs-lookup"><span data-stu-id="989c0-116">true</span></span>|<span data-ttu-id="989c0-117">启用 ETW。</span><span class="sxs-lookup"><span data-stu-id="989c0-117">Enable ETW.</span></span> <span data-ttu-id="989c0-118">这是从 Windows Vista 和 Windows Server 2008 操作系统开始的 Windows 版本的默认值。</span><span class="sxs-lookup"><span data-stu-id="989c0-118">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="989c0-119">false</span><span class="sxs-lookup"><span data-stu-id="989c0-119">false</span></span>|<span data-ttu-id="989c0-120">禁用 ETW。</span><span class="sxs-lookup"><span data-stu-id="989c0-120">Disable ETW.</span></span> <span data-ttu-id="989c0-121">这是早期版本的 Windows 的默认设置。</span><span class="sxs-lookup"><span data-stu-id="989c0-121">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="989c0-122">子元素</span><span class="sxs-lookup"><span data-stu-id="989c0-122">Child Elements</span></span>  
 <span data-ttu-id="989c0-123">无。</span><span class="sxs-lookup"><span data-stu-id="989c0-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="989c0-124">父元素</span><span class="sxs-lookup"><span data-stu-id="989c0-124">Parent Elements</span></span>  
  
|<span data-ttu-id="989c0-125">元素</span><span class="sxs-lookup"><span data-stu-id="989c0-125">Element</span></span>|<span data-ttu-id="989c0-126">描述</span><span class="sxs-lookup"><span data-stu-id="989c0-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="989c0-127">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="989c0-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="989c0-128">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="989c0-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="989c0-129">注解</span><span class="sxs-lookup"><span data-stu-id="989c0-129">Remarks</span></span>  
 <span data-ttu-id="989c0-130">从 Windows Vista 开始，默认情况下启用 ETW。</span><span class="sxs-lookup"><span data-stu-id="989c0-130">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="989c0-131">使用此元素可禁用应用程序的 ETW。</span><span class="sxs-lookup"><span data-stu-id="989c0-131">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="989c0-132">在早期版本的 Windows 中，使用此元素为应用程序启用 ETW。</span><span class="sxs-lookup"><span data-stu-id="989c0-132">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="989c0-133">可以通过使用注册表设置在服务器上全局启用或禁用 ETW。</span><span class="sxs-lookup"><span data-stu-id="989c0-133">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="989c0-134">请参阅[控制 .NET Framework 日志记录](../../../performance/controlling-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="989c0-134">See [Controlling .NET Framework Logging](../../../performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="989c0-135">示例</span><span class="sxs-lookup"><span data-stu-id="989c0-135">Example</span></span>  
 <span data-ttu-id="989c0-136">下面的示例演示如何为应用程序启用 ETW 跟踪。</span><span class="sxs-lookup"><span data-stu-id="989c0-136">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="989c0-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="989c0-137">See also</span></span>

- [<span data-ttu-id="989c0-138">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="989c0-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="989c0-139">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="989c0-139">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="989c0-140">控制 .NET Framework 日志记录</span><span class="sxs-lookup"><span data-stu-id="989c0-140">Controlling .NET Framework Logging</span></span>](../../../performance/controlling-logging.md)
