---
title: 如何：将相关的常量值组合在一起
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 0f694aee722e8ce31f663ec9fe52a09a2eb2a958
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058724"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="c3a8c-102">如何：将相关的常量值组合在一起 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3a8c-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>

<span data-ttu-id="c3a8c-103">枚举是将相关常量组合在一起的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="c3a8c-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="c3a8c-104">使用 `Enum` 类或模块的声明部分中的语句创建枚举。</span><span class="sxs-lookup"><span data-stu-id="c3a8c-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="c3a8c-105">有关详细信息，请参阅 [如何：声明枚举](how-to-declare-enumerations.md)。</span><span class="sxs-lookup"><span data-stu-id="c3a8c-105">For more information, see [How to: Declare an Enumeration](how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="c3a8c-106">对相关常数值分组</span><span class="sxs-lookup"><span data-stu-id="c3a8c-106">To group related constant values</span></span>  
  
1. <span data-ttu-id="c3a8c-107">编写包含代码访问级别、 `Enum` 关键字和有效名称的声明。</span><span class="sxs-lookup"><span data-stu-id="c3a8c-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="c3a8c-108">此示例创建 `Private` 枚举 `temperatureValues` 。</span><span class="sxs-lookup"><span data-stu-id="c3a8c-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. <span data-ttu-id="c3a8c-109">定义枚举中的常量。</span><span class="sxs-lookup"><span data-stu-id="c3a8c-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="c3a8c-110">此示例创建 `Public` 枚举 `temperatureValues` 并分配其值。</span><span class="sxs-lookup"><span data-stu-id="c3a8c-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c3a8c-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="c3a8c-111">See also</span></span>

- [<span data-ttu-id="c3a8c-112">枚举和名称限定</span><span class="sxs-lookup"><span data-stu-id="c3a8c-112">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="c3a8c-113">如何：引用枚举成员</span><span class="sxs-lookup"><span data-stu-id="c3a8c-113">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="c3a8c-114">何时使用枚举</span><span class="sxs-lookup"><span data-stu-id="c3a8c-114">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="c3a8c-115">常量概述</span><span class="sxs-lookup"><span data-stu-id="c3a8c-115">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="c3a8c-116">常数和文本数据类型</span><span class="sxs-lookup"><span data-stu-id="c3a8c-116">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="c3a8c-117">常量和枚举</span><span class="sxs-lookup"><span data-stu-id="c3a8c-117">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
