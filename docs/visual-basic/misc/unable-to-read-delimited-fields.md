---
title: 无法读取分隔字段，因为当 EscapeQuotes 设置为 True 时，双引号不是合法的分隔符
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: 29682edb78b848897ac2999f2d84dc1a9c1a3367
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100347"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a><span data-ttu-id="e00ca-102">无法读取分隔字段，因为当 EscapeQuotes 设置为 True 时，双引号不是合法的分隔符</span><span class="sxs-lookup"><span data-stu-id="e00ca-102">Unable to read delimited fields because a double quote is not a legal delimiter when EscapeQuotes is set to True</span></span>

<span data-ttu-id="e00ca-103">`TextFieldParser` 无法从文件中读取，因为引号 (") 以分隔符形式提供，且 `EscapeQuotes` 设置为 `True`。</span><span class="sxs-lookup"><span data-stu-id="e00ca-103">The `TextFieldParser` cannot read from the file because a quotation mark (") has been supplied as the delimiter and `EscapeQuotes` is set to `True`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e00ca-104">更正此错误</span><span class="sxs-lookup"><span data-stu-id="e00ca-104">To correct this error</span></span>  
  
- <span data-ttu-id="e00ca-105">将 `EscapeQuotes` 设置为 `False`。</span><span class="sxs-lookup"><span data-stu-id="e00ca-105">Set `EscapeQuotes` to `False`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e00ca-106">请参阅</span><span class="sxs-lookup"><span data-stu-id="e00ca-106">See also</span></span>

- [<span data-ttu-id="e00ca-107">TextFieldParser.SetDelimiters 方法</span><span class="sxs-lookup"><span data-stu-id="e00ca-107">TextFieldParser.SetDelimiters Method</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A)
- [<span data-ttu-id="e00ca-108">TextFieldParser.Delimiters 属性</span><span class="sxs-lookup"><span data-stu-id="e00ca-108">TextFieldParser.Delimiters Property</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A)
- [<span data-ttu-id="e00ca-109">如何：读取逗号分隔的文本文件</span><span class="sxs-lookup"><span data-stu-id="e00ca-109">How to: Read From Comma-Delimited Text Files</span></span>](../developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="e00ca-110">TextFieldParser Object</span><span class="sxs-lookup"><span data-stu-id="e00ca-110">TextFieldParser Object</span></span>](../language-reference/objects/textfieldparser-object.md)
