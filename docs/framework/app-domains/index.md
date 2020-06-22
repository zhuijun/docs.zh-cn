---
title: 使用应用程序域和程序集编程
description: 了解如何在 .NET 中使用应用程序域和程序集进行编程。 请参阅关于如何创建应用程序域和程序集的操作指南主题和示例的链接。
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
ms.openlocfilehash: 1c28fe0abeb279a1dbbc6dcf043c1780c72d79df
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903433"
---
# <a name="programming-with-application-domains-and-assemblies"></a><span data-ttu-id="2c763-104">使用应用程序域和程序集编程</span><span class="sxs-lookup"><span data-stu-id="2c763-104">Programming with Application Domains and Assemblies</span></span>

<span data-ttu-id="2c763-105">Microsoft Internet Explorer、ASP.NET 和 Windows Shell 等主机将公共语言运行时加载到进程中，在相应进程中创建[应用程序域](application-domains.md)，然后在 .NET Framework 应用程序运行时加载并执行相应应用程序域中的用户代码。</span><span class="sxs-lookup"><span data-stu-id="2c763-105">Hosts such as Microsoft Internet Explorer, ASP.NET, and the Windows shell load the common language runtime into a process, create an [application domain](application-domains.md) in that process, and then load and execute user code in that application domain when running a .NET Framework application.</span></span> <span data-ttu-id="2c763-106">在大多数情况下，不必担心创建应用程序域和将程序集加载到这些域中，因为运行时主机会执行这些任务。</span><span class="sxs-lookup"><span data-stu-id="2c763-106">In most cases, you do not have to worry about creating application domains and loading assemblies into them because the runtime host performs those tasks.</span></span>  
  
<span data-ttu-id="2c763-107">不过，如果要创建将托管公共语言运行时的应用程序、要创建以编程方式卸载的工具/代码或要创建可以动态卸载和重载的可插入组件，需要创建自己的应用程序域。</span><span class="sxs-lookup"><span data-stu-id="2c763-107">However, if you are creating an application that will host the common language runtime, creating tools or code you want to unload programmatically, or creating pluggable components that can be unloaded and reloaded on the fly, you will be creating your own application domains.</span></span> <span data-ttu-id="2c763-108">即使不要创建运行时主机，也可以参阅本部分，其中介绍了有关如何使用应用程序域和这些应用程序域中加载的程序集的重要信息。</span><span class="sxs-lookup"><span data-stu-id="2c763-108">Even if you are not creating a runtime host, this section provides important information on how to work with application domains and assemblies loaded in these application domains.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2c763-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="2c763-109">In This Section</span></span>  

[<span data-ttu-id="2c763-110">应用程序域和程序集用法主题</span><span class="sxs-lookup"><span data-stu-id="2c763-110">Application Domains and Assemblies How-to Topics</span></span>](application-domains-and-assemblies-how-to-topics.md)  
<span data-ttu-id="2c763-111">收录了使用应用程序域和程序集进行编程的相关概念性文档中的所有用法主题链接。</span><span class="sxs-lookup"><span data-stu-id="2c763-111">Provides links to all How-to topics found in the conceptual documentation for programming with application domains and assemblies.</span></span>  
  
[<span data-ttu-id="2c763-112">使用应用程序域</span><span class="sxs-lookup"><span data-stu-id="2c763-112">Using Application Domains</span></span>](use.md)  
<span data-ttu-id="2c763-113">举例说明了如何创建、配置和使用应用程序域。</span><span class="sxs-lookup"><span data-stu-id="2c763-113">Provides examples of creating, configuring, and using application domains.</span></span>  
  
[<span data-ttu-id="2c763-114">使用程序集编程</span><span class="sxs-lookup"><span data-stu-id="2c763-114">Programming with Assemblies</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="2c763-115">描述如何在程序集上创建、签署和设置特性。</span><span class="sxs-lookup"><span data-stu-id="2c763-115">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2c763-116">相关章节</span><span class="sxs-lookup"><span data-stu-id="2c763-116">Related Sections</span></span>  

[<span data-ttu-id="2c763-117">发出动态方法和程序集</span><span class="sxs-lookup"><span data-stu-id="2c763-117">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="2c763-118">描述如何创建动态程序集。</span><span class="sxs-lookup"><span data-stu-id="2c763-118">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="2c763-119">.NET 中的程序集</span><span class="sxs-lookup"><span data-stu-id="2c763-119">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="2c763-120">提供程序集的概念性概述。</span><span class="sxs-lookup"><span data-stu-id="2c763-120">Provides a conceptual overview of assemblies.</span></span>  
  
[<span data-ttu-id="2c763-121">应用程序域</span><span class="sxs-lookup"><span data-stu-id="2c763-121">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="2c763-122">提供应用程序域的概念性概述。</span><span class="sxs-lookup"><span data-stu-id="2c763-122">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="2c763-123">反射概述</span><span class="sxs-lookup"><span data-stu-id="2c763-123">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="2c763-124">介绍了如何使用 **Reflection** 类获取程序集的信息。</span><span class="sxs-lookup"><span data-stu-id="2c763-124">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
