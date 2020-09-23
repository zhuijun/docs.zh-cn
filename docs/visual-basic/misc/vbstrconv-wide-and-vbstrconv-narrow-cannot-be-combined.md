---
title: 不能组合 VbStrConv.Wide 和 VbStrConv.Narrow
ms.date: 07/20/2015
f1_keywords:
- vbrArgument_IllegalWideNarrow
ms.assetid: a53b4e6a-36b1-4e36-b2c5-8196313ec599
ms.openlocfilehash: 7193d1f635ff877ab5d07f03584f19f5ce18138a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059363"
---
# <a name="vbstrconvwide-and-vbstrconvnarrow-cannot-be-combined"></a><span data-ttu-id="291bc-102">不能组合 VbStrConv.Wide 和 VbStrConv.Narrow</span><span class="sxs-lookup"><span data-stu-id="291bc-102">VbStrConv.Wide and VbStrConv.Narrow cannot be combined</span></span>

<span data-ttu-id="291bc-103">你的应用程序尝试组合 `VbStrConv` 枚举成员 `Wide` 和 `Narrow`，而它们是互斥的。</span><span class="sxs-lookup"><span data-stu-id="291bc-103">Your application is trying to combine the `VbStrConv` enumeration members `Wide` and `Narrow`, which are mutually exclusive.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="291bc-104">更正此错误</span><span class="sxs-lookup"><span data-stu-id="291bc-104">To correct this error</span></span>  
  
1. <span data-ttu-id="291bc-105">删除 `VbStrConv.Wide` 或 `VbStrConv.Narrow`。</span><span class="sxs-lookup"><span data-stu-id="291bc-105">Remove either `VbStrConv.Wide` or `VbStrConv.Narrow`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="291bc-106">请参阅</span><span class="sxs-lookup"><span data-stu-id="291bc-106">See also</span></span>

- <xref:System.Globalization>

- [<span data-ttu-id="291bc-107">开发全球化和本地化应用</span><span class="sxs-lookup"><span data-stu-id="291bc-107">Develop globalized and localized apps</span></span>](/visualstudio/ide/globalizing-and-localizing-applications)
