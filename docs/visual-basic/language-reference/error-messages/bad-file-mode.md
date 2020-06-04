---
title: 错误的文件模式
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: 534ea2d8316dc29cace798c5ad9b7697a290026f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409864"
---
# <a name="bad-file-mode"></a>错误的文件模式
用于操作文件内容的语句必须适合于打开该文件的模式。 可能的原因包括：  
  
- `FilePutObject`或 `FileGetObject` 语句指定顺序文件。  
  
- `Print`语句指定了一个打开的文件，该文件用于访问模式，而不是 `Output` 或 `Append` 。  
  
- `Input`语句指定为访问模式打开的文件，而不是`Input`  
  
- 尝试写入只读文件。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
- 请确保 `FilePutObject` 和 `FileGetObject` 仅引用打开的 `Random` 或访问的文件 `Binary` 。  
  
- 请确保 `Print` 为 `Output` 或访问模式指定打开的文件 `Append` 。 否则，请使用不同的语句将数据放置在文件中，或在适当的模式下重新打开文件。  
  
- 请确保 `Input` 指定一个打开的文件 `Input` 。 否则，请使用不同的语句将数据放置在文件中，或在适当的模式下重新打开文件。  
  
- 如果要写入只读文件，请更改该文件的读/写状态，或不要尝试写入该文件。  
  
- 使用 `My.Computer.FileSystem` 对象中的可用功能。  
  
## <a name="see-also"></a>另请参阅

- <xref:Microsoft.VisualBasic.FileSystem>
- [疑难解答：读取和写入文本文件](../../developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
