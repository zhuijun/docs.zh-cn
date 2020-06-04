---
title: 参数 BasePath 必须是一个文件夹的路径
ms.date: 07/20/2015
ms.assetid: b180ce60-ad57-41a6-a313-491d86d84cc7
ms.openlocfilehash: 5b55c1510e7a9607e71c2afb4771eb23ace2faad
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368083"
---
# <a name="argument-basepath-must-be-a-path-to-a-folder"></a>参数 BasePath 必须是一个文件夹的路径
参数 `BasePath` 必须包含文件夹的路径。 你可能会错误地解析字符串，并提供一个未被识别为有效路径的值。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
- 检查为 `BasePath` 提供的值，确保它是一个文件夹的有效路径。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.CodeDom.Compiler.TempFileCollection.BasePath%2A>
- <xref:System.Resources.ResXResourceWriter.BasePath%2A>
- <xref:System.Resources.ResXResourceReader.BasePath%2A>
- [如何：分析文件路径](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
