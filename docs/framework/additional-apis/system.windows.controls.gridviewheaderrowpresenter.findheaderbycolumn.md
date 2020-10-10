---
title: 'FindHeaderByColumn 方法 (GridViewHeaderRowPresenter) '
description: 了解名为 FindHeaderByColumn 的专用 WPF 方法。
ms.date: 09/25/2020
ms.technology: dotnet-wpf
topic_type:
- apiref
api_name:
- System.Windows.Controls.GridViewHeaderRowPresenter.FindHeaderByColumn
api_location:
- PresentationFramework.dll
api_type:
- Assembly
ms.openlocfilehash: 88ed2928f86602d1078488354de6d5267c0311f5
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877781"
---
# <a name="findheaderbycolumn-method"></a><span data-ttu-id="ef4c5-103">FindHeaderByColumn 方法</span><span class="sxs-lookup"><span data-stu-id="ef4c5-103">FindHeaderByColumn method</span></span>

<span data-ttu-id="ef4c5-104">在可视化树中查找指定列的列标题。</span><span class="sxs-lookup"><span data-stu-id="ef4c5-104">Finds the column header for the specified column in the visual tree.</span></span>

```csharp
private GridViewColumnHeader FindHeaderByColumn(GridViewColumn column)
```

> [!WARNING]
> <span data-ttu-id="ef4c5-105">此方法是专用的，不应在代码中直接使用。</span><span class="sxs-lookup"><span data-stu-id="ef4c5-105">This method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="ef4c5-106">在任何情况下，Microsoft 不支持在生产应用程序中使用此方法。</span><span class="sxs-lookup"><span data-stu-id="ef4c5-106">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="ef4c5-107">参数</span><span class="sxs-lookup"><span data-stu-id="ef4c5-107">Parameters</span></span>

<span data-ttu-id="ef4c5-108">`column` <xref:System.Windows.Controls.GridViewColumn></span><span class="sxs-lookup"><span data-stu-id="ef4c5-108">`column` <xref:System.Windows.Controls.GridViewColumn></span></span>\
<span data-ttu-id="ef4c5-109">应找到并返回其标头的列。</span><span class="sxs-lookup"><span data-stu-id="ef4c5-109">The column whose header should be found and returned.</span></span>

## <a name="return-value"></a><span data-ttu-id="ef4c5-110">返回值</span><span class="sxs-lookup"><span data-stu-id="ef4c5-110">Return value</span></span>

<xref:System.Windows.Controls.GridViewColumnHeader>\
<span data-ttu-id="ef4c5-111">指定列的标头， `null` 如果指定列不存在，则为。</span><span class="sxs-lookup"><span data-stu-id="ef4c5-111">The header of the specified column, or `null` if the specified column doesn't exist.</span></span>

## <a name="requirements"></a><span data-ttu-id="ef4c5-112">要求</span><span class="sxs-lookup"><span data-stu-id="ef4c5-112">Requirements</span></span>

<span data-ttu-id="ef4c5-113">**命名空间：** <xref:System.Windows.Controls></span><span class="sxs-lookup"><span data-stu-id="ef4c5-113">**Namespace:** <xref:System.Windows.Controls></span></span>

<span data-ttu-id="ef4c5-114">**程序集：** PresentationFramework.dll</span><span class="sxs-lookup"><span data-stu-id="ef4c5-114">**Assembly:** PresentationFramework.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="ef4c5-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="ef4c5-115">See also</span></span>

- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
