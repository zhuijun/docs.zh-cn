---
title: 'PrepareHeaderDrag 方法 (GridViewHeaderRowPresenter) '
description: 了解名为 PrepareHeaderDrag 的专用 WPF 方法。
ms.date: 09/25/2020
ms.technology: dotnet-wpf
topic_type:
- apiref
api_name:
- System.Windows.Controls.GridViewHeaderRowPresenter.PrepareHeaderDrag
api_location:
- PresentationFramework.dll
api_type:
- Assembly
ms.openlocfilehash: 6d806b8a50de3234cd04198f4ab86621dcd6ede1
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877778"
---
# <a name="prepareheaderdrag-method"></a><span data-ttu-id="cdb16-103">PrepareHeaderDrag 方法</span><span class="sxs-lookup"><span data-stu-id="cdb16-103">PrepareHeaderDrag method</span></span>

<span data-ttu-id="cdb16-104">准备要重新排序的指定列标题。</span><span class="sxs-lookup"><span data-stu-id="cdb16-104">Prepares the specified column header for reordering.</span></span>

```csharp
private void PrepareHeaderDrag(GridViewColumnHeader header, Point pos, Point relativePos, bool cancelInvoke)
```

> [!WARNING]
> <span data-ttu-id="cdb16-105">此方法是专用的，不应在代码中直接使用。</span><span class="sxs-lookup"><span data-stu-id="cdb16-105">This method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="cdb16-106">在任何情况下，Microsoft 不支持在生产应用程序中使用此方法。</span><span class="sxs-lookup"><span data-stu-id="cdb16-106">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="cdb16-107">参数</span><span class="sxs-lookup"><span data-stu-id="cdb16-107">Parameters</span></span>

<span data-ttu-id="cdb16-108">`header` <xref:System.Windows.Controls.GridViewColumnHeader></span><span class="sxs-lookup"><span data-stu-id="cdb16-108">`header` <xref:System.Windows.Controls.GridViewColumnHeader></span></span>\
<span data-ttu-id="cdb16-109">准备重新排序的列标题。</span><span class="sxs-lookup"><span data-stu-id="cdb16-109">The column header to prepare for reordering.</span></span>

<span data-ttu-id="cdb16-110">`pos` <xref:System.Windows.Point></span><span class="sxs-lookup"><span data-stu-id="cdb16-110">`pos` <xref:System.Windows.Point></span></span>\
<span data-ttu-id="cdb16-111">相对于的位置， <xref:System.Windows.Controls.GridViewHeaderRowPresenter> 拖动从此处开始。</span><span class="sxs-lookup"><span data-stu-id="cdb16-111">The position, relative to <xref:System.Windows.Controls.GridViewHeaderRowPresenter>, where the dragging starts.</span></span>

<span data-ttu-id="cdb16-112">`relativePos` <xref:System.Windows.Point></span><span class="sxs-lookup"><span data-stu-id="cdb16-112">`relativePos` <xref:System.Windows.Point></span></span>\
<span data-ttu-id="cdb16-113">相对于的位置， `header` 拖动从此处开始。</span><span class="sxs-lookup"><span data-stu-id="cdb16-113">The position, relative to `header`, where the dragging starts.</span></span>

<span data-ttu-id="cdb16-114">`cancelInvoke` <xref:System.Boolean></span><span class="sxs-lookup"><span data-stu-id="cdb16-114">`cancelInvoke` <xref:System.Boolean></span></span>\
<span data-ttu-id="cdb16-115">`true` 如果取消重新排序，则为;否则为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="cdb16-115">`true` to cancel the reordering; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="cdb16-116">要求</span><span class="sxs-lookup"><span data-stu-id="cdb16-116">Requirements</span></span>

<span data-ttu-id="cdb16-117">**命名空间：** <xref:System.Windows.Controls></span><span class="sxs-lookup"><span data-stu-id="cdb16-117">**Namespace:** <xref:System.Windows.Controls></span></span>

<span data-ttu-id="cdb16-118">**程序集：** PresentationFramework.dll</span><span class="sxs-lookup"><span data-stu-id="cdb16-118">**Assembly:** PresentationFramework.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="cdb16-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="cdb16-119">See also</span></span>

- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
