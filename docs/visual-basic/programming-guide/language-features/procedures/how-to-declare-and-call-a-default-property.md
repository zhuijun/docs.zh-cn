---
title: 如何：声明和调用默认属性
ms.date: 07/20/2015
helpviewer_keywords:
- defaults [Visual Basic], properties
- properties [Visual Basic], default
- procedures [Visual Basic], defining
- default properties [Visual Basic], in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
ms.openlocfilehash: 21aa6e6a9bba23d767b9d1fac610eaac3265550d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91087448"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a><span data-ttu-id="dbc47-102">如何：在 Visual Basic 中声明和调用默认属性</span><span class="sxs-lookup"><span data-stu-id="dbc47-102">How to: Declare and Call a Default Property in Visual Basic</span></span>

<span data-ttu-id="dbc47-103">*默认属性*是您的代码无需指定即可访问的类或结构属性。</span><span class="sxs-lookup"><span data-stu-id="dbc47-103">A *default property* is a class or structure property that your code can access without specifying it.</span></span> <span data-ttu-id="dbc47-104">当调用代码命名类或结构而不是属性，并且上下文允许访问属性时，Visual Basic 解析对该类或结构的默认属性（如果存在）的访问。</span><span class="sxs-lookup"><span data-stu-id="dbc47-104">When calling code names a class or structure but not a property, and the context allows access to a property, Visual Basic resolves the access to that class or structure's default property if one exists.</span></span>  
  
 <span data-ttu-id="dbc47-105">一个类或结构最多只能有一个默认属性。</span><span class="sxs-lookup"><span data-stu-id="dbc47-105">A class or structure can have at most one default property.</span></span> <span data-ttu-id="dbc47-106">不过，你可以重载一个默认属性，并拥有多个版本的属性。</span><span class="sxs-lookup"><span data-stu-id="dbc47-106">However, you can overload a default property and have more than one version of it.</span></span>  
  
 <span data-ttu-id="dbc47-107">有关详细信息，请参阅 [默认值](../../../language-reference/modifiers/default.md)。</span><span class="sxs-lookup"><span data-stu-id="dbc47-107">For more information, see [Default](../../../language-reference/modifiers/default.md).</span></span>  
  
### <a name="to-declare-a-default-property"></a><span data-ttu-id="dbc47-108">声明默认属性</span><span class="sxs-lookup"><span data-stu-id="dbc47-108">To declare a default property</span></span>  
  
1. <span data-ttu-id="dbc47-109">以正常方式声明属性。</span><span class="sxs-lookup"><span data-stu-id="dbc47-109">Declare the property in the normal way.</span></span> <span data-ttu-id="dbc47-110">不要指定 `Shared` 或 `Private` 关键字。</span><span class="sxs-lookup"><span data-stu-id="dbc47-110">Do not specify the `Shared` or `Private` keyword.</span></span>  
  
2. <span data-ttu-id="dbc47-111">`Default`在属性声明中包含关键字。</span><span class="sxs-lookup"><span data-stu-id="dbc47-111">Include the `Default` keyword in the property declaration.</span></span>  
  
3. <span data-ttu-id="dbc47-112">至少为属性指定一个参数。</span><span class="sxs-lookup"><span data-stu-id="dbc47-112">Specify at least one parameter for the property.</span></span> <span data-ttu-id="dbc47-113">不能定义不接受至少一个参数的默认属性。</span><span class="sxs-lookup"><span data-stu-id="dbc47-113">You cannot define a default property that does not take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#17)]  
  
### <a name="to-call-a-default-property"></a><span data-ttu-id="dbc47-114">调用默认属性</span><span class="sxs-lookup"><span data-stu-id="dbc47-114">To call a default property</span></span>  
  
