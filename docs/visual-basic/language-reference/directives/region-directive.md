---
title: '#Region 指令'
ms.date: 07/20/2015
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
ms.openlocfilehash: cd53a6079c1564a8c73a0a1a6273fc166d18d3e6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409929"
---
# <a name="region-directive"></a><span data-ttu-id="56c88-102">#Region 指令</span><span class="sxs-lookup"><span data-stu-id="56c88-102">#Region Directive</span></span>

<span data-ttu-id="56c88-103">折叠并隐藏 Visual Basic 文件中的代码段。</span><span class="sxs-lookup"><span data-stu-id="56c88-103">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56c88-104">语法</span><span class="sxs-lookup"><span data-stu-id="56c88-104">Syntax</span></span>  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="56c88-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="56c88-105">Parts</span></span>  
  
|<span data-ttu-id="56c88-106">术语</span><span class="sxs-lookup"><span data-stu-id="56c88-106">Term</span></span>|<span data-ttu-id="56c88-107">定义</span><span class="sxs-lookup"><span data-stu-id="56c88-107">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="56c88-108">必需。</span><span class="sxs-lookup"><span data-stu-id="56c88-108">Required.</span></span> <span data-ttu-id="56c88-109">当区域处于折叠状态时充当区域标题的字符串。</span><span class="sxs-lookup"><span data-stu-id="56c88-109">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="56c88-110">默认情况下，区域处于折叠状态。</span><span class="sxs-lookup"><span data-stu-id="56c88-110">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="56c88-111">终止 `#Region` 块。</span><span class="sxs-lookup"><span data-stu-id="56c88-111">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56c88-112">备注</span><span class="sxs-lookup"><span data-stu-id="56c88-112">Remarks</span></span>  

 <span data-ttu-id="56c88-113">使用 `#Region` 指令指定使用 Visual Studio Code 编辑器的大纲显示功能时要展开或折叠的代码块。</span><span class="sxs-lookup"><span data-stu-id="56c88-113">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="56c88-114">您可以在其他区域中放置或*嵌套*区域，以将类似区域组合在一起。</span><span class="sxs-lookup"><span data-stu-id="56c88-114">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56c88-115">示例</span><span class="sxs-lookup"><span data-stu-id="56c88-115">Example</span></span>  

 <span data-ttu-id="56c88-116">此示例使用 `#Region` 指令。</span><span class="sxs-lookup"><span data-stu-id="56c88-116">This example uses the `#Region` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="56c88-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="56c88-117">See also</span></span>

- [<span data-ttu-id="56c88-118">#If...Then...#Else 指令</span><span class="sxs-lookup"><span data-stu-id="56c88-118">#If...Then...#Else Directives</span></span>](if-then-else-directives.md)
- [<span data-ttu-id="56c88-119">大纲显示</span><span class="sxs-lookup"><span data-stu-id="56c88-119">Outlining</span></span>](/visualstudio/ide/outlining)
- [<span data-ttu-id="56c88-120">如何：折叠和隐藏代码节</span><span class="sxs-lookup"><span data-stu-id="56c88-120">How to: Collapse and Hide Sections of Code</span></span>](../../programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
