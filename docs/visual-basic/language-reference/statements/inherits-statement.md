---
title: Inherits Statement
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: 5d88a01f90bc91a88229d19aa2368f8c71075b2f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404494"
---
# <a name="inherits-statement"></a><span data-ttu-id="3eaa2-102">Inherits Statement</span><span class="sxs-lookup"><span data-stu-id="3eaa2-102">Inherits Statement</span></span>
<span data-ttu-id="3eaa2-103">导致当前类或接口继承其他类或接口集的属性、变量、属性、过程和事件。</span><span class="sxs-lookup"><span data-stu-id="3eaa2-103">Causes the current class or interface to inherit the attributes, variables, properties, procedures, and events from another class or set of interfaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eaa2-104">语法</span><span class="sxs-lookup"><span data-stu-id="3eaa2-104">Syntax</span></span>  
  
```vb  
Inherits basetypenames  
```  
  
## <a name="parts"></a><span data-ttu-id="3eaa2-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="3eaa2-105">Parts</span></span>  
  
|<span data-ttu-id="3eaa2-106">术语</span><span class="sxs-lookup"><span data-stu-id="3eaa2-106">Term</span></span>|<span data-ttu-id="3eaa2-107">定义</span><span class="sxs-lookup"><span data-stu-id="3eaa2-107">Definition</span></span>|  
|---|---|  
|`basetypenames`|<span data-ttu-id="3eaa2-108">必需。</span><span class="sxs-lookup"><span data-stu-id="3eaa2-108">Required.</span></span> <span data-ttu-id="3eaa2-109">此类派生自的类的名称。</span><span class="sxs-lookup"><span data-stu-id="3eaa2-109">The name of the class from which this class derives.</span></span><br /><br /> <span data-ttu-id="3eaa2-110">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="3eaa2-110">-or-</span></span><br /><br /> <span data-ttu-id="3eaa2-111">此接口派生自的接口的名称。</span><span class="sxs-lookup"><span data-stu-id="3eaa2-111">The names of the interfaces from which this interface derives.</span></span> <span data-ttu-id="3eaa2-112">使用逗号分隔多个名称。</span><span class="sxs-lookup"><span data-stu-id="3eaa2-112">Use commas to separate multiple names.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3eaa2-113">备注</span><span class="sxs-lookup"><span data-stu-id="3eaa2-113">Remarks</span></span>  
 <span data-ttu-id="3eaa2-114">如果使用，则 `Inherits` 语句必须是类或接口定义中的第一个非空白非注释行。</span><span class="sxs-lookup"><span data-stu-id="3eaa2-114">If used, the `Inherits` statement must be the first non-blank, non-comment line in a class or interface definition.</span></span> <span data-ttu-id="3eaa2-115">它应紧跟 `Class` 或 `Interface` 语句。</span><span class="sxs-lookup"><span data-stu-id="3eaa2-115">It should immediately follow the `Class` or `Interface` statement.</span></span>  
  
 <span data-ttu-id="3eaa2-116">`Inherits`只能在类或接口中使用。</span><span class="sxs-lookup"><span data-stu-id="3eaa2-116">You can use `Inherits` only in a class or interface.</span></span> <span data-ttu-id="3eaa2-117">这意味着继承的声明上下文不能是源文件、命名空间、结构、模块、过程或块。</span><span class="sxs-lookup"><span data-stu-id="3eaa2-117">This means the declaration context for an inheritance cannot be a source file, namespace, structure, module, procedure, or block.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="3eaa2-118">规则</span><span class="sxs-lookup"><span data-stu-id="3eaa2-118">Rules</span></span>  
  
- <span data-ttu-id="3eaa2-119">**类继承。**</span><span class="sxs-lookup"><span data-stu-id="3eaa2-119">**Class Inheritance.**</span></span> <span data-ttu-id="3eaa2-120">如果类使用 `Inherits` 语句，则只能指定一个基类。</span><span class="sxs-lookup"><span data-stu-id="3eaa2-120">If a class uses the `Inherits` statement, you can specify only one base class.</span></span>  
  
     <span data-ttu-id="3eaa2-121">类不能从嵌套在它中的类继承。</span><span class="sxs-lookup"><span data-stu-id="3eaa2-121">A class cannot inherit from a class nested within it.</span></span>  
  
