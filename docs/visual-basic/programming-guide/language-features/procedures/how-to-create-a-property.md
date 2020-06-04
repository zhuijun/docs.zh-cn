---
title: 如何：创建属性
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: fa220998d12206e620c242b9b39df3dc1b639d29
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388253"
---
# <a name="how-to-create-a-property-visual-basic"></a><span data-ttu-id="c4a1d-102">如何：创建属性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4a1d-102">How to: Create a Property (Visual Basic)</span></span>
<span data-ttu-id="c4a1d-103">将属性定义包含在 `Property` 语句和 `End Property` 语句之间。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-103">You enclose a property definition between a `Property` statement and an `End Property` statement.</span></span> <span data-ttu-id="c4a1d-104">在此定义中，你将定义 `Get` 过程、 `Set` 过程或同时定义这两者。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-104">Within this definition you define a `Get` procedure, a `Set` procedure, or both.</span></span> <span data-ttu-id="c4a1d-105">所有属性的代码都位于这些过程中。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-105">All the property's code lies within these procedures.</span></span>  
  
 <span data-ttu-id="c4a1d-106">`Get`过程检索属性的值，并且 `Set` 过程存储值。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-106">The `Get` procedure retrieves the property's value, and the `Set` procedure stores a value.</span></span> <span data-ttu-id="c4a1d-107">如果希望属性具有读/写访问权限，则必须定义这两个过程。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-107">If you want the property to have read/write access, you must define both procedures.</span></span> <span data-ttu-id="c4a1d-108">对于只读属性，只定义 `Get` ，对于只写属性，只定义 `Set` 。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-108">For a read-only property, you define only `Get`, and for a write-only property, you define only `Set`.</span></span>  
  
### <a name="to-create-a-property"></a><span data-ttu-id="c4a1d-109">创建属性</span><span class="sxs-lookup"><span data-stu-id="c4a1d-109">To create a property</span></span>  
  
1. <span data-ttu-id="c4a1d-110">在任何属性或过程外部，使用[Property 语句](../../../language-reference/statements/property-statement.md)，后跟 `End Property` 语句。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-110">Outside any property or procedure, use a [Property Statement](../../../language-reference/statements/property-statement.md), followed by an `End Property` statement.</span></span>  
  
2. <span data-ttu-id="c4a1d-111">如果属性采用参数，请在关键字后面跟 `Property` 上过程的名称，然后将参数列表括在括号中。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-111">If the property takes parameters, follow the `Property` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>  
  
3. <span data-ttu-id="c4a1d-112">在括号后跟一个 `As` 子句以指定属性值的数据类型。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-112">Follow the parentheses with an `As` clause to specify the data type of the property's value.</span></span> <span data-ttu-id="c4a1d-113">即使对于只写属性，也必须指定数据类型。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-113">You must specify the data type even for a write-only property.</span></span>  
  
4. <span data-ttu-id="c4a1d-114">`Get` `Set` 根据需要添加和过程。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-114">Add `Get` and `Set` procedures, as appropriate.</span></span> <span data-ttu-id="c4a1d-115">请参阅以下说明。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-115">See the following directions.</span></span>  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a><span data-ttu-id="c4a1d-116">创建检索属性值的 Get 过程</span><span class="sxs-lookup"><span data-stu-id="c4a1d-116">To create a Get procedure that retrieves a property value</span></span>  
  
1. <span data-ttu-id="c4a1d-117">在 `Property` 和 `End Property` 语句之间，编写[Get 语句](../../../language-reference/statements/get-statement.md)，后跟一个 `End Get` 语句。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-117">Between the `Property` and `End Property` statements, write a [Get Statement](../../../language-reference/statements/get-statement.md), followed by an `End Get` statement.</span></span> <span data-ttu-id="c4a1d-118">无需为过程定义任何参数 `Get` 。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-118">You do not need to define any parameters for the `Get` procedure.</span></span>  
  
2. <span data-ttu-id="c4a1d-119">放置代码语句以检索和语句之间的属性值 `Get` `End Get` 。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-119">Place the code statements to retrieve the property's value between the `Get` and `End Get` statements.</span></span> <span data-ttu-id="c4a1d-120">除了生成并返回属性的值外，此代码还可以包含其他计算和数据操作。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-120">This code can include other calculations and data manipulations in addition to generating and returning the property's value.</span></span>  
  
3. <span data-ttu-id="c4a1d-121">使用 `Return` 语句将属性的值返回到调用代码。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-121">Use a `Return` statement to return the property's value to the calling code.</span></span>  
  
 <span data-ttu-id="c4a1d-122">必须 `Get` 为读写属性以及只读属性编写过程。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-122">You must write a `Get` procedure for a read-write property and for a read-only property.</span></span> <span data-ttu-id="c4a1d-123">不得 `Get` 为只写属性定义过程。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-123">You must not define a `Get` procedure for a write-only property.</span></span>  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a><span data-ttu-id="c4a1d-124">创建写入属性值的 Set 过程</span><span class="sxs-lookup"><span data-stu-id="c4a1d-124">To create a Set procedure that writes a property's value</span></span>  
  
