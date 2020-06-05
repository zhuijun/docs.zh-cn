---
title: <paramref>
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 3ca08016d3cef0c44e4f3c0bd0d017628eda606d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400042"
---
# <a name="paramref-visual-basic"></a><span data-ttu-id="35858-101">\<paramref> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35858-101">\<paramref> (Visual Basic)</span></span>
<span data-ttu-id="35858-102">将单词设置为参数格式。</span><span class="sxs-lookup"><span data-stu-id="35858-102">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35858-103">语法</span><span class="sxs-lookup"><span data-stu-id="35858-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="35858-104">参数</span><span class="sxs-lookup"><span data-stu-id="35858-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="35858-105">要引用的参数的名称。</span><span class="sxs-lookup"><span data-stu-id="35858-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="35858-106">用双引号 (" ") 将名称引起来。</span><span class="sxs-lookup"><span data-stu-id="35858-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35858-107">备注</span><span class="sxs-lookup"><span data-stu-id="35858-107">Remarks</span></span>  
 <span data-ttu-id="35858-108">`<paramref>`标记提供了一种方法，用于指示某个字是参数。</span><span class="sxs-lookup"><span data-stu-id="35858-108">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="35858-109">可以处理 XML 文件，以便以某种不同的方式格式化此参数。</span><span class="sxs-lookup"><span data-stu-id="35858-109">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="35858-110">使用 [-doc](../../reference/command-line-compiler/doc.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="35858-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35858-111">示例</span><span class="sxs-lookup"><span data-stu-id="35858-111">Example</span></span>  
 <span data-ttu-id="35858-112">此示例使用 `<paramref>` 标记来引用 `id` 参数。</span><span class="sxs-lookup"><span data-stu-id="35858-112">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="35858-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="35858-113">See also</span></span>

- [<span data-ttu-id="35858-114">XML 注释标记</span><span class="sxs-lookup"><span data-stu-id="35858-114">XML Comment Tags</span></span>](index.md)
