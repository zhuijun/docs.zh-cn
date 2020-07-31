---
title: 缓解：基于指针的触控和触笔支持
description: 了解为面向 .NET Framework 4.7 的 WPF 应用启用可选 WPF 触控/触笔堆栈的影响。
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
ms.openlocfilehash: d0c0effeaa727c615dddc3b92cdd34aafde65705
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475419"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="4b003-103">缓解：基于指针的触控和触笔支持</span><span class="sxs-lookup"><span data-stu-id="4b003-103">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="4b003-104">对于面向 .NET Framework 4.7 且在 Windows 10 创意者更新及更高版本的 Windows 上运行的 WPF 应用程序，可以启用基于 `WM_POINTER` 的可选 WPF 触控/触笔堆栈。</span><span class="sxs-lookup"><span data-stu-id="4b003-104">WPF applications that target the .NET Framework 4.7 and are running on Windows starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="4b003-105">影响</span><span class="sxs-lookup"><span data-stu-id="4b003-105">Impact</span></span>

<span data-ttu-id="4b003-106">未显式启用基于指针的触控/触笔支持的开发者应该不会看到 WPF 触控/触笔行为有任何变化。</span><span class="sxs-lookup"><span data-stu-id="4b003-106">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="4b003-107">下面介绍了可选的基于 `WM_POINTER` 的触控/触笔堆栈当前存在的已知问题：</span><span class="sxs-lookup"><span data-stu-id="4b003-107">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="4b003-108">不支持实时墨迹书写。</span><span class="sxs-lookup"><span data-stu-id="4b003-108">No support for real-time inking.</span></span>

   <span data-ttu-id="4b003-109">尽管墨迹书写和触笔插件仍可运行，但它们是在 UI 线程上进行处理，这可能会导致性能变得糟糕。</span><span class="sxs-lookup"><span data-stu-id="4b003-109">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="4b003-110">从触控/触笔事件提升到鼠标事件方面的更改导致行为发生变化。</span><span class="sxs-lookup"><span data-stu-id="4b003-110">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="4b003-111">控制行为可能不同。</span><span class="sxs-lookup"><span data-stu-id="4b003-111">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="4b003-112">拖/放行为无法正确显示触控输入反馈。</span><span class="sxs-lookup"><span data-stu-id="4b003-112">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="4b003-113">（这不会影响触笔输入。）</span><span class="sxs-lookup"><span data-stu-id="4b003-113">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="4b003-114">无法再通过触控/触笔事件启动拖/放行为。</span><span class="sxs-lookup"><span data-stu-id="4b003-114">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="4b003-115">这可能会导致应用程序无响应，直到检测到鼠标输入。</span><span class="sxs-lookup"><span data-stu-id="4b003-115">This can potentially cause the application to become unresponsive until mouse input is detected.</span></span> <span data-ttu-id="4b003-116">相反，开发者应通过鼠标事件启动拖放行为。</span><span class="sxs-lookup"><span data-stu-id="4b003-116">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a><span data-ttu-id="4b003-117">选择启用基于 WM_POINTER 的触控/触笔支持</span><span class="sxs-lookup"><span data-stu-id="4b003-117">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="4b003-118">要启用此堆栈的开发者可以在应用程序的 app.config 文件中添加下面的代码。</span><span class="sxs-lookup"><span data-stu-id="4b003-118">Developers who wish to enable this stack can add the following to their application's *app.config* file.</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="4b003-119">删除此条目或将其值设置为 `false` 可以禁用此可选堆栈。</span><span class="sxs-lookup"><span data-stu-id="4b003-119">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b003-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="4b003-120">See also</span></span>

- [<span data-ttu-id="4b003-121">应用程序兼容性</span><span class="sxs-lookup"><span data-stu-id="4b003-121">Application compatibility</span></span>](application-compatibility.md)
