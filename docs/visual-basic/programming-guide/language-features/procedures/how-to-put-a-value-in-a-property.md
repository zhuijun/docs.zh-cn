---
title: 如何：在属性中放置值
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: 7d85066d4678ee2a53b8339bee2db20374482579
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071399"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a><span data-ttu-id="5aba4-102">如何：在属性中放置值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5aba4-102">How to: Put a Value in a Property (Visual Basic)</span></span>

<span data-ttu-id="5aba4-103">通过将属性名称放在赋值语句的左侧，可以在属性中存储值。</span><span class="sxs-lookup"><span data-stu-id="5aba4-103">You store a value in a property by putting the property name on the left side of an assignment statement.</span></span>  
  
 <span data-ttu-id="5aba4-104">该属性的 `Set` 过程存储一个值，但不会按名称显式调用它。</span><span class="sxs-lookup"><span data-stu-id="5aba4-104">The property's `Set` procedure stores a value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="5aba4-105">像使用变量一样使用属性。</span><span class="sxs-lookup"><span data-stu-id="5aba4-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="5aba4-106">Visual Basic 对属性的过程进行调用。</span><span class="sxs-lookup"><span data-stu-id="5aba4-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-store-a-value-in-a-property"></a><span data-ttu-id="5aba4-107">在属性中存储值</span><span class="sxs-lookup"><span data-stu-id="5aba4-107">To store a value in a property</span></span>  
  
1. <span data-ttu-id="5aba4-108">使用赋值语句左侧的属性名称。</span><span class="sxs-lookup"><span data-stu-id="5aba4-108">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="5aba4-109">下面的示例将 Visual Basic 属性的值设置 `TimeOfDay` 为 noon，并隐式调用其 `Set` 过程。</span><span class="sxs-lookup"><span data-stu-id="5aba4-109">The following example sets the value of the Visual Basic `TimeOfDay` property to noon, implicitly calling its `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. <span data-ttu-id="5aba4-110">如果属性采用参数，请在属性名称后面加上括号，以将参数列表括起来。</span><span class="sxs-lookup"><span data-stu-id="5aba4-110">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="5aba4-111">如果没有参数，则可以选择省略括号。</span><span class="sxs-lookup"><span data-stu-id="5aba4-111">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="5aba4-112">将参数置于括号中的参数列表内，用逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="5aba4-112">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="5aba4-113">请确保以属性定义相应参数的相同顺序提供参数。</span><span class="sxs-lookup"><span data-stu-id="5aba4-113">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
4. <span data-ttu-id="5aba4-114">赋值语句右侧生成的值存储在属性中。</span><span class="sxs-lookup"><span data-stu-id="5aba4-114">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5aba4-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="5aba4-115">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [<span data-ttu-id="5aba4-116">Property 过程</span><span class="sxs-lookup"><span data-stu-id="5aba4-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="5aba4-117">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="5aba4-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="5aba4-118">Property Statement</span><span class="sxs-lookup"><span data-stu-id="5aba4-118">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="5aba4-119">Visual Basic 中属性和变量的差异</span><span class="sxs-lookup"><span data-stu-id="5aba4-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="5aba4-120">如何：创建属性</span><span class="sxs-lookup"><span data-stu-id="5aba4-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="5aba4-121">如何：声明具有混合访问级别的属性</span><span class="sxs-lookup"><span data-stu-id="5aba4-121">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="5aba4-122">如何：调用 Property 过程</span><span class="sxs-lookup"><span data-stu-id="5aba4-122">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="5aba4-123">如何：在 Visual Basic 中声明和调用默认属性</span><span class="sxs-lookup"><span data-stu-id="5aba4-123">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="5aba4-124">如何：从属性获取值</span><span class="sxs-lookup"><span data-stu-id="5aba4-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
