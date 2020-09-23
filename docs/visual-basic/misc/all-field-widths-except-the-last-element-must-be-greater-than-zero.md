---
title: 所有字段宽度（除了最后一个元素外）都必须大于零
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_FieldWidthsMustPositive
ms.assetid: 41d8c661-a749-4c89-be56-905c6e7c3c9d
ms.openlocfilehash: 4fb40e5f2b458fbbd0bfdb329f75250e70fd7e28
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91083912"
---
# <a name="all-field-widths-except-the-last-element-must-be-greater-than-zero"></a><span data-ttu-id="d1ef3-102">所有字段宽度（除了最后一个元素外）都必须大于零</span><span class="sxs-lookup"><span data-stu-id="d1ef3-102">All field widths, except the last element, must be greater than zero</span></span>

<span data-ttu-id="d1ef3-103">所有字段宽度（除了最后一个元素外）都必须大于零。</span><span class="sxs-lookup"><span data-stu-id="d1ef3-103">All field widths, except the last element, must be greater than zero.</span></span> <span data-ttu-id="d1ef3-104">最后一个元素的字段宽度小于或等于零表示最后一个字段的长度是可变的。</span><span class="sxs-lookup"><span data-stu-id="d1ef3-104">A field width less than or equal to zero in the last element indicates the last field is of variable length.</span></span>  
  
 <span data-ttu-id="d1ef3-105">操作已失败，因为最后一个元素以外的某个字段宽度被设置为等于或小于零。</span><span class="sxs-lookup"><span data-stu-id="d1ef3-105">The operation has failed because a field width other than the last element is set to zero or less.</span></span> <span data-ttu-id="d1ef3-106">可将小于或等于零的字段宽度用作最后一个元素以指示最后一个字段的长度可变，但不能将它用作任何其他元素。</span><span class="sxs-lookup"><span data-stu-id="d1ef3-106">A field width less than or equal to zero can be used as the last element to indicate that the last field is of variable length, but it cannot be used as any other element.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d1ef3-107">更正此错误</span><span class="sxs-lookup"><span data-stu-id="d1ef3-107">To correct this error</span></span>  
  
- <span data-ttu-id="d1ef3-108">将字段宽度设置为正确的长度。</span><span class="sxs-lookup"><span data-stu-id="d1ef3-108">Set the field width to the correct length.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1ef3-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="d1ef3-109">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths>
- [<span data-ttu-id="d1ef3-110">如何：读取固定宽度的文本文件</span><span class="sxs-lookup"><span data-stu-id="d1ef3-110">How to: Read From Fixed-width Text Files</span></span>](../developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="d1ef3-111">TextFieldParser Object</span><span class="sxs-lookup"><span data-stu-id="d1ef3-111">TextFieldParser Object</span></span>](../language-reference/objects/textfieldparser-object.md)
