---
title: 密钥
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
ms.openlocfilehash: 582ed5bb67b9c7504e736710aa4649cffb12ef45
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867998"
---
# <a name="key-visual-basic"></a><span data-ttu-id="1f00b-102">Key (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f00b-102">Key (Visual Basic)</span></span>

<span data-ttu-id="1f00b-103">关键字可用于 `Key` 指定匿名类型的属性的行为。</span><span class="sxs-lookup"><span data-stu-id="1f00b-103">The `Key` keyword enables you to specify behavior for properties of anonymous types.</span></span> <span data-ttu-id="1f00b-104">只有指定为键属性的属性才会在匿名类型实例与哈希代码值的计算之间进行相等性测试。</span><span class="sxs-lookup"><span data-stu-id="1f00b-104">Only properties you designate as key properties participate in tests of equality between anonymous type instances, or calculation of hash code values.</span></span> <span data-ttu-id="1f00b-105">键属性的值不能更改。</span><span class="sxs-lookup"><span data-stu-id="1f00b-105">The values of key properties cannot be changed.</span></span>  
  
 <span data-ttu-id="1f00b-106">将匿名类型的属性指定为键属性，方法是在 `Key` 初始化列表中将关键字置于其声明之前。</span><span class="sxs-lookup"><span data-stu-id="1f00b-106">You designate a property of an anonymous type as a key property by placing the keyword `Key` in front of its declaration in the initialization list.</span></span> <span data-ttu-id="1f00b-107">在下面的示例中， `Airline` 和 `FlightNo` 是键属性，但 `Gate` 不是。</span><span class="sxs-lookup"><span data-stu-id="1f00b-107">In the following example, `Airline` and `FlightNo` are key properties, but `Gate` is not.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#26)]  
  
 <span data-ttu-id="1f00b-108">创建新的匿名类型时，它会直接从继承 <xref:System.Object> 。</span><span class="sxs-lookup"><span data-stu-id="1f00b-108">When a new anonymous type is created, it inherits directly from <xref:System.Object>.</span></span> <span data-ttu-id="1f00b-109">编译器会重写三个继承成员： <xref:System.Object.Equals%2A> 、 <xref:System.Object.GetHashCode%2A> 和 <xref:System.Object.ToString%2A> 。</span><span class="sxs-lookup"><span data-stu-id="1f00b-109">The compiler overrides three inherited members: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="1f00b-110">为和生成的替代代码 <xref:System.Object.Equals%2A> <xref:System.Object.GetHashCode%2A> 基于键属性。</span><span class="sxs-lookup"><span data-stu-id="1f00b-110">The override code that is produced for <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> is based on key properties.</span></span> <span data-ttu-id="1f00b-111">如果类型中没有键属性，则不会 <xref:System.Object.GetHashCode%2A> <xref:System.Object.Equals%2A> 重写这些属性。</span><span class="sxs-lookup"><span data-stu-id="1f00b-111">If there are no key properties in the type, <xref:System.Object.GetHashCode%2A> and <xref:System.Object.Equals%2A> are not overridden.</span></span>  
  
