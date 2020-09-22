---
title: <param>
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 19300a928a59c7259f81b282bd28d9bdd447d76b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872628"
---
# <a name="param-visual-basic"></a><span data-ttu-id="ee321-101">\<param> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee321-101">\<param> (Visual Basic)</span></span>

<span data-ttu-id="ee321-102">定义参数名称和说明。</span><span class="sxs-lookup"><span data-stu-id="ee321-102">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee321-103">语法</span><span class="sxs-lookup"><span data-stu-id="ee321-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee321-104">参数</span><span class="sxs-lookup"><span data-stu-id="ee321-104">Parameters</span></span>  

 `name`  
 <span data-ttu-id="ee321-105">方法参数的名称。</span><span class="sxs-lookup"><span data-stu-id="ee321-105">The name of a method parameter.</span></span> <span data-ttu-id="ee321-106">用双引号 (" ") 将名称引起来。</span><span class="sxs-lookup"><span data-stu-id="ee321-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="ee321-107">参数的说明。</span><span class="sxs-lookup"><span data-stu-id="ee321-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee321-108">备注</span><span class="sxs-lookup"><span data-stu-id="ee321-108">Remarks</span></span>  

 <span data-ttu-id="ee321-109">在方法声明的注释中，应使用 `<param>` 标记来描述方法参数之一。</span><span class="sxs-lookup"><span data-stu-id="ee321-109">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="ee321-110">标记的文本 `<param>` 将出现在以下位置：</span><span class="sxs-lookup"><span data-stu-id="ee321-110">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
- <span data-ttu-id="ee321-111">IntelliSense 的参数信息。</span><span class="sxs-lookup"><span data-stu-id="ee321-111">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="ee321-112">有关详细信息，请参阅[使用 IntelliSense](/visualstudio/ide/using-intellisense)。</span><span class="sxs-lookup"><span data-stu-id="ee321-112">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
- <span data-ttu-id="ee321-113">对象浏览器。</span><span class="sxs-lookup"><span data-stu-id="ee321-113">Object Browser.</span></span> <span data-ttu-id="ee321-114">有关详细信息，请参阅 [查看代码的结构](/visualstudio/ide/viewing-the-structure-of-code)。</span><span class="sxs-lookup"><span data-stu-id="ee321-114">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="ee321-115">使用 [-doc](../../reference/command-line-compiler/doc.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="ee321-115">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee321-116">示例</span><span class="sxs-lookup"><span data-stu-id="ee321-116">Example</span></span>  

 <span data-ttu-id="ee321-117">此示例使用 `<param>` 标记来描述 `id` 参数。</span><span class="sxs-lookup"><span data-stu-id="ee321-117">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="ee321-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ee321-118">See also</span></span>

- [<span data-ttu-id="ee321-119">XML 注释标记</span><span class="sxs-lookup"><span data-stu-id="ee321-119">XML Comment Tags</span></span>](index.md)
