---
title: TextFieldParser 不支持包含空格的注释标记
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_WhitespaceInToken
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
ms.openlocfilehash: 51dc2b82d7f04c652e18173b8450b65c15ee6ec2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411891"
---
# <a name="textfieldparser-does-not-support-comment-tokens-that-contain-white-space"></a>TextFieldParser 不支持包含空格的注释标记
提供了包含空格的注释标记。 `TextFieldParser` 不支持包含空格的注释标记，除非空格出现在标记的开头。 出现在标记开头的空格将被忽略。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
- 提供正确的注释标记。  
  
## <a name="see-also"></a>另请参阅

- [TextFieldParser.CommentTokens 属性](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A)
- [使用 TextFieldParser 对象分析文本文件](../developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [TextFieldParser Object](../language-reference/objects/textfieldparser-object.md)
