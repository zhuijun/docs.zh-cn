---
title: 剪贴板格式无效
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: 429d1e120a0044152a358a87663eb09989f45b0e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874594"
---
# <a name="clipboard-format-is-not-valid"></a><span data-ttu-id="4e6c0-102">剪贴板格式无效</span><span class="sxs-lookup"><span data-stu-id="4e6c0-102">Clipboard format is not valid</span></span>

<span data-ttu-id="4e6c0-103">指定的剪贴板格式与正在执行的方法不兼容。</span><span class="sxs-lookup"><span data-stu-id="4e6c0-103">The specified Clipboard format is incompatible with the method being executed.</span></span> <span data-ttu-id="4e6c0-104">此错误的可能原因包括：</span><span class="sxs-lookup"><span data-stu-id="4e6c0-104">Among the possible causes for this error are:</span></span>  
  
- <span data-ttu-id="4e6c0-105">将剪贴板的 `GetText` 或 `SetText` 方法用于或以外的剪贴板格式 `vbCFText` `vbCFLink` 。</span><span class="sxs-lookup"><span data-stu-id="4e6c0-105">Using the Clipboard's `GetText` or `SetText` method with a Clipboard format other than `vbCFText` or `vbCFLink`.</span></span>  
  
- <span data-ttu-id="4e6c0-106">将剪贴板的 `GetData` 或 `SetData` 方法用于、或以外的剪贴板格式 `vbCFBitmap` `vbCFDIB` `vbCFMetafile` 。</span><span class="sxs-lookup"><span data-stu-id="4e6c0-106">Using the Clipboard's `GetData` or `SetData` method with a Clipboard format other than `vbCFBitmap`, `vbCFDIB`, or `vbCFMetafile`.</span></span>  
  
- <span data-ttu-id="4e6c0-107">`GetData` `SetData` 如果在 microsoft windows `DataObject` 中未注册剪贴板格式，则在 microsoft windows 为注册格式 ( # B0 HC000-&HFFFF) 的范围内，使用具有剪贴板格式的或方法作为已注册的格式。</span><span class="sxs-lookup"><span data-stu-id="4e6c0-107">Using the `GetData` or `SetData` methods of a `DataObject` with a Clipboard format in the range reserved by Microsoft Windows for registered formats (&HC000-&HFFFF), when that Clipboard format has not been registered with Microsoft Windows.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4e6c0-108">更正此错误</span><span class="sxs-lookup"><span data-stu-id="4e6c0-108">To correct this error</span></span>  
  
- <span data-ttu-id="4e6c0-109">删除无效的格式，并指定一个有效的格式。</span><span class="sxs-lookup"><span data-stu-id="4e6c0-109">Remove the invalid format and specify a valid one.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e6c0-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4e6c0-110">See also</span></span>

- [<span data-ttu-id="4e6c0-111">剪贴板：添加其他格式</span><span class="sxs-lookup"><span data-stu-id="4e6c0-111">Clipboard: Adding Other Formats</span></span>](/cpp/mfc/clipboard-adding-other-formats)