- <span data-ttu-id="3eaa2-122">**接口继承。**</span><span class="sxs-lookup"><span data-stu-id="3eaa2-122">**Interface Inheritance.**</span></span> <span data-ttu-id="3eaa2-123">如果接口使用 `Inherits` 语句，则可以指定一个或多个基接口。</span><span class="sxs-lookup"><span data-stu-id="3eaa2-123">If an interface uses the `Inherits` statement, you can specify one or more base interfaces.</span></span> <span data-ttu-id="3eaa2-124">即使两个接口都定义了具有相同名称的成员，也可以从两个接口继承。</span><span class="sxs-lookup"><span data-stu-id="3eaa2-124">You can inherit from two interfaces even if they each define a member with the same name.</span></span> <span data-ttu-id="3eaa2-125">如果这样做，则实现代码必须使用名称限定来指定要实现的成员。</span><span class="sxs-lookup"><span data-stu-id="3eaa2-125">If you do so, the implementing code must use name qualification to specify which member it is implementing.</span></span>  
  
     <span data-ttu-id="3eaa2-126">接口不能从具有限制性更强的访问级别的其他接口继承。</span><span class="sxs-lookup"><span data-stu-id="3eaa2-126">An interface cannot inherit from another interface with a more restrictive access level.</span></span> <span data-ttu-id="3eaa2-127">例如， `Public` 接口无法从 `Friend` 接口继承。</span><span class="sxs-lookup"><span data-stu-id="3eaa2-127">For example, a `Public` interface cannot inherit from a `Friend` interface.</span></span>  
  
     <span data-ttu-id="3eaa2-128">接口不能从嵌套在它内的接口继承。</span><span class="sxs-lookup"><span data-stu-id="3eaa2-128">An interface cannot inherit from an interface nested within it.</span></span>  
  
 <span data-ttu-id="3eaa2-129">.NET Framework 中的类继承示例是 <xref:System.ArgumentException> 类，该类继承自 <xref:System.SystemException> 类。</span><span class="sxs-lookup"><span data-stu-id="3eaa2-129">An example of class inheritance in the .NET Framework is the <xref:System.ArgumentException> class, which inherits from the <xref:System.SystemException> class.</span></span> <span data-ttu-id="3eaa2-130">这将提供 <xref:System.ArgumentException> 系统异常所需的所有预定义属性和过程，如 <xref:System.Exception.Message%2A> 属性和 <xref:System.Exception.ToString%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="3eaa2-130">This provides to <xref:System.ArgumentException> all the predefined properties and procedures required by system exceptions, such as the <xref:System.Exception.Message%2A> property and the <xref:System.Exception.ToString%2A> method.</span></span>  
  
 <span data-ttu-id="3eaa2-131">.NET Framework 中的接口继承示例是 <xref:System.Collections.ICollection> 从接口继承的接口 <xref:System.Collections.IEnumerable> 。</span><span class="sxs-lookup"><span data-stu-id="3eaa2-131">An example of interface inheritance in the .NET Framework is the <xref:System.Collections.ICollection> interface, which inherits from the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="3eaa2-132">这会导致 <xref:System.Collections.ICollection> 继承遍历集合所需的枚举器的定义。</span><span class="sxs-lookup"><span data-stu-id="3eaa2-132">This causes <xref:System.Collections.ICollection> to inherit the definition of the enumerator required to traverse a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3eaa2-133">示例</span><span class="sxs-lookup"><span data-stu-id="3eaa2-133">Example</span></span>  
 <span data-ttu-id="3eaa2-134">下面的示例使用 `Inherits` 语句来显示名为的类如何 `thisClass` 继承名为的基类的所有成员 `anotherClass` 。</span><span class="sxs-lookup"><span data-stu-id="3eaa2-134">The following example uses the `Inherits` statement to show how a class named `thisClass` can inherit all the members of a base class named `anotherClass`.</span></span>  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="3eaa2-135">示例</span><span class="sxs-lookup"><span data-stu-id="3eaa2-135">Example</span></span>  
 <span data-ttu-id="3eaa2-136">下面的示例演示多个接口的继承。</span><span class="sxs-lookup"><span data-stu-id="3eaa2-136">The following example shows inheritance of multiple interfaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 <span data-ttu-id="3eaa2-137">名为的接口 `thisInterface` 现在包括 <xref:System.IComparable> 、和接口中的所有定义， <xref:System.IDisposable> <xref:System.IFormattable> 这些继承成员分别提供两个对象的特定于类型的比较，释放已分配的资源，并将对象的值表示为 `String` 。</span><span class="sxs-lookup"><span data-stu-id="3eaa2-137">The interface named `thisInterface` now includes all the definitions in the <xref:System.IComparable>, <xref:System.IDisposable>, and <xref:System.IFormattable> interfaces The inherited members provide respectively for type-specific comparison of two objects, releasing allocated resources, and expressing the value of an object as a `String`.</span></span> <span data-ttu-id="3eaa2-138">实现的类 `thisInterface` 必须实现每个基接口的每个成员。</span><span class="sxs-lookup"><span data-stu-id="3eaa2-138">A class that implements `thisInterface` must implement every member of every base interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eaa2-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3eaa2-139">See also</span></span>

- [<span data-ttu-id="3eaa2-140">MustInherit</span><span class="sxs-lookup"><span data-stu-id="3eaa2-140">MustInherit</span></span>](../modifiers/mustinherit.md)
- [<span data-ttu-id="3eaa2-141">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="3eaa2-141">NotInheritable</span></span>](../modifiers/notinheritable.md)
- [<span data-ttu-id="3eaa2-142">对象和类</span><span class="sxs-lookup"><span data-stu-id="3eaa2-142">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="3eaa2-143">继承基础知识</span><span class="sxs-lookup"><span data-stu-id="3eaa2-143">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="3eaa2-144">接口</span><span class="sxs-lookup"><span data-stu-id="3eaa2-144">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
