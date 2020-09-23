---
title: TextFieldParser 不支持包含空格的注释标记
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_WhitespaceInToken
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
ms.openlocfilehash: 825f999f8eab3563dd77039ef19ae5e329bb4240
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078497"
---
# <a name="textfieldparser-does-not-support-comment-tokens-that-contain-white-space"></a><span data-ttu-id="3eec7-102">TextFieldParser 不支持包含空格的注释标记</span><span class="sxs-lookup"><span data-stu-id="3eec7-102">TextFieldParser does not support comment tokens that contain white space</span></span>

<span data-ttu-id="3eec7-103">提供了包含空格的注释标记。</span><span class="sxs-lookup"><span data-stu-id="3eec7-103">A comment token that contains white space has been supplied.</span></span> <span data-ttu-id="3eec7-104">`TextFieldParser` 不支持包含空格的注释标记，除非空格出现在标记的开头。</span><span class="sxs-lookup"><span data-stu-id="3eec7-104">The `TextFieldParser` does not support comment tokens that contain white space unless the white space occurs at the beginning of the token.</span></span> <span data-ttu-id="3eec7-105">出现在标记开头的空格将被忽略。</span><span class="sxs-lookup"><span data-stu-id="3eec7-105">White space occurring at the beginning of a token is ignored.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3eec7-106">更正此错误</span><span class="sxs-lookup"><span data-stu-id="3eec7-106">To correct this error</span></span>  
  
- <span data-ttu-id="3eec7-107">提供正确的注释标记。</span><span class="sxs-lookup"><span data-stu-id="3eec7-107">Supply a correct comment token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eec7-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="3eec7-108">See also</span></span>

- [<span data-ttu-id="3eec7-109">TextFieldParser.CommentTokens 属性</span><span class="sxs-lookup"><span data-stu-id="3eec7-109">TextFieldParser.CommentTokens Property</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A)
- [<span data-ttu-id="3eec7-110">使用 TextFieldParser 对象分析文本文件</span><span class="sxs-lookup"><span data-stu-id="3eec7-110">Parsing Text Files with the TextFieldParser Object</span></span>](../developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="3eec7-111">TextFieldParser Object</span><span class="sxs-lookup"><span data-stu-id="3eec7-111">TextFieldParser Object</span></span>](../language-reference/objects/textfieldparser-object.md)
