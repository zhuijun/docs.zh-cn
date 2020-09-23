---
title: 不能组合 SimplifiedChinese 和 VbStrConv.TraditionalChinese
ms.date: 07/20/2015
f1_keywords:
- vbrArgument_StrConvSCandTC
ms.assetid: d8e6a11b-f549-43b5-8337-0594340e1325
ms.openlocfilehash: 512651add89de23b35512e736dbf74f0891c995a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91060479"
---
# <a name="simplifiedchinese-and-vbstrconvtraditionalchinese-cannot-be-combined"></a><span data-ttu-id="fa92b-102">不能组合 SimplifiedChinese 和 VbStrConv.TraditionalChinese</span><span class="sxs-lookup"><span data-stu-id="fa92b-102">SimplifiedChinese and VbStrConv.TraditionalChinese cannot be combined</span></span>

<span data-ttu-id="fa92b-103">应用程序尝试组合 `VbStrConv` 枚举成员 `SimplifiedChinese` 和 `TraditionalChinese`，而它们是互斥的。</span><span class="sxs-lookup"><span data-stu-id="fa92b-103">Your application is attempting to combine the `VbStrConv` enumeration members `SimplifiedChinese` and `TraditionalChinese`, which are mutually exclusive.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fa92b-104">更正此错误</span><span class="sxs-lookup"><span data-stu-id="fa92b-104">To correct this error</span></span>  
  
- <span data-ttu-id="fa92b-105">删除 `VbStrConv.SimplifiedChinese` 或 `VbStrConv.TraditionalChinese`。</span><span class="sxs-lookup"><span data-stu-id="fa92b-105">Remove either `VbStrConv.SimplifiedChinese` or `VbStrConv.TraditionalChinese`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa92b-106">请参阅</span><span class="sxs-lookup"><span data-stu-id="fa92b-106">See also</span></span>

- <xref:System.Globalization>

- [<span data-ttu-id="fa92b-107">开发全球化和本地化应用</span><span class="sxs-lookup"><span data-stu-id="fa92b-107">Develop globalized and localized apps</span></span>](/visualstudio/ide/globalizing-and-localizing-applications)
