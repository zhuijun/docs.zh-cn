---
title: <etwEnable> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
ms.openlocfilehash: 1c3e42dfbc2c27841ed065e90bad24575e4fb2b1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178263"
---
# <a name="etwenable-element"></a><span data-ttu-id="eb51c-102">\<etwEnable> 元素</span><span class="sxs-lookup"><span data-stu-id="eb51c-102">\<etwEnable> Element</span></span>

<span data-ttu-id="eb51c-103">指定是否为公共语言运行时事件启用 Windows 事件跟踪 (ETW)。</span><span class="sxs-lookup"><span data-stu-id="eb51c-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<etwEnabled>**  
  
## <a name="syntax"></a><span data-ttu-id="eb51c-104">语法</span><span class="sxs-lookup"><span data-stu-id="eb51c-104">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb51c-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="eb51c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="eb51c-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="eb51c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb51c-107">特性</span><span class="sxs-lookup"><span data-stu-id="eb51c-107">Attributes</span></span>  
  
|<span data-ttu-id="eb51c-108">属性</span><span class="sxs-lookup"><span data-stu-id="eb51c-108">Attribute</span></span>|<span data-ttu-id="eb51c-109">说明</span><span class="sxs-lookup"><span data-stu-id="eb51c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eb51c-110">enabled</span><span class="sxs-lookup"><span data-stu-id="eb51c-110">enabled</span></span>|<span data-ttu-id="eb51c-111">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="eb51c-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="eb51c-112">指定是否应启用 ETW。</span><span class="sxs-lookup"><span data-stu-id="eb51c-112">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="eb51c-113">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="eb51c-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="eb51c-114">值</span><span class="sxs-lookup"><span data-stu-id="eb51c-114">Value</span></span>|<span data-ttu-id="eb51c-115">描述</span><span class="sxs-lookup"><span data-stu-id="eb51c-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="eb51c-116">是</span><span class="sxs-lookup"><span data-stu-id="eb51c-116">true</span></span>|<span data-ttu-id="eb51c-117">启用 ETW。</span><span class="sxs-lookup"><span data-stu-id="eb51c-117">Enable ETW.</span></span> <span data-ttu-id="eb51c-118">这是从 Windows Vista 和 Windows Server 2008 操作系统开始的 Windows 版本的默认值。</span><span class="sxs-lookup"><span data-stu-id="eb51c-118">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="eb51c-119">false</span><span class="sxs-lookup"><span data-stu-id="eb51c-119">false</span></span>|<span data-ttu-id="eb51c-120">禁用 ETW。</span><span class="sxs-lookup"><span data-stu-id="eb51c-120">Disable ETW.</span></span> <span data-ttu-id="eb51c-121">这是早期版本的 Windows 的默认设置。</span><span class="sxs-lookup"><span data-stu-id="eb51c-121">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb51c-122">子元素</span><span class="sxs-lookup"><span data-stu-id="eb51c-122">Child Elements</span></span>  

 <span data-ttu-id="eb51c-123">无。</span><span class="sxs-lookup"><span data-stu-id="eb51c-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eb51c-124">父元素</span><span class="sxs-lookup"><span data-stu-id="eb51c-124">Parent Elements</span></span>  
  
|<span data-ttu-id="eb51c-125">元素</span><span class="sxs-lookup"><span data-stu-id="eb51c-125">Element</span></span>|<span data-ttu-id="eb51c-126">描述</span><span class="sxs-lookup"><span data-stu-id="eb51c-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="eb51c-127">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="eb51c-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="eb51c-128">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="eb51c-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb51c-129">备注</span><span class="sxs-lookup"><span data-stu-id="eb51c-129">Remarks</span></span>  

 <span data-ttu-id="eb51c-130">从 Windows Vista 开始，默认情况下启用 ETW。</span><span class="sxs-lookup"><span data-stu-id="eb51c-130">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="eb51c-131">使用此元素可禁用应用程序的 ETW。</span><span class="sxs-lookup"><span data-stu-id="eb51c-131">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="eb51c-132">在早期版本的 Windows 中，使用此元素为应用程序启用 ETW。</span><span class="sxs-lookup"><span data-stu-id="eb51c-132">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eb51c-133">可以通过使用注册表设置在服务器上全局启用或禁用 ETW。</span><span class="sxs-lookup"><span data-stu-id="eb51c-133">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="eb51c-134">请参阅 [控制 .NET Framework 日志记录](../../../performance/controlling-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="eb51c-134">See [Controlling .NET Framework Logging](../../../performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb51c-135">示例</span><span class="sxs-lookup"><span data-stu-id="eb51c-135">Example</span></span>  

 <span data-ttu-id="eb51c-136">下面的示例演示如何为应用程序启用 ETW 跟踪。</span><span class="sxs-lookup"><span data-stu-id="eb51c-136">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb51c-137">请参阅</span><span class="sxs-lookup"><span data-stu-id="eb51c-137">See also</span></span>

- [<span data-ttu-id="eb51c-138">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="eb51c-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="eb51c-139">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="eb51c-139">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="eb51c-140">控制 .NET Framework 日志记录</span><span class="sxs-lookup"><span data-stu-id="eb51c-140">Controlling .NET Framework Logging</span></span>](../../../performance/controlling-logging.md)