1. <span data-ttu-id="dbc47-115">声明包含类或结构类型的变量。</span><span class="sxs-lookup"><span data-stu-id="dbc47-115">Declare a variable of the containing class or structure type.</span></span>  
  
     [!code-vb[VbVbcnProcedures#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#16)]  
  
2. <span data-ttu-id="dbc47-116">在通常包含属性名称的表达式中单独使用变量名。</span><span class="sxs-lookup"><span data-stu-id="dbc47-116">Use the variable name alone in an expression where you would normally include the property name.</span></span>  
  
     [!code-vb[VbVbcnProcedures#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#21)]  
  
3. <span data-ttu-id="dbc47-117">在变量名称后面加上括号中的参数列表。</span><span class="sxs-lookup"><span data-stu-id="dbc47-117">Follow the variable name with an argument list in parentheses.</span></span> <span data-ttu-id="dbc47-118">默认属性必须至少采用一个参数。</span><span class="sxs-lookup"><span data-stu-id="dbc47-118">A default property must take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#20)]  
  
4. <span data-ttu-id="dbc47-119">若要检索默认属性值，请在表达式中使用变量名，在表达式中使用变量名，或者在等 (`=`) 在赋值语句中登录。</span><span class="sxs-lookup"><span data-stu-id="dbc47-119">To retrieve the default property value, use the variable name, with an argument list, in an expression or following the equal (`=`) sign in an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#15)]  
  
5. <span data-ttu-id="dbc47-120">若要设置默认属性值，请在赋值语句左侧使用带有参数列表的变量名称。</span><span class="sxs-lookup"><span data-stu-id="dbc47-120">To set the default property value, use the variable name, with an argument list, on the left side of an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#14)]  
  
6. <span data-ttu-id="dbc47-121">您始终可以将默认属性名称与变量名称一起指定，就像访问任何其他属性一样。</span><span class="sxs-lookup"><span data-stu-id="dbc47-121">You can always specify the default property name together with the variable name, just as you would do to access any other property.</span></span>  
  
     [!code-vb[VbVbcnProcedures#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#19)]  
  
## <a name="example"></a><span data-ttu-id="dbc47-122">示例</span><span class="sxs-lookup"><span data-stu-id="dbc47-122">Example</span></span>  

 <span data-ttu-id="dbc47-123">下面的示例声明类的默认属性。</span><span class="sxs-lookup"><span data-stu-id="dbc47-123">The following example declares a default property on a class.</span></span>  
  
 [!code-vb[VbVbcnProcedures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="dbc47-124">示例</span><span class="sxs-lookup"><span data-stu-id="dbc47-124">Example</span></span>  

 <span data-ttu-id="dbc47-125">下面的示例演示如何调用类的默认属性 `myProperty` `class1` 。</span><span class="sxs-lookup"><span data-stu-id="dbc47-125">The following example demonstrates how to call the default property `myProperty` on class `class1`.</span></span> <span data-ttu-id="dbc47-126">这三个赋值语句将值存储在中 `myProperty` ，并且 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 调用读取这些值。</span><span class="sxs-lookup"><span data-stu-id="dbc47-126">The three assignment statements store values in `myProperty`, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> call reads the values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#13)]  
  
 <span data-ttu-id="dbc47-127">默认属性的最常见用途是 <xref:Microsoft.VisualBasic.Collection.Item%2A> 不同集合类的属性。</span><span class="sxs-lookup"><span data-stu-id="dbc47-127">The most common use of a default property is the <xref:Microsoft.VisualBasic.Collection.Item%2A> property on various collection classes.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="dbc47-128">可靠编程</span><span class="sxs-lookup"><span data-stu-id="dbc47-128">Robust Programming</span></span>  

 <span data-ttu-id="dbc47-129">默认属性可能会减少源代码中的字符，但会使代码更难以阅读。</span><span class="sxs-lookup"><span data-stu-id="dbc47-129">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="dbc47-130">如果调用代码不熟悉你的类或结构，则当它对类或结构名称进行引用时，该引用是否访问类或结构本身，或者默认属性，则不能确定这一点。</span><span class="sxs-lookup"><span data-stu-id="dbc47-130">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="dbc47-131">这可能会导致编译器错误或细微的运行时逻辑错误。</span><span class="sxs-lookup"><span data-stu-id="dbc47-131">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="dbc47-132">通过始终使用 [Option Strict 语句](../../../language-reference/statements/option-strict-statement.md) 将编译器类型检查设置为，可以在一定程度上减少默认属性错误的几率 `On` 。</span><span class="sxs-lookup"><span data-stu-id="dbc47-132">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="dbc47-133">如果打算在代码中使用预定义的类或结构，则必须确定它是否具有默认属性，如果是，则必须确定其名称。</span><span class="sxs-lookup"><span data-stu-id="dbc47-133">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="dbc47-134">由于这些缺点，你应考虑不要定义默认属性。</span><span class="sxs-lookup"><span data-stu-id="dbc47-134">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="dbc47-135">为实现代码可读性，还应考虑始终显式引用所有属性，甚至是默认属性。</span><span class="sxs-lookup"><span data-stu-id="dbc47-135">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbc47-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="dbc47-136">See also</span></span>

- [<span data-ttu-id="dbc47-137">Property 过程</span><span class="sxs-lookup"><span data-stu-id="dbc47-137">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="dbc47-138">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="dbc47-138">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="dbc47-139">Property Statement</span><span class="sxs-lookup"><span data-stu-id="dbc47-139">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="dbc47-140">默认</span><span class="sxs-lookup"><span data-stu-id="dbc47-140">Default</span></span>](../../../language-reference/modifiers/default.md)
- [<span data-ttu-id="dbc47-141">Visual Basic 中属性和变量的差异</span><span class="sxs-lookup"><span data-stu-id="dbc47-141">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="dbc47-142">如何：创建属性</span><span class="sxs-lookup"><span data-stu-id="dbc47-142">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="dbc47-143">如何：声明具有混合访问级别的属性</span><span class="sxs-lookup"><span data-stu-id="dbc47-143">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="dbc47-144">如何：调用 Property 过程</span><span class="sxs-lookup"><span data-stu-id="dbc47-144">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="dbc47-145">如何：在属性中放置值</span><span class="sxs-lookup"><span data-stu-id="dbc47-145">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="dbc47-146">如何：从属性获取值</span><span class="sxs-lookup"><span data-stu-id="dbc47-146">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
