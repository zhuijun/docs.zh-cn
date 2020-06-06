---
title: <ThrowUnobservedTaskExceptions> 元素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
ms.openlocfilehash: de5a686bcbd88fc52173b488103f033575623d62
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153810"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="c29c8-102">\<ThrowUnobservedTaskExceptions> 元素</span><span class="sxs-lookup"><span data-stu-id="c29c8-102">\<ThrowUnobservedTaskExceptions> Element</span></span>
<span data-ttu-id="c29c8-103">指定未经处理的任务异常是否应终止正在运行的进程。</span><span class="sxs-lookup"><span data-stu-id="c29c8-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**  
  
## <a name="syntax"></a><span data-ttu-id="c29c8-104">语法</span><span class="sxs-lookup"><span data-stu-id="c29c8-104">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c29c8-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="c29c8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c29c8-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c29c8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c29c8-107">特性</span><span class="sxs-lookup"><span data-stu-id="c29c8-107">Attributes</span></span>  
  
|<span data-ttu-id="c29c8-108">属性</span><span class="sxs-lookup"><span data-stu-id="c29c8-108">Attribute</span></span>|<span data-ttu-id="c29c8-109">说明</span><span class="sxs-lookup"><span data-stu-id="c29c8-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="c29c8-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="c29c8-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="c29c8-111">指定未经处理的任务异常是否应终止正在运行的进程。</span><span class="sxs-lookup"><span data-stu-id="c29c8-111">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c29c8-112">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="c29c8-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="c29c8-113">值</span><span class="sxs-lookup"><span data-stu-id="c29c8-113">Value</span></span>|<span data-ttu-id="c29c8-114">说明</span><span class="sxs-lookup"><span data-stu-id="c29c8-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="c29c8-115">对于未处理的任务异常，不会终止正在运行的进程。</span><span class="sxs-lookup"><span data-stu-id="c29c8-115">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="c29c8-116">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="c29c8-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="c29c8-117">终止正在运行的进程的未处理任务异常。</span><span class="sxs-lookup"><span data-stu-id="c29c8-117">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c29c8-118">子元素</span><span class="sxs-lookup"><span data-stu-id="c29c8-118">Child Elements</span></span>  
 <span data-ttu-id="c29c8-119">无。</span><span class="sxs-lookup"><span data-stu-id="c29c8-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c29c8-120">父元素</span><span class="sxs-lookup"><span data-stu-id="c29c8-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c29c8-121">元素</span><span class="sxs-lookup"><span data-stu-id="c29c8-121">Element</span></span>|<span data-ttu-id="c29c8-122">描述</span><span class="sxs-lookup"><span data-stu-id="c29c8-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c29c8-123">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="c29c8-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c29c8-124">包含有关运行时初始化选项的信息。</span><span class="sxs-lookup"><span data-stu-id="c29c8-124">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="c29c8-125">注解</span><span class="sxs-lookup"><span data-stu-id="c29c8-125">Remarks</span></span>  
 <span data-ttu-id="c29c8-126">如果未观察到与关联的异常 <xref:System.Threading.Tasks.Task> ，则不会进行任何 <xref:System.Threading.Tasks.Task.Wait%2A> 操作，也不会附加父级，并且该 <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> 属性不会被视为未观察到。</span><span class="sxs-lookup"><span data-stu-id="c29c8-126">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="c29c8-127">在 .NET Framework 4 中，默认情况下，如果 <xref:System.Threading.Tasks.Task> 存在未观察到异常的，则终结器将引发异常并终止进程。</span><span class="sxs-lookup"><span data-stu-id="c29c8-127">In the .NET Framework 4, by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="c29c8-128">进程终止由垃圾回收和终止的时间决定。</span><span class="sxs-lookup"><span data-stu-id="c29c8-128">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="c29c8-129">为了使开发人员可以更轻松地根据任务编写异步代码，.NET Framework 4.5 更改未观察到异常的此默认行为。</span><span class="sxs-lookup"><span data-stu-id="c29c8-129">To make it easier for developers to write asynchronous code based on tasks, the .NET Framework 4.5 changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="c29c8-130">未观察到异常仍会 <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> 引发事件，但在默认情况下，进程不会终止。</span><span class="sxs-lookup"><span data-stu-id="c29c8-130">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="c29c8-131">相反，引发事件后将忽略此异常，而不管事件处理程序是否观察到该异常。</span><span class="sxs-lookup"><span data-stu-id="c29c8-131">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="c29c8-132">在 .NET Framework 4.5 中，可以使用应用程序配置文件中的[ \<ThrowUnobservedTaskExceptions> 元素](throwunobservedtaskexceptions-element.md)来启用引发异常的 .NET Framework 4 行为。</span><span class="sxs-lookup"><span data-stu-id="c29c8-132">In the .NET Framework 4.5, you can use the [\<ThrowUnobservedTaskExceptions> element](throwunobservedtaskexceptions-element.md) in an application configuration file to enable the .NET Framework 4 behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="c29c8-133">还可以通过以下方式之一指定异常行为：</span><span class="sxs-lookup"><span data-stu-id="c29c8-133">You can also specify the exception behavior in one of the following ways:</span></span>  
  
- <span data-ttu-id="c29c8-134">通过设置环境变量 `COMPlus_ThrowUnobservedTaskExceptions` （ `set COMPlus_ThrowUnobservedTaskExceptions=1` ）。</span><span class="sxs-lookup"><span data-stu-id="c29c8-134">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
- <span data-ttu-id="c29c8-135">通过在 HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft 中设置注册表 DWORD 值 ThrowUnobservedTaskExceptions = 1 \\ 。.Netframework 键。</span><span class="sxs-lookup"><span data-stu-id="c29c8-135">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c29c8-136">示例</span><span class="sxs-lookup"><span data-stu-id="c29c8-136">Example</span></span>  
 <span data-ttu-id="c29c8-137">下面的示例演示如何使用应用程序配置文件在任务中启用异常引发。</span><span class="sxs-lookup"><span data-stu-id="c29c8-137">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="c29c8-138">示例</span><span class="sxs-lookup"><span data-stu-id="c29c8-138">Example</span></span>  
 <span data-ttu-id="c29c8-139">下面的示例演示如何从任务中引发未观察到异常。</span><span class="sxs-lookup"><span data-stu-id="c29c8-139">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="c29c8-140">必须以发布程序的形式运行代码，才能正常工作。</span><span class="sxs-lookup"><span data-stu-id="c29c8-140">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c29c8-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c29c8-141">See also</span></span>

- [<span data-ttu-id="c29c8-142">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="c29c8-142">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c29c8-143">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="c29c8-143">Configuration File Schema</span></span>](../index.md)
