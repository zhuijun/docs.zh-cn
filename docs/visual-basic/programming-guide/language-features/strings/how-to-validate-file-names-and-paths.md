---
title: 如何：验证文件名和路径
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: 3b4695dfbcaf05c73bd53af5be7a49d081eb8e47
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410575"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>如何：在 Visual Basic 中验证文件名和路径
此示例返回一个 `Boolean` 值，该值指示字符串是否表示文件名或路径。 验证检查名称是否包含文件系统不允许使用的字符。  
  
## <a name="example"></a>示例  
 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 此示例不检查名称是否错误地放置了冒号或没有名称的目录，或者名称长度是否超过了系统定义的最大长度。 它也不会检查应用程序是否有权访问具有指定名称的文件系统资源。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [验证字符串 (Visual Basic)](validating-strings.md)
