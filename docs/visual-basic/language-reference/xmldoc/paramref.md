---
title: <paramref>
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: d7aacc5faea22f9c5a4b865a32c832154fe624c5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872618"
---
# <a name="paramref-visual-basic"></a><span data-ttu-id="30daf-101">\<paramref> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30daf-101">\<paramref> (Visual Basic)</span></span>

<span data-ttu-id="30daf-102">将单词设置为参数格式。</span><span class="sxs-lookup"><span data-stu-id="30daf-102">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30daf-103">语法</span><span class="sxs-lookup"><span data-stu-id="30daf-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="30daf-104">参数</span><span class="sxs-lookup"><span data-stu-id="30daf-104">Parameters</span></span>  

 `name`  
 <span data-ttu-id="30daf-105">要引用的参数的名称。</span><span class="sxs-lookup"><span data-stu-id="30daf-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="30daf-106">用双引号 (" ") 将名称引起来。</span><span class="sxs-lookup"><span data-stu-id="30daf-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30daf-107">备注</span><span class="sxs-lookup"><span data-stu-id="30daf-107">Remarks</span></span>  

 <span data-ttu-id="30daf-108">`<paramref>`标记提供了一种方法，用于指示某个字是参数。</span><span class="sxs-lookup"><span data-stu-id="30daf-108">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="30daf-109">可以处理 XML 文件，以便以某种不同的方式格式化此参数。</span><span class="sxs-lookup"><span data-stu-id="30daf-109">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="30daf-110">使用 [-doc](../../reference/command-line-compiler/doc.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="30daf-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30daf-111">示例</span><span class="sxs-lookup"><span data-stu-id="30daf-111">Example</span></span>  

 <span data-ttu-id="30daf-112">此示例使用 `<paramref>` 标记来引用 `id` 参数。</span><span class="sxs-lookup"><span data-stu-id="30daf-112">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="30daf-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="30daf-113">See also</span></span>

- [<span data-ttu-id="30daf-114">XML 注释标记</span><span class="sxs-lookup"><span data-stu-id="30daf-114">XML Comment Tags</span></span>](index.md)
