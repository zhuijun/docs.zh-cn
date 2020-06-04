---
title: Set 语句
ms.date: 07/20/2015
f1_keywords:
- vb.Set
helpviewer_keywords:
- property procedures [Visual Basic], Set statements
- Set statement [Visual Basic]
- Set statement [Visual Basic], syntax
- write-only properties
- properties [Visual Basic], write-only
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
ms.openlocfilehash: 49d4c36805b64d7232a94e818256723a0437b6ef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404182"
---
# <a name="set-statement-visual-basic"></a><span data-ttu-id="c29eb-102">Set 语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c29eb-102">Set Statement (Visual Basic)</span></span>
<span data-ttu-id="c29eb-103">声明 `Set` 用于向属性赋值的属性过程。</span><span class="sxs-lookup"><span data-stu-id="c29eb-103">Declares a `Set` property procedure used to assign a value to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c29eb-104">语法</span><span class="sxs-lookup"><span data-stu-id="c29eb-104">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a><span data-ttu-id="c29eb-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="c29eb-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="c29eb-106">可选。</span><span class="sxs-lookup"><span data-stu-id="c29eb-106">Optional.</span></span> <span data-ttu-id="c29eb-107">请参阅[特性列表](attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="c29eb-107">See [Attribute List](attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="c29eb-108">在 `Get` 此属性中的最多一个和语句上是可选的 `Set` 。</span><span class="sxs-lookup"><span data-stu-id="c29eb-108">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="c29eb-109">可以是以下其中一个值：</span><span class="sxs-lookup"><span data-stu-id="c29eb-109">Can be one of the following:</span></span>  
  
- [<span data-ttu-id="c29eb-110">避免</span><span class="sxs-lookup"><span data-stu-id="c29eb-110">Protected</span></span>](../modifiers/protected.md)  
  
- [<span data-ttu-id="c29eb-111">友好</span><span class="sxs-lookup"><span data-stu-id="c29eb-111">Friend</span></span>](../modifiers/friend.md)  
  
- <span data-ttu-id="c29eb-112">专用 </span><span class="sxs-lookup"><span data-stu-id="c29eb-112">[Private](../modifiers/private.md)</span></span>  
  
