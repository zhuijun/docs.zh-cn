---
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 6e9f63e4d31df7790f51ae4d166b606f2c63f14b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872975"
---
# <a name="example-visual-basic"></a><span data-ttu-id="32d57-101">\<example> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32d57-101">\<example> (Visual Basic)</span></span>

<span data-ttu-id="32d57-102">指定成员的示例。</span><span class="sxs-lookup"><span data-stu-id="32d57-102">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32d57-103">语法</span><span class="sxs-lookup"><span data-stu-id="32d57-103">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a><span data-ttu-id="32d57-104">参数</span><span class="sxs-lookup"><span data-stu-id="32d57-104">Parameters</span></span>  

 `description`  
 <span data-ttu-id="32d57-105">代码示例的说明。</span><span class="sxs-lookup"><span data-stu-id="32d57-105">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32d57-106">备注</span><span class="sxs-lookup"><span data-stu-id="32d57-106">Remarks</span></span>  

 <span data-ttu-id="32d57-107">借助 `<example>` 标记，可以指定如何使用方法或其他库成员的示例。</span><span class="sxs-lookup"><span data-stu-id="32d57-107">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="32d57-108">这通常涉及到使用 [\<code>](code.md) 标记。</span><span class="sxs-lookup"><span data-stu-id="32d57-108">This commonly involves using the [\<code>](code.md) tag.</span></span>  
  
 <span data-ttu-id="32d57-109">使用 [-doc](../../reference/command-line-compiler/doc.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="32d57-109">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32d57-110">示例</span><span class="sxs-lookup"><span data-stu-id="32d57-110">Example</span></span>  

 <span data-ttu-id="32d57-111">此示例使用 `<example>` 标记来包含使用字段的示例 `ID` 。</span><span class="sxs-lookup"><span data-stu-id="32d57-111">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="32d57-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="32d57-112">See also</span></span>

- [<span data-ttu-id="32d57-113">XML 注释标记</span><span class="sxs-lookup"><span data-stu-id="32d57-113">XML Comment Tags</span></span>](index.md)
