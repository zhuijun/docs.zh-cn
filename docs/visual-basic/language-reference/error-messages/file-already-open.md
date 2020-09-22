---
title: 文件已打开
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 97f9e13e6802e793f7c7baf1f03ec51205eb6d42
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874175"
---
# <a name="file-already-open"></a>文件已打开

有时，必须先关闭文件，然后才能 `FileOpen` 进行其他或其他操作。 此错误的可能原因包括：  
  
- `FileOpen`为已打开的文件执行了顺序输出模式操作  
  
- 语句引用打开的文件。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1. 在执行语句前关闭文件。  
  
## <a name="see-also"></a>另请参阅

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
