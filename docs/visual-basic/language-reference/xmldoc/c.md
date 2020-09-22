---
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 969df339eb766d2edb444ab5626af4e69accddba
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871698"
---
# <a name="c-visual-basic"></a><span data-ttu-id="d4b33-101">\<c> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4b33-101">\<c> (Visual Basic)</span></span>

<span data-ttu-id="d4b33-102">指示说明中的文本为代码。</span><span class="sxs-lookup"><span data-stu-id="d4b33-102">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4b33-103">语法</span><span class="sxs-lookup"><span data-stu-id="d4b33-103">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4b33-104">参数</span><span class="sxs-lookup"><span data-stu-id="d4b33-104">Parameters</span></span>  
  
|<span data-ttu-id="d4b33-105">参数</span><span class="sxs-lookup"><span data-stu-id="d4b33-105">Parameter</span></span>|<span data-ttu-id="d4b33-106">描述</span><span class="sxs-lookup"><span data-stu-id="d4b33-106">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="d4b33-107">要指示为代码的文本。</span><span class="sxs-lookup"><span data-stu-id="d4b33-107">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4b33-108">备注</span><span class="sxs-lookup"><span data-stu-id="d4b33-108">Remarks</span></span>  

 <span data-ttu-id="d4b33-109">使用 `<c>` 标记可以指示应将说明内的文本标记为代码。</span><span class="sxs-lookup"><span data-stu-id="d4b33-109">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="d4b33-110">使用 [\<code>](code.md) 指示作为代码的多行文本。</span><span class="sxs-lookup"><span data-stu-id="d4b33-110">Use [\<code>](code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="d4b33-111">使用 [-doc](../../reference/command-line-compiler/doc.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="d4b33-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4b33-112">示例</span><span class="sxs-lookup"><span data-stu-id="d4b33-112">Example</span></span>  

 <span data-ttu-id="d4b33-113">此示例使用 " `<c>` 摘要" 部分中的标记指示该 `Counter` 为代码。</span><span class="sxs-lookup"><span data-stu-id="d4b33-113">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d4b33-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d4b33-114">See also</span></span>

- [<span data-ttu-id="d4b33-115">XML 注释标记</span><span class="sxs-lookup"><span data-stu-id="d4b33-115">XML Comment Tags</span></span>](index.md)
