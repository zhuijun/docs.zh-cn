---
title: <param>
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: d325d5f9fbfd132630cf280653be214a267a7a80
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400055"
---
# <a name="param-visual-basic"></a><span data-ttu-id="74c4a-101">\<param> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74c4a-101">\<param> (Visual Basic)</span></span>
<span data-ttu-id="74c4a-102">定义参数名称和说明。</span><span class="sxs-lookup"><span data-stu-id="74c4a-102">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74c4a-103">语法</span><span class="sxs-lookup"><span data-stu-id="74c4a-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="74c4a-104">参数</span><span class="sxs-lookup"><span data-stu-id="74c4a-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="74c4a-105">方法参数的名称。</span><span class="sxs-lookup"><span data-stu-id="74c4a-105">The name of a method parameter.</span></span> <span data-ttu-id="74c4a-106">用双引号 (" ") 将名称引起来。</span><span class="sxs-lookup"><span data-stu-id="74c4a-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="74c4a-107">参数的说明。</span><span class="sxs-lookup"><span data-stu-id="74c4a-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74c4a-108">备注</span><span class="sxs-lookup"><span data-stu-id="74c4a-108">Remarks</span></span>  
 <span data-ttu-id="74c4a-109">在 `<param>` 方法声明的注释中使用标记来描述方法的参数之一。</span><span class="sxs-lookup"><span data-stu-id="74c4a-109">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="74c4a-110">标记的文本 `<param>` 将出现在以下位置：</span><span class="sxs-lookup"><span data-stu-id="74c4a-110">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
- <span data-ttu-id="74c4a-111">IntelliSense 的参数信息。</span><span class="sxs-lookup"><span data-stu-id="74c4a-111">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="74c4a-112">有关详细信息，请参阅[使用 IntelliSense](/visualstudio/ide/using-intellisense)。</span><span class="sxs-lookup"><span data-stu-id="74c4a-112">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
- <span data-ttu-id="74c4a-113">对象浏览器。</span><span class="sxs-lookup"><span data-stu-id="74c4a-113">Object Browser.</span></span> <span data-ttu-id="74c4a-114">有关详细信息，请参阅[查看代码的结构](/visualstudio/ide/viewing-the-structure-of-code)。</span><span class="sxs-lookup"><span data-stu-id="74c4a-114">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="74c4a-115">使用 [-doc](../../reference/command-line-compiler/doc.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="74c4a-115">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74c4a-116">示例</span><span class="sxs-lookup"><span data-stu-id="74c4a-116">Example</span></span>  
 <span data-ttu-id="74c4a-117">此示例使用 `<param>` 标记来描述 `id` 参数。</span><span class="sxs-lookup"><span data-stu-id="74c4a-117">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="74c4a-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="74c4a-118">See also</span></span>

- [<span data-ttu-id="74c4a-119">XML 注释标记</span><span class="sxs-lookup"><span data-stu-id="74c4a-119">XML Comment Tags</span></span>](index.md)
