---
title: 错误的文件名或文件号
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 11e866d9a8da7ad1ecc5f788fc31f6ac96d32f2c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409824"
---
# <a name="bad-file-name-or-number"></a>错误的文件名或文件号
尝试访问指定的文件时出错。 此错误的可能原因包括：  
  
- 语句引用的文件具有未在语句中指定 `FileOpen` 或在语句中指定的、 `FileOpen` 但随后已关闭的文件。  
  
- 语句引用的文件的数量超出了文件编号范围。  
  
- 语句引用的文件名或编号无效。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1. 请确保在语句中指定了文件名 `FileOpen` 。 请注意，如果调用 `FileClose` 不带参数的语句，则可能会无意中关闭所有打开的文件。  
  
2. 如果你的代码生成了文件号算法，请确保数字有效。  
  
3. 检查文件名，确保它们符合操作系统约定。  
  
## <a name="see-also"></a>另请参阅

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [Visual Basic 命名约定](../../programming-guide/program-structure/naming-conventions.md)
