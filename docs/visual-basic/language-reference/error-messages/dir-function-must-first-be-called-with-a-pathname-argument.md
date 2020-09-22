---
title: 必须首先用一个“PathName”自变量调用“Dir”函数
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 1064a44f7c266b9dcce05dfddedef6bb1e919999
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874457"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a>必须首先用一个“PathName”自变量调用“Dir”函数

对函数的初始调用 `Dir` 不包含 `PathName` 参数。 对的第一次调用 `Dir` 必须包含 `PathName` ，但对的后续调用 `Dir` 不需要包含参数来检索下一项。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1. `PathName`在函数调用中提供参数。  
  
## <a name="see-also"></a>另请参阅

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