1. <span data-ttu-id="c4a1d-125">在 `Property` 和 `End Property` 语句之间，编写一个[Set 语句](../../../language-reference/statements/set-statement.md)，后跟一个 `End Set` 语句。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-125">Between the `Property` and `End Property` statements, write a [Set Statement](../../../language-reference/statements/set-statement.md), followed by an `End Set` statement.</span></span>  
  
2. <span data-ttu-id="c4a1d-126">在 `Set` 语句中，在 `Set` 关键字后面加上括号中的参数列表。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-126">In the `Set` statement, follow the `Set` keyword with a parameter list in parentheses.</span></span> <span data-ttu-id="c4a1d-127">此参数列表必须至少包含调用代码传递的值的值参数。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-127">This parameter list must include at least a value parameter for the value passed by the calling code.</span></span> <span data-ttu-id="c4a1d-128">此值参数的默认名称为 `Value` ，但你可以根据需要使用不同的名称。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-128">The default name for this value parameter is `Value`, but you can use a different name if appropriate.</span></span> <span data-ttu-id="c4a1d-129">Value 参数的数据类型必须与属性本身的数据类型相同。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-129">The value parameter must have the same data type as the property itself.</span></span>  
  
3. <span data-ttu-id="c4a1d-130">放置代码语句，以在和语句之间存储值 `Set` `End Set` 。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-130">Place the code statements to store a value in the property between the `Set` and `End Set` statements.</span></span> <span data-ttu-id="c4a1d-131">除了验证和存储属性值外，此代码还可以包含其他计算和数据操作。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-131">This code can include other calculations and data manipulations in addition to validating and storing the property's value.</span></span>  
  
4. <span data-ttu-id="c4a1d-132">使用 value 参数接受调用代码提供的值。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-132">Use the value parameter to accept the value supplied by the calling code.</span></span> <span data-ttu-id="c4a1d-133">您可以直接在赋值语句中存储此值，也可以在表达式中使用该值来计算要存储的内部值。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-133">You can either store this value directly in an assignment statement, or use it in an expression to calculate the internal value to be stored.</span></span>  
  
 <span data-ttu-id="c4a1d-134">您必须为 `Set` 读写属性和只写属性编写一个过程。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-134">You must write a `Set` procedure for a read-write property and for a write-only property.</span></span> <span data-ttu-id="c4a1d-135">不得 `Set` 为只读属性定义过程。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-135">You must not define a `Set` procedure for a read-only property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4a1d-136">示例</span><span class="sxs-lookup"><span data-stu-id="c4a1d-136">Example</span></span>  
 <span data-ttu-id="c4a1d-137">下面的示例创建一个读/写属性，该属性将全名存储为两个构成名称，即名字和姓氏。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-137">The following example creates a read/write property that stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="c4a1d-138">在调用代码读取时 `fullName` ，此 `Get` 过程将组合这两个构成名称并返回全名。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-138">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="c4a1d-139">当调用代码分配新的全名时，该 `Set` 过程会尝试将其分成两个构成名称。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-139">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="c4a1d-140">如果找不到空间，则会将其存储为名字。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-140">If it does not find a space, it stores it all as the first name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 <span data-ttu-id="c4a1d-141">下面的示例演示对的属性过程的典型调用 `fullName` 。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-141">The following example shows typical calls to the property procedures of `fullName`.</span></span> <span data-ttu-id="c4a1d-142">第一次调用设置属性值，第二次调用将检索它。</span><span class="sxs-lookup"><span data-stu-id="c4a1d-142">The first call sets the property value and the second call retrieves it.</span></span>  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="c4a1d-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c4a1d-143">See also</span></span>

- [<span data-ttu-id="c4a1d-144">过程</span><span class="sxs-lookup"><span data-stu-id="c4a1d-144">Procedures</span></span>](./index.md)
- [<span data-ttu-id="c4a1d-145">Property 过程</span><span class="sxs-lookup"><span data-stu-id="c4a1d-145">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="c4a1d-146">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="c4a1d-146">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="c4a1d-147">Visual Basic 中属性和变量的差异</span><span class="sxs-lookup"><span data-stu-id="c4a1d-147">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="c4a1d-148">如何：声明具有混合访问级别的属性</span><span class="sxs-lookup"><span data-stu-id="c4a1d-148">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="c4a1d-149">如何：调用 Property 过程</span><span class="sxs-lookup"><span data-stu-id="c4a1d-149">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="c4a1d-150">如何：在 Visual Basic 中声明和调用默认属性</span><span class="sxs-lookup"><span data-stu-id="c4a1d-150">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="c4a1d-151">如何：在属性中放置值</span><span class="sxs-lookup"><span data-stu-id="c4a1d-151">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="c4a1d-152">如何：从属性获取值</span><span class="sxs-lookup"><span data-stu-id="c4a1d-152">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
