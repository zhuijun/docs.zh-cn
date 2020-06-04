---
title: 指令
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: b5fcf3cb8801bc99dd2096c28cc41ebefeb34592
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409993"
---
# <a name="directives-visual-basic"></a><span data-ttu-id="a252a-102">指令 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a252a-102">Directives (Visual Basic)</span></span>

<span data-ttu-id="a252a-103">本节中的主题记录 Visual Basic 源代码编译器指令。</span><span class="sxs-lookup"><span data-stu-id="a252a-103">The topics in this section document the Visual Basic source code compiler directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a252a-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="a252a-104">In This Section</span></span>  

 <span data-ttu-id="a252a-105">[#Const 指令](const-directive.md)--定义编译器常量</span><span class="sxs-lookup"><span data-stu-id="a252a-105">[#Const Directive](const-directive.md) -- Define a compiler constant</span></span>  
  
 <span data-ttu-id="a252a-106">[#ExternalSource 指令](externalsource-directive.md)--指示源行与源外部的文本之间的映射</span><span class="sxs-lookup"><span data-stu-id="a252a-106">[#ExternalSource Directive](externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source</span></span>  
  
 <span data-ttu-id="a252a-107">[#If .。。Then ... #Else 指令](if-then-else-directives.md)-编译选定的代码块</span><span class="sxs-lookup"><span data-stu-id="a252a-107">[#If...Then...#Else Directives](if-then-else-directives.md) -- Compile selected blocks of code</span></span>  
  
 <span data-ttu-id="a252a-108">[#Region 指令](region-directive.md)--折叠和隐藏 Visual Studio 编辑器中的代码段</span><span class="sxs-lookup"><span data-stu-id="a252a-108">[#Region Directive](region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor</span></span>  
  
 <span data-ttu-id="a252a-109">**#Disable，#Enable** --针对代码区域禁用和启用特定警告。</span><span class="sxs-lookup"><span data-stu-id="a252a-109">**#Disable, #Enable** -- Disable and enable specific warnings for regions of code.</span></span>  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 <span data-ttu-id="a252a-110">还可以禁用和启用以逗号分隔的警告代码列表。</span><span class="sxs-lookup"><span data-stu-id="a252a-110">You can disable and enable a comma-separated list of warning codes too.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a252a-111">相关章节</span><span class="sxs-lookup"><span data-stu-id="a252a-111">Related Sections</span></span>  

 [<span data-ttu-id="a252a-112">Visual Basic 语言参考</span><span class="sxs-lookup"><span data-stu-id="a252a-112">Visual Basic Language Reference</span></span>](../index.md)  
  