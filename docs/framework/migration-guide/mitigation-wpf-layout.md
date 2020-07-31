---
title: 缓解：WPF 布局
description: 了解如何缓解由 WPF 控件布局的更改导致的问题（例如，将对象移动到一个像素的位置）。
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: e4e4612f7b39eefbf0e76ac86c8eb644c257ba75
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475341"
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="c0935-103">缓解：WPF 布局</span><span class="sxs-lookup"><span data-stu-id="c0935-103">Mitigation: WPF Layout</span></span>
<span data-ttu-id="c0935-104">WPF 控件的布局可能稍有变化。</span><span class="sxs-lookup"><span data-stu-id="c0935-104">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="c0935-105">影响</span><span class="sxs-lookup"><span data-stu-id="c0935-105">Impact</span></span>  
 <span data-ttu-id="c0935-106">此更改的结果是：</span><span class="sxs-lookup"><span data-stu-id="c0935-106">As a result of this change:</span></span>  
  
- <span data-ttu-id="c0935-107">元素的宽度或高度最多可以扩大或收缩一个像素。</span><span class="sxs-lookup"><span data-stu-id="c0935-107">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
- <span data-ttu-id="c0935-108">对象的位置最多可以移动一个像素。</span><span class="sxs-lookup"><span data-stu-id="c0935-108">The placement of an object can move by at most one pixel.</span></span>  
  
- <span data-ttu-id="c0935-109">居中的元素最多可以垂直或水平地偏离中心一个像素。</span><span class="sxs-lookup"><span data-stu-id="c0935-109">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="c0935-110">默认情况下，仅对面向 .NET Framework 4.6 的应用启用此新布局。</span><span class="sxs-lookup"><span data-stu-id="c0935-110">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="c0935-111">缓解</span><span class="sxs-lookup"><span data-stu-id="c0935-111">Mitigation</span></span>  
 <span data-ttu-id="c0935-112">由于这种修改往往会消除高 DPI 处 WPF 控件的右侧或底部剪辑，因此面向早期版本的 .NET framework 但在.NET Framework 4.6 上运行的应用可以通过将下面的行添加到 app.config 文件的 `<runtime>` 部分来选择加入此新行为：</span><span class="sxs-lookup"><span data-stu-id="c0935-112">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="c0935-113">面向 .NET Framework 4.6 但希望 WPF 控件使用之前的布局算法来呈现的应用可以通过将下面的行添加到 app.config 文件的 `<runtime>` 部分来执行此操作：</span><span class="sxs-lookup"><span data-stu-id="c0935-113">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="c0935-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="c0935-114">See also</span></span>

- [<span data-ttu-id="c0935-115">应用程序兼容性</span><span class="sxs-lookup"><span data-stu-id="c0935-115">Application compatibility</span></span>](application-compatibility.md)
