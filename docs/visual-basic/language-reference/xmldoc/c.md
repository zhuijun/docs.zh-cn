---
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: c8ba03d9cc01c4751d15c01530c6cbf7d499dc3b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400158"
---
# <a name="c-visual-basic"></a><span data-ttu-id="be1ad-101">\<c> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be1ad-101">\<c> (Visual Basic)</span></span>
<span data-ttu-id="be1ad-102">指示说明中的文本为代码。</span><span class="sxs-lookup"><span data-stu-id="be1ad-102">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be1ad-103">语法</span><span class="sxs-lookup"><span data-stu-id="be1ad-103">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="be1ad-104">参数</span><span class="sxs-lookup"><span data-stu-id="be1ad-104">Parameters</span></span>  
  
|<span data-ttu-id="be1ad-105">参数</span><span class="sxs-lookup"><span data-stu-id="be1ad-105">Parameter</span></span>|<span data-ttu-id="be1ad-106">说明</span><span class="sxs-lookup"><span data-stu-id="be1ad-106">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="be1ad-107">要指示为代码的文本。</span><span class="sxs-lookup"><span data-stu-id="be1ad-107">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be1ad-108">备注</span><span class="sxs-lookup"><span data-stu-id="be1ad-108">Remarks</span></span>  
 <span data-ttu-id="be1ad-109">`<c>`标记提供了一种方法，用于指示应将说明中的文本标记为代码。</span><span class="sxs-lookup"><span data-stu-id="be1ad-109">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="be1ad-110">用于将 [\<code>](code.md) 多行指示为代码。</span><span class="sxs-lookup"><span data-stu-id="be1ad-110">Use [\<code>](code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="be1ad-111">使用 [-doc](../../reference/command-line-compiler/doc.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="be1ad-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be1ad-112">示例</span><span class="sxs-lookup"><span data-stu-id="be1ad-112">Example</span></span>  
 <span data-ttu-id="be1ad-113">此示例使用 " `<c>` 摘要" 部分中的标记指示该 `Counter` 为代码。</span><span class="sxs-lookup"><span data-stu-id="be1ad-113">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="be1ad-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="be1ad-114">See also</span></span>

- [<span data-ttu-id="be1ad-115">XML 注释标记</span><span class="sxs-lookup"><span data-stu-id="be1ad-115">XML Comment Tags</span></span>](index.md)
