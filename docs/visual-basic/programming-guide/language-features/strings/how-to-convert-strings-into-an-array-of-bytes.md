---
title: 如何：将字符串转换为字节数组
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- arrays [Visual Basic], converting strings to
- byte arrays
- examples [Visual Basic], string conversion
- arrays [Visual Basic], byte arrays
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
ms.openlocfilehash: 3ee1d5e1e31054f23f4510c7a112d8e3473bcdd7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410601"
---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a>如何：在 Visual Basic 中将字符串转换为字节数组
本主题演示如何将字符串转换为字节数组。  
  
## <a name="example"></a>示例  
 此示例使用 <xref:System.Text.Encoding.GetBytes%2A> encoding 类的方法 <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> 将字符串转换为字节数组。  
  
 [!code-vb[VbVbalrStrings#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#74)]  
  
 可以从多个编码选项中进行选择，以将字符串转换为字节数组：  
  
- <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>：获取 ASCII （7位）字符集的编码。  
  
- <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>：获取使用大 endian 字节顺序的 UTF-16 格式的编码。  
  
- <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>：获取系统的当前 ANSI 代码页的编码。  
  
- <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>：获取使用小 endian 字节顺序的 UTF-16 格式的编码。  
  
- <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>：使用小字节序字节顺序获取 UTF-32 格式的编码。  
  
- <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>：获取 UTF-7 格式的编码。  
  
- <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>：获取 UTF-8 格式的编码。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetBytes%2A>
- [如何：在 Visual Basic 中将字节数组转换为字符串](how-to-convert-an-array-of-bytes-into-a-string.md)
