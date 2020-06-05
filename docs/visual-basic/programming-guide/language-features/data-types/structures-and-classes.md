---
title: 结构和类
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], vs. structures
- structures [Visual Basic]
- classes [Visual Basic]
- structures [Visual Basic], compared to classes
- structures [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
ms.openlocfilehash: d252d9216a9b825ad0663a5779d7ce7f81fa9011
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393567"
---
# <a name="structures-and-classes-visual-basic"></a><span data-ttu-id="3512c-102">结构和类 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3512c-102">Structures and Classes (Visual Basic)</span></span>
<span data-ttu-id="3512c-103">Visual Basic 统一了结构和类的语法，因此，这两个实体支持大多数相同的功能。</span><span class="sxs-lookup"><span data-stu-id="3512c-103">Visual Basic unifies the syntax for structures and classes, with the result that both entities support most of the same features.</span></span> <span data-ttu-id="3512c-104">但结构和类之间也存在重要差异。</span><span class="sxs-lookup"><span data-stu-id="3512c-104">However, there are also important differences between structures and classes.</span></span>  
  
 <span data-ttu-id="3512c-105">类的优点是引用类型，传递引用比将结构变量传递到其所有数据更有效。</span><span class="sxs-lookup"><span data-stu-id="3512c-105">Classes have the advantage of being reference types — passing a reference is more efficient than passing a structure variable with all its data.</span></span> <span data-ttu-id="3512c-106">另一方面，结构不需要在全局堆上分配内存。</span><span class="sxs-lookup"><span data-stu-id="3512c-106">On the other hand, structures do not require allocation of memory on the global heap.</span></span>  
  
 <span data-ttu-id="3512c-107">由于不能从结构继承，因此结构应仅用于不需要扩展的对象。</span><span class="sxs-lookup"><span data-stu-id="3512c-107">Because you cannot inherit from a structure, structures should be used only for objects that do not need to be extended.</span></span> <span data-ttu-id="3512c-108">如果要创建的对象的实例大小较小，请使用结构，并考虑类与结构的性能特征。</span><span class="sxs-lookup"><span data-stu-id="3512c-108">Use structures when the object you wish to create has a small instance size, and take into account the performance characteristics of classes versus structures.</span></span>  
  
## <a name="similarities"></a><span data-ttu-id="3512c-109">相似性</span><span class="sxs-lookup"><span data-stu-id="3512c-109">Similarities</span></span>  
 <span data-ttu-id="3512c-110">结构和类在以下方面类似：</span><span class="sxs-lookup"><span data-stu-id="3512c-110">Structures and classes are similar in the following respects:</span></span>  
  
- <span data-ttu-id="3512c-111">两者都是*容器*类型，这意味着它们包含其他类型作为成员。</span><span class="sxs-lookup"><span data-stu-id="3512c-111">Both are *container* types, meaning that they contain other types as members.</span></span>  
  
- <span data-ttu-id="3512c-112">两者都具有成员，其中可以包含构造函数、方法、属性、字段、常量、枚举、事件和事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="3512c-112">Both have members, which can include constructors, methods, properties, fields, constants, enumerations, events, and event handlers.</span></span> <span data-ttu-id="3512c-113">但是，不要将这些成员与结构的已声明*元素*混淆。</span><span class="sxs-lookup"><span data-stu-id="3512c-113">However, do not confuse these members with the declared *elements* of a structure.</span></span>  
  
- <span data-ttu-id="3512c-114">两者的成员可以具有不同的访问级别。</span><span class="sxs-lookup"><span data-stu-id="3512c-114">Members of both can have individualized access levels.</span></span> <span data-ttu-id="3512c-115">例如，一个成员可以声明， `Public` 另一个成员 `Private` 。</span><span class="sxs-lookup"><span data-stu-id="3512c-115">For example, one member can be declared `Public` and another `Private`.</span></span>  
  
- <span data-ttu-id="3512c-116">两者均可实现接口。</span><span class="sxs-lookup"><span data-stu-id="3512c-116">Both can implement interfaces.</span></span>  
  
- <span data-ttu-id="3512c-117">两者都可以具有共享构造函数（带有或不带参数）。</span><span class="sxs-lookup"><span data-stu-id="3512c-117">Both can have shared constructors, with or without parameters.</span></span>  
  
- <span data-ttu-id="3512c-118">两者都可以公开*默认属性*，前提是该属性至少采用一个参数。</span><span class="sxs-lookup"><span data-stu-id="3512c-118">Both can expose a *default property*, provided that property takes at least one parameter.</span></span>  
  
- <span data-ttu-id="3512c-119">两者都可以声明和引发事件，并且两者都可以声明委托。</span><span class="sxs-lookup"><span data-stu-id="3512c-119">Both can declare and raise events, and both can declare delegates.</span></span>  
  
## <a name="differences"></a><span data-ttu-id="3512c-120">差异</span><span class="sxs-lookup"><span data-stu-id="3512c-120">Differences</span></span>  
 <span data-ttu-id="3512c-121">结构和类在以下方面有所不同：</span><span class="sxs-lookup"><span data-stu-id="3512c-121">Structures and classes differ in the following particulars:</span></span>  
  
- <span data-ttu-id="3512c-122">结构是*值类型*;类是*引用类型*。</span><span class="sxs-lookup"><span data-stu-id="3512c-122">Structures are *value types*; classes are *reference types*.</span></span> <span data-ttu-id="3512c-123">结构类型的变量包含结构的数据，而不是包含对作为类类型的数据的引用。</span><span class="sxs-lookup"><span data-stu-id="3512c-123">A variable of a structure type contains the structure's data, rather than containing a reference to the data as a class type does.</span></span>  
  
- <span data-ttu-id="3512c-124">结构使用堆栈分配;类使用堆分配。</span><span class="sxs-lookup"><span data-stu-id="3512c-124">Structures use stack allocation; classes use heap allocation.</span></span>  
  
- <span data-ttu-id="3512c-125">默认情况下，所有结构元素都是默认的; 默认情况下 `Public` ，类变量和常量是 `Private` 其他类成员 `Public` 。</span><span class="sxs-lookup"><span data-stu-id="3512c-125">All structure elements are `Public` by default; class variables and constants are `Private` by default, while other class members are `Public` by default.</span></span> <span data-ttu-id="3512c-126">类成员的这种行为提供与 Visual Basic 6.0 系统的默认值的兼容性。</span><span class="sxs-lookup"><span data-stu-id="3512c-126">This behavior for class members provides compatibility with the Visual Basic 6.0 system of defaults.</span></span>  
  
- <span data-ttu-id="3512c-127">结构中必须至少有一个非共享变量或非共享的非自定义事件元素;类可以完全为空。</span><span class="sxs-lookup"><span data-stu-id="3512c-127">A structure must have at least one nonshared variable or nonshared, noncustom event element; a class can be completely empty.</span></span>  
  
- <span data-ttu-id="3512c-128">不能将结构元素声明为 `Protected` ; 类成员可以。</span><span class="sxs-lookup"><span data-stu-id="3512c-128">Structure elements cannot be declared as `Protected`; class members can.</span></span>  
  
- <span data-ttu-id="3512c-129">仅当结构过程是[共享](../../../language-reference/modifiers/shared.md) `Sub` 过程，并且仅通过[AddHandler 语句](../../../language-reference/statements/addhandler-statement.md)的方式处理时，结构过程才能处理事件; 任何类过程都可以使用[Handles](../../../language-reference/statements/handles-clause.md)关键字或语句处理事件 `AddHandler` 。</span><span class="sxs-lookup"><span data-stu-id="3512c-129">A structure procedure can handle events only if it is a [Shared](../../../language-reference/modifiers/shared.md)`Sub` procedure, and only by means of the [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md); any class procedure can handle events, using either the [Handles](../../../language-reference/statements/handles-clause.md) keyword or the `AddHandler` statement.</span></span> <span data-ttu-id="3512c-130">有关详细信息，请参阅[事件](../events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="3512c-130">For more information, see [Events](../events/index.md).</span></span>  
  
- <span data-ttu-id="3512c-131">结构变量声明不能为数组指定初始值设定项或初始大小;类变量声明可以。</span><span class="sxs-lookup"><span data-stu-id="3512c-131">Structure variable declarations cannot specify initializers or initial sizes for arrays; class variable declarations can.</span></span>  
  
- <span data-ttu-id="3512c-132">结构隐式继承自 <xref:System.ValueType?displayProperty=nameWithType> 类，且不能从任何其他类型继承; 类可以继承自以外的任何类 <xref:System.ValueType?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="3512c-132">Structures implicitly inherit from the <xref:System.ValueType?displayProperty=nameWithType> class and cannot inherit from any other type; classes can inherit from any class or classes other than <xref:System.ValueType?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="3512c-133">结构不可继承;类为。</span><span class="sxs-lookup"><span data-stu-id="3512c-133">Structures are not inheritable; classes are.</span></span>  
  
- <span data-ttu-id="3512c-134">结构永远不会终止，因此，公共语言运行时（CLR）从不会对 <xref:System.Object.Finalize%2A> 任何结构调用方法; 类由垃圾回收器（GC）终止，后者 <xref:System.Object.Finalize%2A> 在检测到没有剩余的活动引用时对类调用。</span><span class="sxs-lookup"><span data-stu-id="3512c-134">Structures are never terminated, so the common language runtime (CLR) never calls the <xref:System.Object.Finalize%2A> method on any structure; classes are terminated by the garbage collector (GC), which calls <xref:System.Object.Finalize%2A> on a class when it detects there are no active references remaining.</span></span>  
  
- <span data-ttu-id="3512c-135">结构不需要构造函数;类。</span><span class="sxs-lookup"><span data-stu-id="3512c-135">A structure does not require a constructor; a class does.</span></span>  
  
- <span data-ttu-id="3512c-136">仅当结构使用参数时，才可具有非共享构造函数;类可以具有或不带参数。</span><span class="sxs-lookup"><span data-stu-id="3512c-136">Structures can have nonshared constructors only if they take parameters; classes can have them with or without parameters.</span></span>  
  
 <span data-ttu-id="3512c-137">每个结构都具有一个不带参数的隐式公共构造函数。</span><span class="sxs-lookup"><span data-stu-id="3512c-137">Every structure has an implicit public constructor without parameters.</span></span> <span data-ttu-id="3512c-138">此构造函数将结构的所有数据元素初始化为其默认值。</span><span class="sxs-lookup"><span data-stu-id="3512c-138">This constructor initializes all the structure's data elements to their default values.</span></span> <span data-ttu-id="3512c-139">不能重新定义此行为。</span><span class="sxs-lookup"><span data-stu-id="3512c-139">You cannot redefine this behavior.</span></span>  
  
## <a name="instances-and-variables"></a><span data-ttu-id="3512c-140">实例和变量</span><span class="sxs-lookup"><span data-stu-id="3512c-140">Instances and Variables</span></span>  
 <span data-ttu-id="3512c-141">由于结构是值类型，因此每个结构变量将永久绑定到单个结构实例。</span><span class="sxs-lookup"><span data-stu-id="3512c-141">Because structures are value types, each structure variable is permanently bound to an individual structure instance.</span></span> <span data-ttu-id="3512c-142">但类是引用类型，而对象变量可在不同时间引用各种类实例。</span><span class="sxs-lookup"><span data-stu-id="3512c-142">But classes are reference types, and an object variable can refer to various class instances at different times.</span></span> <span data-ttu-id="3512c-143">这种区分会按以下方式影响结构和类的使用：</span><span class="sxs-lookup"><span data-stu-id="3512c-143">This distinction affects your usage of structures and classes in the following ways:</span></span>  
  
- <span data-ttu-id="3512c-144">**起始.**</span><span class="sxs-lookup"><span data-stu-id="3512c-144">**Initialization.**</span></span> <span data-ttu-id="3512c-145">结构变量使用结构的无参数构造函数隐式包括元素的初始化。</span><span class="sxs-lookup"><span data-stu-id="3512c-145">A structure variable implicitly includes an initialization of the elements using the structure's parameterless constructor.</span></span> <span data-ttu-id="3512c-146">因此， `Dim s As struct1` 等效于 `Dim s As struct1 = New struct1()` 。</span><span class="sxs-lookup"><span data-stu-id="3512c-146">Therefore, `Dim s As struct1` is equivalent to `Dim s As struct1 = New struct1()`.</span></span>  
  
- <span data-ttu-id="3512c-147">**分配变量。**</span><span class="sxs-lookup"><span data-stu-id="3512c-147">**Assigning Variables.**</span></span> <span data-ttu-id="3512c-148">将一个结构变量分配给另一个结构变量或将结构实例传递给过程参数时，所有变量元素的当前值都将复制到新结构。</span><span class="sxs-lookup"><span data-stu-id="3512c-148">When you assign one structure variable to another, or pass a structure instance to a procedure argument, the current values of all the variable elements are copied to the new structure.</span></span> <span data-ttu-id="3512c-149">当您将一个对象变量分配给另一个对象变量，或将一个对象变量传递给某个过程时，只会复制引用指针。</span><span class="sxs-lookup"><span data-stu-id="3512c-149">When you assign one object variable to another, or pass an object variable to a procedure, only the reference pointer is copied.</span></span>  
  
- <span data-ttu-id="3512c-150">**不分配任何内容。**</span><span class="sxs-lookup"><span data-stu-id="3512c-150">**Assigning Nothing.**</span></span> <span data-ttu-id="3512c-151">您可以将值[Nothing](../../../language-reference/nothing.md)赋给结构变量，但该实例继续与变量关联。</span><span class="sxs-lookup"><span data-stu-id="3512c-151">You can assign the value [Nothing](../../../language-reference/nothing.md) to a structure variable, but the instance continues to be associated with the variable.</span></span> <span data-ttu-id="3512c-152">尽管变量元素由赋值重新初始化，仍可以调用其方法并访问其数据元素。</span><span class="sxs-lookup"><span data-stu-id="3512c-152">You can still call its methods and access its data elements, although variable elements are reinitialized by the assignment.</span></span>  
  
     <span data-ttu-id="3512c-153">与此相反，如果您将一个对象变量设置为 `Nothing` ，则将其与任何类实例取消关联，并且您无法通过该变量访问任何成员，除非您向其分配了其他实例。</span><span class="sxs-lookup"><span data-stu-id="3512c-153">In contrast, if you set an object variable to `Nothing`, you dissociate it from any class instance, and you cannot access any members through the variable until you assign another instance to it.</span></span>  
  
- <span data-ttu-id="3512c-154">**多个实例。**</span><span class="sxs-lookup"><span data-stu-id="3512c-154">**Multiple Instances.**</span></span> <span data-ttu-id="3512c-155">对象变量可在不同时间分配给它的不同类实例，而多个对象变量可同时引用相同的类实例。</span><span class="sxs-lookup"><span data-stu-id="3512c-155">An object variable can have different class instances assigned to it at different times, and several object variables can refer to the same class instance at the same time.</span></span> <span data-ttu-id="3512c-156">对类成员的值所做的更改会在通过指向同一实例的另一个变量进行访问时影响这些成员。</span><span class="sxs-lookup"><span data-stu-id="3512c-156">Changes you make to the values of class members affect those members when accessed through another variable pointing to the same instance.</span></span>  
  
     <span data-ttu-id="3512c-157">但是，结构元素在其自己的实例中是隔离的。</span><span class="sxs-lookup"><span data-stu-id="3512c-157">Structure elements, however, are isolated within their own instance.</span></span> <span data-ttu-id="3512c-158">对其值所做的更改不会反映在其他任何结构变量中，即使在同一声明的其他实例中也是如此 `Structure` 。</span><span class="sxs-lookup"><span data-stu-id="3512c-158">Changes to their values are not reflected in any other structure variables, even in other instances of the same `Structure` declaration.</span></span>  
  
- <span data-ttu-id="3512c-159">**等于.**</span><span class="sxs-lookup"><span data-stu-id="3512c-159">**Equality.**</span></span> <span data-ttu-id="3512c-160">必须使用逐个元素测试来执行两个结构的相等性测试。</span><span class="sxs-lookup"><span data-stu-id="3512c-160">Equality testing of two structures must be performed with an element-by-element test.</span></span> <span data-ttu-id="3512c-161">可以使用方法比较两个对象变量 <xref:System.Object.Equals%2A> 。</span><span class="sxs-lookup"><span data-stu-id="3512c-161">Two object variables can be compared using the <xref:System.Object.Equals%2A> method.</span></span> <span data-ttu-id="3512c-162"><xref:System.Object.Equals%2A>指示两个变量是否指向同一个实例。</span><span class="sxs-lookup"><span data-stu-id="3512c-162"><xref:System.Object.Equals%2A> indicates whether the two variables point to the same instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3512c-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3512c-163">See also</span></span>

- [<span data-ttu-id="3512c-164">数据类型</span><span class="sxs-lookup"><span data-stu-id="3512c-164">Data Types</span></span>](index.md)
- [<span data-ttu-id="3512c-165">复合数据类型</span><span class="sxs-lookup"><span data-stu-id="3512c-165">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="3512c-166">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="3512c-166">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="3512c-167">结构</span><span class="sxs-lookup"><span data-stu-id="3512c-167">Structures</span></span>](structures.md)
- [<span data-ttu-id="3512c-168">数据类型疑难解答</span><span class="sxs-lookup"><span data-stu-id="3512c-168">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="3512c-169">结构和其他编程元素</span><span class="sxs-lookup"><span data-stu-id="3512c-169">Structures and Other Programming Elements</span></span>](structures-and-other-programming-elements.md)
- [<span data-ttu-id="3512c-170">对象和类</span><span class="sxs-lookup"><span data-stu-id="3512c-170">Objects and Classes</span></span>](../objects-and-classes/index.md)
