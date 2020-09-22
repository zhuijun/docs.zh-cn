---
title: <code>
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: d058663213cf02f2142bff740aeec1b60791362c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873034"
---
# <a name="code-visual-basic"></a><span data-ttu-id="f2643-101">\<code> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2643-101">\<code> (Visual Basic)</span></span>

<span data-ttu-id="f2643-102">指示文本为多行代码。</span><span class="sxs-lookup"><span data-stu-id="f2643-102">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2643-103">语法</span><span class="sxs-lookup"><span data-stu-id="f2643-103">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2643-104">参数</span><span class="sxs-lookup"><span data-stu-id="f2643-104">Parameters</span></span>  

 `content`  
 <span data-ttu-id="f2643-105">要标记为代码的文本。</span><span class="sxs-lookup"><span data-stu-id="f2643-105">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2643-106">备注</span><span class="sxs-lookup"><span data-stu-id="f2643-106">Remarks</span></span>  

 <span data-ttu-id="f2643-107">使用 `<code>` 标记将多行指示为代码。</span><span class="sxs-lookup"><span data-stu-id="f2643-107">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="f2643-108">用于 [\<c>](c.md) 指示应将说明内的文本标记为代码。</span><span class="sxs-lookup"><span data-stu-id="f2643-108">Use [\<c>](c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="f2643-109">使用 [-doc](../../reference/command-line-compiler/doc.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="f2643-109">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2643-110">示例</span><span class="sxs-lookup"><span data-stu-id="f2643-110">Example</span></span>  

 <span data-ttu-id="f2643-111">此示例使用 \<code> 标记来包含用于使用字段的示例代码 `ID` 。</span><span class="sxs-lookup"><span data-stu-id="f2643-111">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f2643-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="f2643-112">See also</span></span>

- [<span data-ttu-id="f2643-113">XML 注释标记</span><span class="sxs-lookup"><span data-stu-id="f2643-113">XML Comment Tags</span></span>](index.md)