- `Protected Friend`  
  
 <span data-ttu-id="c29eb-113">请参阅[Visual Basic 中的访问级别](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="c29eb-113">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `value`  
 <span data-ttu-id="c29eb-114">必需。</span><span class="sxs-lookup"><span data-stu-id="c29eb-114">Required.</span></span> <span data-ttu-id="c29eb-115">包含属性新值的参数。</span><span class="sxs-lookup"><span data-stu-id="c29eb-115">Parameter containing the new value for the property.</span></span>  
  
 `datatype`  
 <span data-ttu-id="c29eb-116">如果 `Option Strict` 为，则为必需 `On` 。</span><span class="sxs-lookup"><span data-stu-id="c29eb-116">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="c29eb-117">参数的数据类型 `value` 。</span><span class="sxs-lookup"><span data-stu-id="c29eb-117">Data type of the `value` parameter.</span></span> <span data-ttu-id="c29eb-118">指定的数据类型必须与声明此语句的属性的数据类型相同 `Set` 。</span><span class="sxs-lookup"><span data-stu-id="c29eb-118">The data type specified must be the same as the data type of the property where this `Set` statement is declared.</span></span>  
  
 `statements`  
 <span data-ttu-id="c29eb-119">可选。</span><span class="sxs-lookup"><span data-stu-id="c29eb-119">Optional.</span></span> <span data-ttu-id="c29eb-120">调用属性过程时运行的一个或多个语句 `Set` 。</span><span class="sxs-lookup"><span data-stu-id="c29eb-120">One or more statements that run when the `Set` property procedure is called.</span></span>  
  
 `End Set`  
 <span data-ttu-id="c29eb-121">必需。</span><span class="sxs-lookup"><span data-stu-id="c29eb-121">Required.</span></span> <span data-ttu-id="c29eb-122">终止属性过程的定义 `Set` 。</span><span class="sxs-lookup"><span data-stu-id="c29eb-122">Terminates the definition of the `Set` property procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c29eb-123">备注</span><span class="sxs-lookup"><span data-stu-id="c29eb-123">Remarks</span></span>  
 <span data-ttu-id="c29eb-124">除非将属性标记为，否则每个属性都必须具有 `Set` 属性过程 `ReadOnly` 。</span><span class="sxs-lookup"><span data-stu-id="c29eb-124">Every property must have a `Set` property procedure unless the property is marked `ReadOnly`.</span></span> <span data-ttu-id="c29eb-125">此 `Set` 过程用于设置属性的值。</span><span class="sxs-lookup"><span data-stu-id="c29eb-125">The `Set` procedure is used to set the value of the property.</span></span>  
  
 <span data-ttu-id="c29eb-126">`Set`当赋值语句提供要存储在属性中的值时，Visual Basic 会自动调用该属性的过程。</span><span class="sxs-lookup"><span data-stu-id="c29eb-126">Visual Basic automatically calls a property's `Set` procedure when an assignment statement provides a value to be stored in the property.</span></span>  
  
 <span data-ttu-id="c29eb-127">Visual Basic `Set` 在属性分配过程中将参数传递给过程。</span><span class="sxs-lookup"><span data-stu-id="c29eb-127">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="c29eb-128">如果没有为提供参数 `Set` ，集成开发环境（IDE）将使用名为的隐式参数 `value` 。</span><span class="sxs-lookup"><span data-stu-id="c29eb-128">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="c29eb-129">参数保留要赋给属性的值。</span><span class="sxs-lookup"><span data-stu-id="c29eb-129">The parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="c29eb-130">通常将此值存储在私有本地变量中，并在 `Get` 调用过程时返回。</span><span class="sxs-lookup"><span data-stu-id="c29eb-130">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
 <span data-ttu-id="c29eb-131">属性声明的主体只能在 `Get` `Set` [property 语句](property-statement.md)和语句之间包含属性的和过程 `End Property` 。</span><span class="sxs-lookup"><span data-stu-id="c29eb-131">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="c29eb-132">它无法存储这些过程以外的任何内容。</span><span class="sxs-lookup"><span data-stu-id="c29eb-132">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="c29eb-133">特别是，它无法存储属性的当前值。</span><span class="sxs-lookup"><span data-stu-id="c29eb-133">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="c29eb-134">您必须将此值存储在属性的外部，因为如果将其存储在任一属性过程中，则其他属性过程将无法访问它。</span><span class="sxs-lookup"><span data-stu-id="c29eb-134">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="c29eb-135">常见的方法是将值存储在与属性在同一级别上声明的[私有](../modifiers/private.md)变量中。</span><span class="sxs-lookup"><span data-stu-id="c29eb-135">The usual approach is to store the value in a [Private](../modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="c29eb-136">必须在应用的 `Set` 属性中定义一个过程。</span><span class="sxs-lookup"><span data-stu-id="c29eb-136">You must define a `Set` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="c29eb-137">此 `Set` 过程默认为其包含属性的访问级别，除非你 `accessmodifier` 在语句中使用 `Set` 。</span><span class="sxs-lookup"><span data-stu-id="c29eb-137">The `Set` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Set` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="c29eb-138">规则</span><span class="sxs-lookup"><span data-stu-id="c29eb-138">Rules</span></span>  
  
- <span data-ttu-id="c29eb-139">**混合访问级别。**</span><span class="sxs-lookup"><span data-stu-id="c29eb-139">**Mixed Access Levels.**</span></span> <span data-ttu-id="c29eb-140">如果要定义读写属性，则可以选择为或过程指定不同的访问级别 `Get` `Set` ，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="c29eb-140">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="c29eb-141">如果执行此操作，则过程访问级别必须比属性的访问级别更严格。</span><span class="sxs-lookup"><span data-stu-id="c29eb-141">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="c29eb-142">例如，如果声明了属性 `Friend` ，则可以声明该 `Set` 过程 `Private` ，而不是 `Public` 。</span><span class="sxs-lookup"><span data-stu-id="c29eb-142">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="c29eb-143">如果要定义 `WriteOnly` 属性，则该 `Set` 过程表示整个属性。</span><span class="sxs-lookup"><span data-stu-id="c29eb-143">If you are defining a `WriteOnly` property, the `Set` procedure represents the entire property.</span></span> <span data-ttu-id="c29eb-144">不能为声明不同的访问级别 `Set` ，因为这会为属性设置两个访问级别。</span><span class="sxs-lookup"><span data-stu-id="c29eb-144">You cannot declare a different access level for `Set`, because that would set two access levels for the property.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="c29eb-145">行为</span><span class="sxs-lookup"><span data-stu-id="c29eb-145">Behavior</span></span>  
  
- <span data-ttu-id="c29eb-146">**从属性过程返回。**</span><span class="sxs-lookup"><span data-stu-id="c29eb-146">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="c29eb-147">当 `Set` 过程返回到调用代码时，执行将在提供要存储的值的语句之后继续执行。</span><span class="sxs-lookup"><span data-stu-id="c29eb-147">When the `Set` procedure returns to the calling code, execution continues following the statement that provided the value to be stored.</span></span>  
  
     <span data-ttu-id="c29eb-148">`Set`属性过程可以使用[Return 语句](return-statement.md)或[Exit 语句](exit-statement.md)返回。</span><span class="sxs-lookup"><span data-stu-id="c29eb-148">`Set` property procedures can return using either the [Return Statement](return-statement.md) or the [Exit Statement](exit-statement.md).</span></span>  
  
     <span data-ttu-id="c29eb-149">`Exit Property`和 `Return` 语句导致直接从属性过程退出。</span><span class="sxs-lookup"><span data-stu-id="c29eb-149">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="c29eb-150">任意数量的 `Exit Property` 和 `Return` 语句可以出现在过程中的任何位置，并且可以混合使用 `Exit Property` 和 `Return` 语句。</span><span class="sxs-lookup"><span data-stu-id="c29eb-150">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c29eb-151">示例</span><span class="sxs-lookup"><span data-stu-id="c29eb-151">Example</span></span>  
 <span data-ttu-id="c29eb-152">下面的示例使用 `Set` 语句设置属性的值。</span><span class="sxs-lookup"><span data-stu-id="c29eb-152">The following example uses the `Set` statement to set the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="c29eb-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c29eb-153">See also</span></span>

- [<span data-ttu-id="c29eb-154">Get 语句</span><span class="sxs-lookup"><span data-stu-id="c29eb-154">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="c29eb-155">Property Statement</span><span class="sxs-lookup"><span data-stu-id="c29eb-155">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="c29eb-156">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="c29eb-156">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="c29eb-157">Property 过程</span><span class="sxs-lookup"><span data-stu-id="c29eb-157">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
