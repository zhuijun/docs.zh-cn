---
title: 文件太大，无法读取到字节数组中
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: b81fc9332d5f1347404fcdd73bce72b6b09778b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363119"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a>文件太大，无法读取到字节数组中
尝试读入字节数组的文件大小超过 4 GB。 `My.Computer.FileSystem.ReadAllBytes`此方法无法读取超过此大小的文件。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
- 使用 <xref:System.IO.StreamReader> 读取文件。 有关详细信息，请参阅[.NET Framework 文件 i/o 和文件系统（Visual Basic）的基础知识](../../developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)。  
  
## <a name="see-also"></a>另请参阅

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [使用 Visual Basic 访问文件](../../developing-apps/programming/drives-directories-files/file-access.md)
- [如何：使用 StreamReader 读取文件中的文本](../../developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
