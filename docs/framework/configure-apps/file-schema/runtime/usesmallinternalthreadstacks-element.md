---
title: <UseSmallInternalThreadStacks> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
ms.openlocfilehash: 4917b47e9e8196eabe691f74531d12308ef80311
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174077"
---
# <a name="usesmallinternalthreadstacks-element"></a><span data-ttu-id="3927e-102">\<UseSmallInternalThreadStacks> 元素</span><span class="sxs-lookup"><span data-stu-id="3927e-102">\<UseSmallInternalThreadStacks> Element</span></span>

<span data-ttu-id="3927e-103">请求公共语言运行时 (CLR) 在创建其内部使用的某些线程时指定显式堆栈大小来减少内存使用，而不是使用这些线程的默认堆栈大小。</span><span class="sxs-lookup"><span data-stu-id="3927e-103">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<UseSmallInternalThreadStacks>**  
  
## <a name="syntax"></a><span data-ttu-id="3927e-104">语法</span><span class="sxs-lookup"><span data-stu-id="3927e-104">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3927e-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="3927e-105">Attributes and Elements</span></span>  

 <span data-ttu-id="3927e-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3927e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3927e-107">特性</span><span class="sxs-lookup"><span data-stu-id="3927e-107">Attributes</span></span>  
  
|<span data-ttu-id="3927e-108">属性</span><span class="sxs-lookup"><span data-stu-id="3927e-108">Attribute</span></span>|<span data-ttu-id="3927e-109">说明</span><span class="sxs-lookup"><span data-stu-id="3927e-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3927e-110">enabled</span><span class="sxs-lookup"><span data-stu-id="3927e-110">enabled</span></span>|<span data-ttu-id="3927e-111">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="3927e-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="3927e-112">指定是否请求 CLR 在创建其内部使用的某些线程时使用显式堆栈大小而不是默认堆栈大小。</span><span class="sxs-lookup"><span data-stu-id="3927e-112">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="3927e-113">显式堆栈大小小于默认堆栈大小 1 MB。</span><span class="sxs-lookup"><span data-stu-id="3927e-113">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3927e-114">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="3927e-114">enabled Attribute</span></span>  
  
|<span data-ttu-id="3927e-115">值</span><span class="sxs-lookup"><span data-stu-id="3927e-115">Value</span></span>|<span data-ttu-id="3927e-116">描述</span><span class="sxs-lookup"><span data-stu-id="3927e-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3927e-117">是</span><span class="sxs-lookup"><span data-stu-id="3927e-117">true</span></span>|<span data-ttu-id="3927e-118">请求显式堆栈大小。</span><span class="sxs-lookup"><span data-stu-id="3927e-118">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="3927e-119">false</span><span class="sxs-lookup"><span data-stu-id="3927e-119">false</span></span>|<span data-ttu-id="3927e-120">使用默认堆栈大小。</span><span class="sxs-lookup"><span data-stu-id="3927e-120">Use the default stack size.</span></span> <span data-ttu-id="3927e-121">这是 .NET Framework 4 的默认值。</span><span class="sxs-lookup"><span data-stu-id="3927e-121">This is the default for the .NET Framework 4.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3927e-122">子元素</span><span class="sxs-lookup"><span data-stu-id="3927e-122">Child Elements</span></span>  

 <span data-ttu-id="3927e-123">无。</span><span class="sxs-lookup"><span data-stu-id="3927e-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3927e-124">父元素</span><span class="sxs-lookup"><span data-stu-id="3927e-124">Parent Elements</span></span>  
  
|<span data-ttu-id="3927e-125">元素</span><span class="sxs-lookup"><span data-stu-id="3927e-125">Element</span></span>|<span data-ttu-id="3927e-126">描述</span><span class="sxs-lookup"><span data-stu-id="3927e-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3927e-127">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="3927e-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3927e-128">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="3927e-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3927e-129">备注</span><span class="sxs-lookup"><span data-stu-id="3927e-129">Remarks</span></span>  

 <span data-ttu-id="3927e-130">此配置元素用于请求进程中减少的虚拟内存使用，因为 CLR 用于其内部线程的显式线程大小（如果请求被接受）小于默认大小。</span><span class="sxs-lookup"><span data-stu-id="3927e-130">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3927e-131">此配置元素是对 CLR 的请求，而不是绝对要求。</span><span class="sxs-lookup"><span data-stu-id="3927e-131">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="3927e-132">在 .NET Framework 4 中，请求仅适用于 x86 体系结构。</span><span class="sxs-lookup"><span data-stu-id="3927e-132">In the .NET Framework 4, the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="3927e-133">在未来版本的 CLR 中，可能会完全忽略此元素，或将其替换为所选内部线程始终使用的显式堆栈大小。</span><span class="sxs-lookup"><span data-stu-id="3927e-133">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="3927e-134">如果 CLR 接受请求，则指定此配置元素会在较小的虚拟内存使用情况下提高可靠性，因为较小的堆栈大小可能会导致堆栈溢出。</span><span class="sxs-lookup"><span data-stu-id="3927e-134">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3927e-135">示例</span><span class="sxs-lookup"><span data-stu-id="3927e-135">Example</span></span>  

 <span data-ttu-id="3927e-136">下面的示例演示如何请求 CLR 对其内部使用的某些线程使用显式堆栈大小。</span><span class="sxs-lookup"><span data-stu-id="3927e-136">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3927e-137">请参阅</span><span class="sxs-lookup"><span data-stu-id="3927e-137">See also</span></span>

- [<span data-ttu-id="3927e-138">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="3927e-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3927e-139">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="3927e-139">Configuration File Schema</span></span>](../index.md)
