---
title: 针对共享 Web 承载优化
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
ms.openlocfilehash: ccaacd44f8aaed9c3178cb94f98b0f58d4d3c7d4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285984"
---
# <a name="optimization-for-shared-web-hosting"></a><span data-ttu-id="6095a-102">针对共享 Web 承载优化</span><span class="sxs-lookup"><span data-stu-id="6095a-102">Optimization for Shared Web Hosting</span></span>
<span data-ttu-id="6095a-103">如果是通过托管多个小型网站进行共享的服务器的管理员，可以将下列 `gcTrimCommitOnLowMemory` 设置添加到 .NET 目录中 Aspnet.config 文件内的 `runtime` 节点，从而优化性能和增加网站容量：</span><span class="sxs-lookup"><span data-stu-id="6095a-103">If you are the administrator for a server that is shared by hosting several small Web sites, you can optimize performance and increase site capacity by adding the following `gcTrimCommitOnLowMemory` setting to the `runtime` node in the Aspnet.config file in the .NET directory:</span></span>  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
> <span data-ttu-id="6095a-104">此建议设置仅适用于共享 Web 托管方案。</span><span class="sxs-lookup"><span data-stu-id="6095a-104">This setting is recommended only for shared Web hosting scenarios.</span></span>  
  
 <span data-ttu-id="6095a-105">由于垃圾回收器保留内存以供将来分配，因此它提交的空间可能会超过真正所需。</span><span class="sxs-lookup"><span data-stu-id="6095a-105">Because the garbage collector retains memory for future allocations, its committed space can be more than what is strictly needed.</span></span> <span data-ttu-id="6095a-106">可以减少此空间来适应系统内存负载过重的情况。</span><span class="sxs-lookup"><span data-stu-id="6095a-106">You can reduce this space to accommodate times when there is a heavy load on system memory.</span></span> <span data-ttu-id="6095a-107">减少提交的此空间可提升性能，并将容量扩展为托管更多网站。</span><span class="sxs-lookup"><span data-stu-id="6095a-107">Reducing this committed space improves performance and expands the capacity to host more sites.</span></span>  
  
 <span data-ttu-id="6095a-108">如果启用 `gcTrimCommitOnLowMemory` 设置，垃圾回收器会计算系统内存负载，并在负载达到 90% 时进入修整模式。</span><span class="sxs-lookup"><span data-stu-id="6095a-108">When the `gcTrimCommitOnLowMemory` setting is enabled, the garbage collector evaluates the system memory load and enters a trimming mode when the load reaches 90%.</span></span> <span data-ttu-id="6095a-109">除非负载下降到不到 85%，否则会一直处于修整模式。</span><span class="sxs-lookup"><span data-stu-id="6095a-109">It maintains the trimming mode until the load drops under 85%.</span></span>  
  
 <span data-ttu-id="6095a-110">如果条件允许，垃圾回收器可以决定 `gcTrimCommitOnLowMemory` 设置对当前应用没有帮助并忽略它。</span><span class="sxs-lookup"><span data-stu-id="6095a-110">When conditions permit, the garbage collector can decide that the `gcTrimCommitOnLowMemory` setting will not help the current application and ignore it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6095a-111">示例</span><span class="sxs-lookup"><span data-stu-id="6095a-111">Example</span></span>  
 <span data-ttu-id="6095a-112">下面的 XML 片段展示了如何启用 `gcTrimCommitOnLowMemory` 设置。</span><span class="sxs-lookup"><span data-stu-id="6095a-112">The following XML fragment shows how to enable the `gcTrimCommitOnLowMemory` setting.</span></span> <span data-ttu-id="6095a-113">省略号表示 `runtime` 节点中会有其他设置。</span><span class="sxs-lookup"><span data-stu-id="6095a-113">Ellipses indicate other settings that would be in the `runtime` node.</span></span>  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<configuration>  
    <runtime>  
    . . .  
    <gcTrimCommitOnLowMemory enabled="true"/>  
    </runtime>  
    . . .  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6095a-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6095a-114">See also</span></span>

- [<span data-ttu-id="6095a-115">垃圾回收</span><span class="sxs-lookup"><span data-stu-id="6095a-115">Garbage Collection</span></span>](index.md)
