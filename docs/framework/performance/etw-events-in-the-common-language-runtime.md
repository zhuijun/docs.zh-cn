---
title: 公共语言运行时中的 ETW 事件
description: 阅读有关公共语言运行时 (CLR) 中的 Windows () ETW 事件跟踪的摘要和查看链接。
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: 5bb9b6a2-7b57-4aea-8809-32b28bc73e88
ms.openlocfilehash: e1da57abba559cdb1e54071c103d67b5327c30ac
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553696"
---
# <a name="etw-events-in-the-common-language-runtime"></a><span data-ttu-id="cff77-103">公共语言运行时中的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="cff77-103">ETW Events in the Common Language Runtime</span></span>
<span data-ttu-id="cff77-104">公共语言运行时 (CLR) 通过大量的调试和分析事件，提供有用的 Windows 事件跟踪 (ETW) 诊断信息。</span><span class="sxs-lookup"><span data-stu-id="cff77-104">The common language runtime (CLR) provides useful event tracing for Windows (ETW) diagnostic information through a large variety of debugging and profiling events.</span></span> <span data-ttu-id="cff77-105">CLR ETW 事件利用 Windows ETW 跟踪系统来扩充公共语言运行时所提供的现有分析和调试支持。</span><span class="sxs-lookup"><span data-stu-id="cff77-105">CLR ETW events leverage the Windows ETW tracing system to augment the existing profiling and debugging support provided by the common language runtime.</span></span>  
  
 <span data-ttu-id="cff77-106">[使用 Etw 改善调试和性能优化](/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)一文中提供了有关 etw 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="cff77-106">More information about ETW is available in the [Improve Debugging and Performance Tuning with ETW](/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw) article.</span></span> <span data-ttu-id="cff77-107">有关 Xperf 的详细信息，请参阅 NTDebugging 博客中的 [Windows Performance Toolkit - Xperf](/archive/blogs/ntdebugging/windows-performance-toolkit-xperf)（Windows 性能工具包 - Xperf）。</span><span class="sxs-lookup"><span data-stu-id="cff77-107">Information about Xperf can be found in the entry [Windows Performance Toolkit - Xperf](/archive/blogs/ntdebugging/windows-performance-toolkit-xperf) in the NTDebugging blog.</span></span>  
  
 <span data-ttu-id="cff77-108">事件主题中所述的所有事件都需要 .NET Framework 4 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="cff77-108">The .NET Framework 4 or later is required for all the events described in the event topics.</span></span> <span data-ttu-id="cff77-109">Windows Vista 操作系统是支持的最低客户端，而 Windows Server 2008 是支持的最低服务器。</span><span class="sxs-lookup"><span data-stu-id="cff77-109">The Windows Vista operating system is the minimum supported client, and Windows Server 2008 is the minimum supported server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cff77-110">本节内容</span><span class="sxs-lookup"><span data-stu-id="cff77-110">In This Section</span></span>  
 [<span data-ttu-id="cff77-111">控制 .NET Framework 日志记录</span><span class="sxs-lookup"><span data-stu-id="cff77-111">Controlling .NET Framework Logging</span></span>](controlling-logging.md)  
 <span data-ttu-id="cff77-112">介绍用于捕获和查看 ETW 事件的工具和命令。</span><span class="sxs-lookup"><span data-stu-id="cff77-112">Describes the tools and commands for capturing and viewing ETW events.</span></span>  
  
 [<span data-ttu-id="cff77-113">CLR ETW 提供程序</span><span class="sxs-lookup"><span data-stu-id="cff77-113">CLR ETW Providers</span></span>](clr-etw-providers.md)  
 <span data-ttu-id="cff77-114">提供有关运行时和断开提供程序，以及如何使用它们收集 ETW 数据的信息。</span><span class="sxs-lookup"><span data-stu-id="cff77-114">Provides information about the runtime and rundown providers, and how you can use them for ETW data collection.</span></span>  
  
 [<span data-ttu-id="cff77-115">CLR ETW 关键字和级别</span><span class="sxs-lookup"><span data-stu-id="cff77-115">CLR ETW Keywords and Levels</span></span>](clr-etw-keywords-and-levels.md)  
 <span data-ttu-id="cff77-116">介绍运行时和断开提供程序的关键字，可通过这些关键字按类别筛选事件。</span><span class="sxs-lookup"><span data-stu-id="cff77-116">Describes the keywords for the Runtime and Rundown providers that enable the filtering of events by category.</span></span>  
  
 [<span data-ttu-id="cff77-117">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="cff77-117">CLR ETW Events</span></span>](clr-etw-events.md)  
 <span data-ttu-id="cff77-118">提供有关 CLR ETW 事件及其关键字、级别和事件数据的详细信息。</span><span class="sxs-lookup"><span data-stu-id="cff77-118">Provides detailed information about CLR ETW events, their keywords, levels, and event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cff77-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="cff77-119">See also</span></span>

- [<span data-ttu-id="cff77-120">ETW Events in the .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cff77-120">ETW Events in the .NET Framework</span></span>](etw-events.md)
