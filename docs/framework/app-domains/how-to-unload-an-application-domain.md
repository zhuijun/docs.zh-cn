---
title: 如何：卸载应用程序域
description: 了解如何使用 AppDomain.Unload 方法在 .NET 中卸载应用程序域，从而正常关闭指定的应用程序域。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Unload method
- application domains, unloading
- unloading application domains
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
ms.openlocfilehash: b64a9553f63aa4a8deb57f23a97fa464edd64fee
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104664"
---
# <a name="how-to-unload-an-application-domain"></a><span data-ttu-id="5f875-103">如何：卸载应用程序域</span><span class="sxs-lookup"><span data-stu-id="5f875-103">How to: Unload an Application Domain</span></span>
<span data-ttu-id="5f875-104">完成使用应用程序域时，可使用 <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> 方法将其卸载。</span><span class="sxs-lookup"><span data-stu-id="5f875-104">When you have finished using an application domain, unload it using the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5f875-105">**Unload** 方法会正常关闭指定的应用程序域。</span><span class="sxs-lookup"><span data-stu-id="5f875-105">The **Unload** method gracefully shuts down the specified application domain.</span></span> <span data-ttu-id="5f875-106">卸载过程中，任何新线程都无法访问该应用程序域，并且会释放所有特性于应用程序域的数据结构。</span><span class="sxs-lookup"><span data-stu-id="5f875-106">During the unloading process, no new threads can access the application domain, and all application domain–specific data structures are freed.</span></span>  
  
 <span data-ttu-id="5f875-107">加载到应用程序域中的所有程序集都会被移除，无法再使用。</span><span class="sxs-lookup"><span data-stu-id="5f875-107">Assemblies loaded into the application domain are removed and are no longer available.</span></span> <span data-ttu-id="5f875-108">如果应用程序域中的程序集不特定于域，则程序集的数据会保留在内存中，直到整个进程关闭。</span><span class="sxs-lookup"><span data-stu-id="5f875-108">If an assembly in the application domain is domain-neutral, data for the assembly remains in memory until the entire process is shut down.</span></span> <span data-ttu-id="5f875-109">除了关闭整个进程，没有机制可以卸载非特定于域的程序集。</span><span class="sxs-lookup"><span data-stu-id="5f875-109">There is no mechanism to unload a domain-neutral assembly other than shutting down the entire process.</span></span> <span data-ttu-id="5f875-110">在某些情况下，卸载应用程序域的请求会不起作用，并导致 <xref:System.CannotUnloadAppDomainException>。</span><span class="sxs-lookup"><span data-stu-id="5f875-110">There are situations where the request to unload an application domain does not work and results in a <xref:System.CannotUnloadAppDomainException>.</span></span>  
  
 <span data-ttu-id="5f875-111">以下示例新建名为 `MyDomain` 的应用程序域，并将一些信息输出至控制台，然后卸载应用程序域。</span><span class="sxs-lookup"><span data-stu-id="5f875-111">The following example creates a new application domain called `MyDomain`, prints some information to the console, and then unloads the application domain.</span></span> <span data-ttu-id="5f875-112">请注意，代码随后会尝试将卸载的应用程序域的友好名称输出至控制台。</span><span class="sxs-lookup"><span data-stu-id="5f875-112">Note that the code then attempts to print the friendly name of the unloaded application domain to the console.</span></span> <span data-ttu-id="5f875-113">此操作生成一个异常，该异常由程序结尾处的 try/catch 语句处理。</span><span class="sxs-lookup"><span data-stu-id="5f875-113">This action generates an exception that is handled by the try/catch statements at the end of the program.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f875-114">示例</span><span class="sxs-lookup"><span data-stu-id="5f875-114">Example</span></span>  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="5f875-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="5f875-115">See also</span></span>

- [<span data-ttu-id="5f875-116">对应用程序域进行编程</span><span class="sxs-lookup"><span data-stu-id="5f875-116">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="5f875-117">如何：创建应用程序域</span><span class="sxs-lookup"><span data-stu-id="5f875-117">How to: Create an Application Domain</span></span>](how-to-create-an-application-domain.md)
- [<span data-ttu-id="5f875-118">使用应用程序域</span><span class="sxs-lookup"><span data-stu-id="5f875-118">Using Application Domains</span></span>](use.md)
