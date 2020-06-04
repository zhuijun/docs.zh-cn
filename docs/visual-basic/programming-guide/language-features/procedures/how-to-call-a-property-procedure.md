---
title: 如何：调用 Property 过程
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: 006961a0f1d4be6b0d52be5bc273dad9733bfe56
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388694"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="9a10a-102">如何：调用 Property 过程 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a10a-102">How to: Call a Property Procedure (Visual Basic)</span></span>
<span data-ttu-id="9a10a-103">通过在属性中存储值或检索其值来调用属性过程。</span><span class="sxs-lookup"><span data-stu-id="9a10a-103">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="9a10a-104">访问属性的方式与访问变量的方式相同。</span><span class="sxs-lookup"><span data-stu-id="9a10a-104">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="9a10a-105">该属性的 `Set` 过程存储一个值，其 `Get` 过程检索值。</span><span class="sxs-lookup"><span data-stu-id="9a10a-105">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="9a10a-106">但是，不要按名称显式调用这些过程。</span><span class="sxs-lookup"><span data-stu-id="9a10a-106">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="9a10a-107">使用赋值语句或表达式中的属性，就像存储或检索变量的值一样。</span><span class="sxs-lookup"><span data-stu-id="9a10a-107">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> <span data-ttu-id="9a10a-108">Visual Basic 对属性的过程进行调用。</span><span class="sxs-lookup"><span data-stu-id="9a10a-108">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="9a10a-109">调用属性的 Get 过程</span><span class="sxs-lookup"><span data-stu-id="9a10a-109">To call a property's Get procedure</span></span>  
  
1. <span data-ttu-id="9a10a-110">在表达式中使用属性名称的方式与使用变量名相同。</span><span class="sxs-lookup"><span data-stu-id="9a10a-110">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="9a10a-111">可以在可以使用变量或常量的任何位置使用属性。</span><span class="sxs-lookup"><span data-stu-id="9a10a-111">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="9a10a-112">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="9a10a-112">-or-</span></span>  
  
     <span data-ttu-id="9a10a-113">在赋值语句中，在等号（）后使用属性名称 `=` 。</span><span class="sxs-lookup"><span data-stu-id="9a10a-113">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="9a10a-114">下面的示例读取属性的值 <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> ，隐式调用其 `Get` 过程。</span><span class="sxs-lookup"><span data-stu-id="9a10a-114">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="9a10a-115">如果属性采用参数，请在属性名称后面加上括号，以将参数列表括起来。</span><span class="sxs-lookup"><span data-stu-id="9a10a-115">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="9a10a-116">如果没有参数，则可以选择省略括号。</span><span class="sxs-lookup"><span data-stu-id="9a10a-116">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="9a10a-117">将参数置于括号中的参数列表内，用逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="9a10a-117">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="9a10a-118">请确保以属性定义相应参数的相同顺序提供参数。</span><span class="sxs-lookup"><span data-stu-id="9a10a-118">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="9a10a-119">属性的值作为变量或常数加入表达式，或者将其存储在赋值语句左侧的变量或属性中。</span><span class="sxs-lookup"><span data-stu-id="9a10a-119">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="9a10a-120">调用属性的 Set 过程</span><span class="sxs-lookup"><span data-stu-id="9a10a-120">To call a property's Set procedure</span></span>  
  
1. <span data-ttu-id="9a10a-121">使用赋值语句左侧的属性名称。</span><span class="sxs-lookup"><span data-stu-id="9a10a-121">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="9a10a-122">下面的示例设置属性的值 <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> ，隐式调用该 `Set` 过程。</span><span class="sxs-lookup"><span data-stu-id="9a10a-122">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. <span data-ttu-id="9a10a-123">如果属性采用参数，请在属性名称后面加上括号，以将参数列表括起来。</span><span class="sxs-lookup"><span data-stu-id="9a10a-123">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="9a10a-124">如果没有参数，则可以选择省略括号。</span><span class="sxs-lookup"><span data-stu-id="9a10a-124">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="9a10a-125">将参数置于括号中的参数列表内，用逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="9a10a-125">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="9a10a-126">请确保以属性定义相应参数的相同顺序提供参数。</span><span class="sxs-lookup"><span data-stu-id="9a10a-126">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="9a10a-127">赋值语句右侧生成的值存储在属性中。</span><span class="sxs-lookup"><span data-stu-id="9a10a-127">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a10a-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9a10a-128">See also</span></span>

- [<span data-ttu-id="9a10a-129">Property 过程</span><span class="sxs-lookup"><span data-stu-id="9a10a-129">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="9a10a-130">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="9a10a-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="9a10a-131">Property Statement</span><span class="sxs-lookup"><span data-stu-id="9a10a-131">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="9a10a-132">Visual Basic 中属性和变量的差异</span><span class="sxs-lookup"><span data-stu-id="9a10a-132">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="9a10a-133">如何：创建属性</span><span class="sxs-lookup"><span data-stu-id="9a10a-133">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="9a10a-134">如何：声明具有混合访问级别的属性</span><span class="sxs-lookup"><span data-stu-id="9a10a-134">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="9a10a-135">如何：在 Visual Basic 中声明和调用默认属性</span><span class="sxs-lookup"><span data-stu-id="9a10a-135">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="9a10a-136">如何：在属性中放置值</span><span class="sxs-lookup"><span data-stu-id="9a10a-136">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="9a10a-137">如何：从属性获取值</span><span class="sxs-lookup"><span data-stu-id="9a10a-137">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
- [<span data-ttu-id="9a10a-138">Get 语句</span><span class="sxs-lookup"><span data-stu-id="9a10a-138">Get Statement</span></span>](../../../language-reference/statements/get-statement.md)
- [<span data-ttu-id="9a10a-139">Set 语句</span><span class="sxs-lookup"><span data-stu-id="9a10a-139">Set Statement</span></span>](../../../language-reference/statements/set-statement.md)
