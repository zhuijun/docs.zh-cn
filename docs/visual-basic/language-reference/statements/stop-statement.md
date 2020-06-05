---
title: Stop 语句
ms.date: 07/20/2015
f1_keywords:
- vb.Stop
helpviewer_keywords:
- breakpoints, Stop statements
- Stop statements [Visual Basic], syntax
- Stop statements [Visual Basic]
- execution [Visual Basic], suspending
- processing, interrupting
- processes, interrupting
- execution [Visual Basic], stopping
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
ms.openlocfilehash: 2ef1e2f9045e5509e11557c9fdaf3edd2786b72c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404221"
---
# <a name="stop-statement-visual-basic"></a>Stop 语句 (Visual Basic)
挂起执行。  
  
## <a name="syntax"></a>语法  
  
```vb  
Stop  
```  
  
## <a name="remarks"></a>备注  
 您可以 `Stop` 在过程中的任何位置放置语句来挂起执行。 使用 `Stop` 语句与在代码中设置断点类似。  
  
 `Stop`语句暂停执行，但与 `End` 此不同，它不会关闭任何文件或清除任何变量，除非在已编译的可执行（.exe）文件中遇到。  
  
> [!NOTE]
> 如果 `Stop` 在集成开发环境（IDE）外部运行的代码中遇到语句，则将调用调试器。 无论代码是在调试模式下编译还是在发布模式下编译，都是如此。  
  
## <a name="example"></a>示例  
 此示例使用 `Stop` 语句通过循环挂起每个迭代的执行 `For...Next` 。  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a>另请参阅

- [End 语句](end-statement.md)