## <a name="equality"></a><span data-ttu-id="1f00b-112">等式</span><span class="sxs-lookup"><span data-stu-id="1f00b-112">Equality</span></span>  

 <span data-ttu-id="1f00b-113">如果两个匿名类型实例是同一类型的实例，并且它们的键属性的值相等，则这两个实例相等。</span><span class="sxs-lookup"><span data-stu-id="1f00b-113">Two anonymous type instances are equal if they are instances of the same type and if the values of their key properties are equal.</span></span> <span data-ttu-id="1f00b-114">在下面的示例中，与 `flight2` `flight1` 上一示例中的相等，因为它们是相同匿名类型的实例，并且它们的键属性具有匹配的值。</span><span class="sxs-lookup"><span data-stu-id="1f00b-114">In the following examples, `flight2` is equal to `flight1` from the previous example because they are instances of the same anonymous type and they have matching values for their key properties.</span></span> <span data-ttu-id="1f00b-115">但是， `flight3` 不等于， `flight1` 因为它的键属性具有不同的值 `FlightNo` 。</span><span class="sxs-lookup"><span data-stu-id="1f00b-115">However, `flight3` is not equal to `flight1` because it has a different value for a key property, `FlightNo`.</span></span> <span data-ttu-id="1f00b-116">实例 `flight4` 的类型 `flight1` 不同，因为它们将不同的属性指定为键属性。</span><span class="sxs-lookup"><span data-stu-id="1f00b-116">Instance `flight4` is not the same type as `flight1` because they designate different properties as key properties.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#27)]  
  
 <span data-ttu-id="1f00b-117">如果仅用非键属性声明了两个实例，则在名称、类型、顺序和值上相同，这两个实例不相等。</span><span class="sxs-lookup"><span data-stu-id="1f00b-117">If two instances are declared with only non-key properties, identical in name, type, order, and value, the two instances are not equal.</span></span> <span data-ttu-id="1f00b-118">没有键属性的实例仅与自身相等。</span><span class="sxs-lookup"><span data-stu-id="1f00b-118">An instance without key properties is equal only to itself.</span></span>  
  
 <span data-ttu-id="1f00b-119">有关这两个匿名类型实例是同一匿名类型的实例的详细信息，请参阅 [匿名类型](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="1f00b-119">For more information about the conditions under which two anonymous type instances are instances of the same anonymous type, see [Anonymous Types](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="hash-code-calculation"></a><span data-ttu-id="1f00b-120">哈希代码计算</span><span class="sxs-lookup"><span data-stu-id="1f00b-120">Hash Code Calculation</span></span>  

 <span data-ttu-id="1f00b-121">与一样 <xref:System.Object.Equals%2A> ，在中为匿名类型定义的哈希函数 <xref:System.Object.GetHashCode%2A> 基于该类型的键属性。</span><span class="sxs-lookup"><span data-stu-id="1f00b-121">Like <xref:System.Object.Equals%2A>, the hash function that is defined in <xref:System.Object.GetHashCode%2A> for an anonymous type is based on the key properties of the type.</span></span> <span data-ttu-id="1f00b-122">下面的示例演示键属性和哈希代码值之间的交互。</span><span class="sxs-lookup"><span data-stu-id="1f00b-122">The following examples show the interaction between key properties and hash code values.</span></span>  
  
 <span data-ttu-id="1f00b-123">与所有键属性具有相同值的匿名类型的实例具有相同的哈希代码值，即使非键属性没有匹配的值也是如此。</span><span class="sxs-lookup"><span data-stu-id="1f00b-123">Instances of an anonymous type that have the same values for all key properties have the same hash code value, even if non-key properties do not have matching values.</span></span> <span data-ttu-id="1f00b-124">下面的语句将返回 `True`。</span><span class="sxs-lookup"><span data-stu-id="1f00b-124">The following statement returns `True`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#37)]  
  
 <span data-ttu-id="1f00b-125">对于一个或多个键属性具有不同值的匿名类型的实例具有不同的哈希代码值。</span><span class="sxs-lookup"><span data-stu-id="1f00b-125">Instances of an anonymous type that have different values for one or more key properties have different hash code values.</span></span> <span data-ttu-id="1f00b-126">下面的语句将返回 `False`。</span><span class="sxs-lookup"><span data-stu-id="1f00b-126">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#38)]  
  
 <span data-ttu-id="1f00b-127">将不同属性指定为键属性的匿名类型的实例不是相同类型的实例。</span><span class="sxs-lookup"><span data-stu-id="1f00b-127">Instances of anonymous types that designate different properties as key properties are not instances of the same type.</span></span> <span data-ttu-id="1f00b-128">即使所有属性的名称和值相同，它们也具有不同的哈希代码值。</span><span class="sxs-lookup"><span data-stu-id="1f00b-128">They have different hash code values even when the names and values of all properties are the same.</span></span> <span data-ttu-id="1f00b-129">下面的语句将返回 `False`。</span><span class="sxs-lookup"><span data-stu-id="1f00b-129">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#39)]  
  
## <a name="read-only-values"></a><span data-ttu-id="1f00b-130">只读值</span><span class="sxs-lookup"><span data-stu-id="1f00b-130">Read-Only Values</span></span>  

 <span data-ttu-id="1f00b-131">键属性的值不能更改。</span><span class="sxs-lookup"><span data-stu-id="1f00b-131">The values of key properties cannot be changed.</span></span> <span data-ttu-id="1f00b-132">例如，在 `flight1` 前面的示例中， `Airline` 和 `FlightNo` 字段是只读的，但 `Gate` 可以更改。</span><span class="sxs-lookup"><span data-stu-id="1f00b-132">For example, in `flight1` in the earlier examples, the `Airline` and `FlightNo` fields are read-only, but `Gate` can be changed.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="1f00b-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1f00b-133">See also</span></span>

- [<span data-ttu-id="1f00b-134">匿名类型定义</span><span class="sxs-lookup"><span data-stu-id="1f00b-134">Anonymous Type Definition</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [<span data-ttu-id="1f00b-135">如何：推断匿名类型声明中的属性名和类型</span><span class="sxs-lookup"><span data-stu-id="1f00b-135">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="1f00b-136">匿名类型</span><span class="sxs-lookup"><span data-stu-id="1f00b-136">Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
