---
title: 无法读取分隔字段，因为当 EscapeQuotes 设置为 True 时，双引号不是合法的分隔符
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: cd2dd4226296ecd210a1e72a7b7fb593874b0008
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398469"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a><span data-ttu-id="f7f5a-102">无法读取分隔字段，因为当 EscapeQuotes 设置为 True 时，双引号不是合法的分隔符</span><span class="sxs-lookup"><span data-stu-id="f7f5a-102">Unable to read delimited fields because a double quote is not a legal delimiter when EscapeQuotes is set to True</span></span>
<span data-ttu-id="f7f5a-103">`TextFieldParser` 无法从文件中读取，因为引号 (") 以分隔符形式提供，且 `EscapeQuotes` 设置为 `True`。</span><span class="sxs-lookup"><span data-stu-id="f7f5a-103">The `TextFieldParser` cannot read from the file because a quotation mark (") has been supplied as the delimiter and `EscapeQuotes` is set to `True`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f7f5a-104">更正此错误</span><span class="sxs-lookup"><span data-stu-id="f7f5a-104">To correct this error</span></span>  
  
- <span data-ttu-id="f7f5a-105">将 `EscapeQuotes` 设置为 `False`。</span><span class="sxs-lookup"><span data-stu-id="f7f5a-105">Set `EscapeQuotes` to `False`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7f5a-106">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f7f5a-106">See also</span></span>

- [<span data-ttu-id="f7f5a-107">TextFieldParser.SetDelimiters 方法</span><span class="sxs-lookup"><span data-stu-id="f7f5a-107">TextFieldParser.SetDelimiters Method</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A)
- [<span data-ttu-id="f7f5a-108">TextFieldParser.Delimiters 属性</span><span class="sxs-lookup"><span data-stu-id="f7f5a-108">TextFieldParser.Delimiters Property</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A)
- [<span data-ttu-id="f7f5a-109">如何：读取逗号分隔的文本文件</span><span class="sxs-lookup"><span data-stu-id="f7f5a-109">How to: Read From Comma-Delimited Text Files</span></span>](../developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="f7f5a-110">TextFieldParser Object</span><span class="sxs-lookup"><span data-stu-id="f7f5a-110">TextFieldParser Object</span></span>](../language-reference/objects/textfieldparser-object.md)
