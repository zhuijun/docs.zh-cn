---
title: 优化应用程序性能
description: 使用这些资源提高 Windows Presentation Foundation 应用程序的性能，例如规划性能和充分利用硬件。
ms.date: 03/30/2017
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
ms.openlocfilehash: 165caaf102a66988db0254839a947b8e262a386d
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166333"
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="30d87-103">优化 WPF 应用程序性能</span><span class="sxs-lookup"><span data-stu-id="30d87-103">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="30d87-104">本部分旨在作为 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 正在寻找提高应用程序性能的方法的应用程序开发人员的参考。</span><span class="sxs-lookup"><span data-stu-id="30d87-104">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="30d87-105">如果你是 Microsoft .NET 框架的新手的开发人员 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ，则应首先熟悉这两个平台。</span><span class="sxs-lookup"><span data-stu-id="30d87-105">If you are a developer who is new to the Microsoft .NET Framework and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="30d87-106">本部分假设同时了解这两种情况，并为已知道足以启动并运行应用程序的程序员编写这些内容。</span><span class="sxs-lookup"><span data-stu-id="30d87-106">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30d87-107">本部分中提供的性能数据基于 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 2.8 GHZ 电脑上运行的应用程序，其中包含 512 RAM 和 ATI Radeon 9700 图形卡。</span><span class="sxs-lookup"><span data-stu-id="30d87-107">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="30d87-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="30d87-108">In This Section</span></span>  
 [<span data-ttu-id="30d87-109">规划应用程序性能</span><span class="sxs-lookup"><span data-stu-id="30d87-109">Planning for Application Performance</span></span>](planning-for-application-performance.md)  
  
 [<span data-ttu-id="30d87-110">利用硬件</span><span class="sxs-lookup"><span data-stu-id="30d87-110">Taking Advantage of Hardware</span></span>](optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="30d87-111">布局和示例</span><span class="sxs-lookup"><span data-stu-id="30d87-111">Layout and Design</span></span>](optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="30d87-112">二维图形和图像处理</span><span class="sxs-lookup"><span data-stu-id="30d87-112">2D Graphics and Imaging</span></span>](optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="30d87-113">对象行为</span><span class="sxs-lookup"><span data-stu-id="30d87-113">Object Behavior</span></span>](optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="30d87-114">应用程序资源</span><span class="sxs-lookup"><span data-stu-id="30d87-114">Application Resources</span></span>](optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="30d87-115">Text</span><span class="sxs-lookup"><span data-stu-id="30d87-115">Text</span></span>](optimizing-performance-text.md)  
  
 [<span data-ttu-id="30d87-116">数据绑定</span><span class="sxs-lookup"><span data-stu-id="30d87-116">Data Binding</span></span>](optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="30d87-117">控制</span><span class="sxs-lookup"><span data-stu-id="30d87-117">Controls</span></span>](optimizing-performance-controls.md)  
  
 [<span data-ttu-id="30d87-118">其他性能建议</span><span class="sxs-lookup"><span data-stu-id="30d87-118">Other Performance Recommendations</span></span>](optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="30d87-119">应用程序启动时间</span><span class="sxs-lookup"><span data-stu-id="30d87-119">Application Startup Time</span></span>](application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="30d87-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="30d87-120">See also</span></span>

- <xref:System.Windows.Media.RenderOptions>
- <xref:System.Windows.Media.RenderCapability>
- [<span data-ttu-id="30d87-121">图形呈现层</span><span class="sxs-lookup"><span data-stu-id="30d87-121">Graphics Rendering Tiers</span></span>](graphics-rendering-tiers.md)
- [<span data-ttu-id="30d87-122">WPF 图形呈现疑难解答</span><span class="sxs-lookup"><span data-stu-id="30d87-122">WPF Graphics Rendering Overview</span></span>](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [<span data-ttu-id="30d87-123">布局</span><span class="sxs-lookup"><span data-stu-id="30d87-123">Layout</span></span>](layout.md)
- [<span data-ttu-id="30d87-124">WPF 中的树</span><span class="sxs-lookup"><span data-stu-id="30d87-124">Trees in WPF</span></span>](trees-in-wpf.md)
- [<span data-ttu-id="30d87-125">Drawing 对象概述</span><span class="sxs-lookup"><span data-stu-id="30d87-125">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="30d87-126">使用 DrawingVisual 对象</span><span class="sxs-lookup"><span data-stu-id="30d87-126">Using DrawingVisual Objects</span></span>](../graphics-multimedia/using-drawingvisual-objects.md)
- [<span data-ttu-id="30d87-127">依赖项属性概述</span><span class="sxs-lookup"><span data-stu-id="30d87-127">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="30d87-128">Freezable 对象概述</span><span class="sxs-lookup"><span data-stu-id="30d87-128">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="30d87-129">XAML 资源</span><span class="sxs-lookup"><span data-stu-id="30d87-129">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="30d87-130">WPF 中的文档</span><span class="sxs-lookup"><span data-stu-id="30d87-130">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="30d87-131">绘制格式化文本</span><span class="sxs-lookup"><span data-stu-id="30d87-131">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
- [<span data-ttu-id="30d87-132">WPF 中的版式</span><span class="sxs-lookup"><span data-stu-id="30d87-132">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="30d87-133">数据绑定概述</span><span class="sxs-lookup"><span data-stu-id="30d87-133">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="30d87-134">导航概述</span><span class="sxs-lookup"><span data-stu-id="30d87-134">Navigation Overview</span></span>](../app-development/navigation-overview.md)
- [<span data-ttu-id="30d87-135">动画提示和技巧</span><span class="sxs-lookup"><span data-stu-id="30d87-135">Animation Tips and Tricks</span></span>](../graphics-multimedia/animation-tips-and-tricks.md)
- [<span data-ttu-id="30d87-136">演练：在 WPF 应用程序中缓存应用程序数据</span><span class="sxs-lookup"><span data-stu-id="30d87-136">Walkthrough: Caching Application Data in a WPF Application</span></span>](walkthrough-caching-application-data-in-a-wpf-application.md)
