---
title: <disableCommitThreadStack> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack
helpviewer_keywords:
- <disableCommitThreadStack> element
- disableCommitThreadStack element
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
ms.openlocfilehash: f717f57fe8670b126ed1468713a2114aaa772762
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198985"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="c3f63-102">\<disableCommitThreadStack> 元素</span><span class="sxs-lookup"><span data-stu-id="c3f63-102">\<disableCommitThreadStack> Element</span></span>

<span data-ttu-id="c3f63-103">指定在线程启动时是否提交完整线程堆栈。</span><span class="sxs-lookup"><span data-stu-id="c3f63-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCommitThreadStack>**  
  
## <a name="syntax"></a><span data-ttu-id="c3f63-104">语法</span><span class="sxs-lookup"><span data-stu-id="c3f63-104">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3f63-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="c3f63-105">Attributes and Elements</span></span>  

 <span data-ttu-id="c3f63-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c3f63-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3f63-107">特性</span><span class="sxs-lookup"><span data-stu-id="c3f63-107">Attributes</span></span>  
  
|<span data-ttu-id="c3f63-108">属性</span><span class="sxs-lookup"><span data-stu-id="c3f63-108">Attribute</span></span>|<span data-ttu-id="c3f63-109">说明</span><span class="sxs-lookup"><span data-stu-id="c3f63-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c3f63-110">enabled</span><span class="sxs-lookup"><span data-stu-id="c3f63-110">enabled</span></span>|<span data-ttu-id="c3f63-111">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="c3f63-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="c3f63-112">指定是否禁止在线程启动时提交完整线程堆栈（默认行为）。</span><span class="sxs-lookup"><span data-stu-id="c3f63-112">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c3f63-113">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="c3f63-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="c3f63-114">值</span><span class="sxs-lookup"><span data-stu-id="c3f63-114">Value</span></span>|<span data-ttu-id="c3f63-115">描述</span><span class="sxs-lookup"><span data-stu-id="c3f63-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c3f63-116">0</span><span class="sxs-lookup"><span data-stu-id="c3f63-116">0</span></span>|<span data-ttu-id="c3f63-117">不禁用公共语言运行时的默认行为（即在线程启动时提交完整线程堆栈）。</span><span class="sxs-lookup"><span data-stu-id="c3f63-117">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="c3f63-118">1</span><span class="sxs-lookup"><span data-stu-id="c3f63-118">1</span></span>|<span data-ttu-id="c3f63-119">禁用公共语言运行时的默认行为（即在线程启动时提交完整线程堆栈）。</span><span class="sxs-lookup"><span data-stu-id="c3f63-119">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c3f63-120">子元素</span><span class="sxs-lookup"><span data-stu-id="c3f63-120">Child Elements</span></span>  

 <span data-ttu-id="c3f63-121">无。</span><span class="sxs-lookup"><span data-stu-id="c3f63-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c3f63-122">父元素</span><span class="sxs-lookup"><span data-stu-id="c3f63-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c3f63-123">元素</span><span class="sxs-lookup"><span data-stu-id="c3f63-123">Element</span></span>|<span data-ttu-id="c3f63-124">描述</span><span class="sxs-lookup"><span data-stu-id="c3f63-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c3f63-125">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="c3f63-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c3f63-126">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="c3f63-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3f63-127">备注</span><span class="sxs-lookup"><span data-stu-id="c3f63-127">Remarks</span></span>  

 <span data-ttu-id="c3f63-128">公共语言运行时的默认行为是在线程启动时提交完整线程堆栈。</span><span class="sxs-lookup"><span data-stu-id="c3f63-128">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="c3f63-129">当必须在内存有限的服务器上创建大量线程，并且其中大多数线程都使用非常小的堆栈空间时，如果公共语言运行时在线程启动时不立即提交完整线程堆栈，则服务器可能会表现更好。</span><span class="sxs-lookup"><span data-stu-id="c3f63-129">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c3f63-130">非托管主机可以使用 `STARTUP_DISABLE_COMMITTHREADSTACK` STARTUP_FLAGS [枚举中的](../../../unmanaged-api/hosting/startup-flags-enumeration.md) 启动标志实现相同结果。</span><span class="sxs-lookup"><span data-stu-id="c3f63-130">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3f63-131">示例</span><span class="sxs-lookup"><span data-stu-id="c3f63-131">Example</span></span>  

 <span data-ttu-id="c3f63-132">下面的示例演示如何禁用公共语言运行时的默认行为（即在线程启动时提交完整线程堆栈）。</span><span class="sxs-lookup"><span data-stu-id="c3f63-132">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3f63-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="c3f63-133">See also</span></span>

- [<span data-ttu-id="c3f63-134">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="c3f63-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c3f63-135">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="c3f63-135">Configuration File Schema</span></span>](../index.md)
