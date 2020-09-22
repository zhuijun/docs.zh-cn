---
title: 程序集
ms.date: 07/20/2015
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
helpviewer_keywords:
- Assembly modifier
- Assembly keyword [Visual Basic]
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
ms.openlocfilehash: 34d6b94f31336e3e99b8ca981a9c4899e5a3d912
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875531"
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="cf1c0-102">程序集 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf1c0-102">Assembly (Visual Basic)</span></span>

<span data-ttu-id="cf1c0-103">指定源文件开头的属性应用于整个程序集。</span><span class="sxs-lookup"><span data-stu-id="cf1c0-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf1c0-104">备注</span><span class="sxs-lookup"><span data-stu-id="cf1c0-104">Remarks</span></span>  

 <span data-ttu-id="cf1c0-105">许多属性都属于单个编程元素，如类或属性。</span><span class="sxs-lookup"><span data-stu-id="cf1c0-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="cf1c0-106">可以通过将特性块附加到尖括号 (在) 中，将此类特性直接应用于 `< >` 声明语句。</span><span class="sxs-lookup"><span data-stu-id="cf1c0-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="cf1c0-107">如果某个特性不仅与以下元素有关，而不属于整个程序集，则可以将特性块放在源文件的开头，并使用关键字标识该特性 `Assembly` 。</span><span class="sxs-lookup"><span data-stu-id="cf1c0-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="cf1c0-108">如果它适用于当前程序集模块，则使用 [module](module-keyword.md) 关键字。</span><span class="sxs-lookup"><span data-stu-id="cf1c0-108">If it applies to the current assembly module, you use the [Module](module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="cf1c0-109">你还可以在 AssemblyInfo 文件中将属性应用于程序集，在这种情况下，你不必在主源代码文件中使用属性块。</span><span class="sxs-lookup"><span data-stu-id="cf1c0-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf1c0-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cf1c0-110">See also</span></span>

- [<span data-ttu-id="cf1c0-111">模块 \<keyword></span><span class="sxs-lookup"><span data-stu-id="cf1c0-111">Module \<keyword></span></span>](module-keyword.md)
- [<span data-ttu-id="cf1c0-112">属性概述</span><span class="sxs-lookup"><span data-stu-id="cf1c0-112">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
