---
title: 需要“Optional”
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: e212939cf814a9ac632571b2203f2f256dea61ae
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873606"
---
# <a name="optional-expected"></a>需要“Optional”

过程声明中的可选参数后跟必需的参数。 可选参数后面的每个参数都必须是可选的。  
  
 **错误 ID：** BC30202  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1. 如果需要参数，请将其移动到自变量列表中的第一个可选参数之前。  
  
2. 如果参数旨在作为可选参数，请使用 `Optional` 关键字。  
  
## <a name="see-also"></a>另请参阅

- [可选参数](../../programming-guide/language-features/procedures/optional-parameters.md)
