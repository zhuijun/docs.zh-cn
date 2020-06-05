---
title: <code>
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: aa65fed863718f1f00b510f82051a13e764e1b23
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400134"
---
# <a name="code-visual-basic"></a><span data-ttu-id="ba217-101">\<code> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba217-101">\<code> (Visual Basic)</span></span>
<span data-ttu-id="ba217-102">指示文本为多行代码。</span><span class="sxs-lookup"><span data-stu-id="ba217-102">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba217-103">语法</span><span class="sxs-lookup"><span data-stu-id="ba217-103">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba217-104">参数</span><span class="sxs-lookup"><span data-stu-id="ba217-104">Parameters</span></span>  
 `content`  
 <span data-ttu-id="ba217-105">要标记为代码的文本。</span><span class="sxs-lookup"><span data-stu-id="ba217-105">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba217-106">备注</span><span class="sxs-lookup"><span data-stu-id="ba217-106">Remarks</span></span>  
 <span data-ttu-id="ba217-107">使用 `<code>` 标记将多行指示为代码。</span><span class="sxs-lookup"><span data-stu-id="ba217-107">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="ba217-108">用于 [\<c>](c.md) 指示应将说明内的文本标记为代码。</span><span class="sxs-lookup"><span data-stu-id="ba217-108">Use [\<c>](c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="ba217-109">使用 [-doc](../../reference/command-line-compiler/doc.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="ba217-109">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba217-110">示例</span><span class="sxs-lookup"><span data-stu-id="ba217-110">Example</span></span>  
 <span data-ttu-id="ba217-111">此示例使用 \<code> 标记来包含用于使用字段的示例代码 `ID` 。</span><span class="sxs-lookup"><span data-stu-id="ba217-111">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ba217-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ba217-112">See also</span></span>

- [<span data-ttu-id="ba217-113">XML 注释标记</span><span class="sxs-lookup"><span data-stu-id="ba217-113">XML Comment Tags</span></span>](index.md)
