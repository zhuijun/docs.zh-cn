---
title: Class 语句
ms.date: 05/12/2018
f1_keywords:
- vb.Class
helpviewer_keywords:
- class modules
- Class statement [Visual Basic]
- classes [Visual Basic], fields
- fields [Visual Basic], of classes
- class types [Visual Basic], class statements
- classes [Visual Basic], creating
- classes [Visual Basic], data members
- data members [Visual Basic], of classes
ms.assetid: f2664f38-eb5a-4d4b-a374-1d041521fb6c
ms.openlocfilehash: 3b64597fcd7453c20ed295fe263eeaa8783b20ae
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866038"
---
# <a name="class-statement-visual-basic"></a><span data-ttu-id="9fa26-102">Class 语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9fa26-102">Class Statement (Visual Basic)</span></span>

<span data-ttu-id="9fa26-103">声明类的名称，并引入类所包含的变量、属性、事件和过程的定义。</span><span class="sxs-lookup"><span data-stu-id="9fa26-103">Declares the name of a class and introduces the definition of the variables, properties, events, and procedures that the class comprises.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fa26-104">语法</span><span class="sxs-lookup"><span data-stu-id="9fa26-104">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] [ Partial ] _  
Class name [ ( Of typelist ) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ statements ]  
End Class  
```  
  
## <a name="parts"></a><span data-ttu-id="9fa26-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="9fa26-105">Parts</span></span>  
  
|<span data-ttu-id="9fa26-106">术语</span><span class="sxs-lookup"><span data-stu-id="9fa26-106">Term</span></span>|<span data-ttu-id="9fa26-107">定义</span><span class="sxs-lookup"><span data-stu-id="9fa26-107">Definition</span></span>|  
|---|---|  
|`attributelist`|<span data-ttu-id="9fa26-108">可选。</span><span class="sxs-lookup"><span data-stu-id="9fa26-108">Optional.</span></span> <span data-ttu-id="9fa26-109">请参阅 [特性列表](attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="9fa26-109">See [Attribute List](attribute-list.md).</span></span>|  
|`accessmodifier`|<span data-ttu-id="9fa26-110">可选。</span><span class="sxs-lookup"><span data-stu-id="9fa26-110">Optional.</span></span> <span data-ttu-id="9fa26-111">可以是以下值之一：</span><span class="sxs-lookup"><span data-stu-id="9fa26-111">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="9fa26-112">-   [公布](../modifiers/public.md)</span><span class="sxs-lookup"><span data-stu-id="9fa26-112">-   [Public](../modifiers/public.md)</span></span><br /><span data-ttu-id="9fa26-113">-   [避免](../modifiers/protected.md)</span><span class="sxs-lookup"><span data-stu-id="9fa26-113">-   [Protected](../modifiers/protected.md)</span></span><br /><span data-ttu-id="9fa26-114">-   [友好](../modifiers/friend.md)</span><span class="sxs-lookup"><span data-stu-id="9fa26-114">-   [Friend](../modifiers/friend.md)</span></span><br /><span data-ttu-id="9fa26-115">-   [专有](../modifiers/private.md)</span><span class="sxs-lookup"><span data-stu-id="9fa26-115">-   [Private](../modifiers/private.md)</span></span><br /><span data-ttu-id="9fa26-116">-   [受保护的朋友](../modifiers/protected-friend.md)</span><span class="sxs-lookup"><span data-stu-id="9fa26-116">-   [Protected Friend](../modifiers/protected-friend.md)</span></span><br /><span data-ttu-id="9fa26-117">- [私有受保护](../modifiers/private-protected.md)</span><span class="sxs-lookup"><span data-stu-id="9fa26-117">- [Private Protected](../modifiers/private-protected.md)</span></span><br/><br/> <span data-ttu-id="9fa26-118">请参阅 [Visual Basic 中的访问级别](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="9fa26-118">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`Shadows`|<span data-ttu-id="9fa26-119">可选。</span><span class="sxs-lookup"><span data-stu-id="9fa26-119">Optional.</span></span> <span data-ttu-id="9fa26-120">请参阅 [阴影](../modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="9fa26-120">See [Shadows](../modifiers/shadows.md).</span></span>|  
|`MustInherit`|<span data-ttu-id="9fa26-121">可选。</span><span class="sxs-lookup"><span data-stu-id="9fa26-121">Optional.</span></span> <span data-ttu-id="9fa26-122">请参阅 [MustInherit](../modifiers/mustinherit.md)。</span><span class="sxs-lookup"><span data-stu-id="9fa26-122">See [MustInherit](../modifiers/mustinherit.md).</span></span>|  
|`NotInheritable`|<span data-ttu-id="9fa26-123">可选。</span><span class="sxs-lookup"><span data-stu-id="9fa26-123">Optional.</span></span> <span data-ttu-id="9fa26-124">请参阅 [NotInheritable](../modifiers/notinheritable.md)。</span><span class="sxs-lookup"><span data-stu-id="9fa26-124">See [NotInheritable](../modifiers/notinheritable.md).</span></span>|  
|`Partial`|<span data-ttu-id="9fa26-125">可选。</span><span class="sxs-lookup"><span data-stu-id="9fa26-125">Optional.</span></span> <span data-ttu-id="9fa26-126">指示类的分部定义。</span><span class="sxs-lookup"><span data-stu-id="9fa26-126">Indicates a partial definition of the class.</span></span> <span data-ttu-id="9fa26-127">请参阅 [部分](../modifiers/partial.md)。</span><span class="sxs-lookup"><span data-stu-id="9fa26-127">See [Partial](../modifiers/partial.md).</span></span>|  
|`name`|<span data-ttu-id="9fa26-128">必需。</span><span class="sxs-lookup"><span data-stu-id="9fa26-128">Required.</span></span> <span data-ttu-id="9fa26-129">此类的名称。</span><span class="sxs-lookup"><span data-stu-id="9fa26-129">Name of this class.</span></span> <span data-ttu-id="9fa26-130">请参阅 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="9fa26-130">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`Of`|<span data-ttu-id="9fa26-131">可选。</span><span class="sxs-lookup"><span data-stu-id="9fa26-131">Optional.</span></span> <span data-ttu-id="9fa26-132">指定这是一个泛型类。</span><span class="sxs-lookup"><span data-stu-id="9fa26-132">Specifies that this is a generic class.</span></span>|  
|`typelist`|<span data-ttu-id="9fa26-133">如果使用 of 关键字，则 [为](of-clause.md) 必需。</span><span class="sxs-lookup"><span data-stu-id="9fa26-133">Required if you use the [Of](of-clause.md) keyword.</span></span> <span data-ttu-id="9fa26-134">此类的类型参数列表。</span><span class="sxs-lookup"><span data-stu-id="9fa26-134">List of type parameters for this class.</span></span> <span data-ttu-id="9fa26-135">请参阅 [类型列表](type-list.md)。</span><span class="sxs-lookup"><span data-stu-id="9fa26-135">See [Type List](type-list.md).</span></span>|  
|`Inherits`|<span data-ttu-id="9fa26-136">可选。</span><span class="sxs-lookup"><span data-stu-id="9fa26-136">Optional.</span></span> <span data-ttu-id="9fa26-137">指示此类继承另一个类的成员。</span><span class="sxs-lookup"><span data-stu-id="9fa26-137">Indicates that this class inherits the members of another class.</span></span> <span data-ttu-id="9fa26-138">请参阅 [Inherits 语句](inherits-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="9fa26-138">See [Inherits Statement](inherits-statement.md).</span></span>|  
|`classname`|<span data-ttu-id="9fa26-139">如果使用语句，则为必需 `Inherits` 。</span><span class="sxs-lookup"><span data-stu-id="9fa26-139">Required if you use the `Inherits` statement.</span></span> <span data-ttu-id="9fa26-140">此类派生自的类的名称。</span><span class="sxs-lookup"><span data-stu-id="9fa26-140">The name of the class from which this class derives.</span></span>|  
|`Implements`|<span data-ttu-id="9fa26-141">可选。</span><span class="sxs-lookup"><span data-stu-id="9fa26-141">Optional.</span></span> <span data-ttu-id="9fa26-142">指示此类实现一个或多个接口的成员。</span><span class="sxs-lookup"><span data-stu-id="9fa26-142">Indicates that this class implements the members of one or more interfaces.</span></span> <span data-ttu-id="9fa26-143">请参阅 [Implements 语句](implements-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="9fa26-143">See [Implements Statement](implements-statement.md).</span></span>|  
|`interfacenames`|<span data-ttu-id="9fa26-144">如果使用语句，则为必需 `Implements` 。</span><span class="sxs-lookup"><span data-stu-id="9fa26-144">Required if you use the `Implements` statement.</span></span> <span data-ttu-id="9fa26-145">此类实现的接口的名称。</span><span class="sxs-lookup"><span data-stu-id="9fa26-145">The names of the interfaces this class implements.</span></span>|  
|`statements`|<span data-ttu-id="9fa26-146">可选。</span><span class="sxs-lookup"><span data-stu-id="9fa26-146">Optional.</span></span> <span data-ttu-id="9fa26-147">定义此类的成员的语句。</span><span class="sxs-lookup"><span data-stu-id="9fa26-147">Statements which define the members of this class.</span></span>|  
|`End Class`|<span data-ttu-id="9fa26-148">必需。</span><span class="sxs-lookup"><span data-stu-id="9fa26-148">Required.</span></span> <span data-ttu-id="9fa26-149">终止 `Class` 定义。</span><span class="sxs-lookup"><span data-stu-id="9fa26-149">Terminates the `Class` definition.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fa26-150">备注</span><span class="sxs-lookup"><span data-stu-id="9fa26-150">Remarks</span></span>  

 <span data-ttu-id="9fa26-151">`Class`语句定义新的数据类型。</span><span class="sxs-lookup"><span data-stu-id="9fa26-151">A `Class` statement defines a new data type.</span></span> <span data-ttu-id="9fa26-152">*类*是面向对象编程的基本构建基块 (OOP) 。</span><span class="sxs-lookup"><span data-stu-id="9fa26-152">A *class* is a fundamental building block of object-oriented programming (OOP).</span></span> <span data-ttu-id="9fa26-153">有关详细信息，请参阅 [对象和类](../../programming-guide/language-features/objects-and-classes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9fa26-153">For more information, see [Objects and Classes](../../programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
 <span data-ttu-id="9fa26-154">只能 `Class` 在命名空间或模块级别使用。</span><span class="sxs-lookup"><span data-stu-id="9fa26-154">You can use `Class` only at namespace or module level.</span></span> <span data-ttu-id="9fa26-155">这意味着类的 *声明上下文* 必须是源文件、命名空间、类、结构、模块或接口，不能是过程或块。</span><span class="sxs-lookup"><span data-stu-id="9fa26-155">This means the *declaration context* for a class must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure or block.</span></span> <span data-ttu-id="9fa26-156">有关详细信息，请参阅[声明上下文和默认访问级别](declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="9fa26-156">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="9fa26-157">类的每个实例都具有独立于所有其他实例的生存期。</span><span class="sxs-lookup"><span data-stu-id="9fa26-157">Each instance of a class has a lifetime independent of all other instances.</span></span> <span data-ttu-id="9fa26-158">此生存期在由 [新运算符](../operators/new-operator.md) 子句或函数（如）创建时开始 <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A> 。</span><span class="sxs-lookup"><span data-stu-id="9fa26-158">This lifetime begins when it is created by a [New Operator](../operators/new-operator.md) clause or by a function such as <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>.</span></span> <span data-ttu-id="9fa26-159">当指向实例的所有变量均设置为 [Nothing](../nothing.md) 或其他类的实例时，它将结束。</span><span class="sxs-lookup"><span data-stu-id="9fa26-159">It ends when all variables pointing to the instance have been set to [Nothing](../nothing.md) or to instances of other classes.</span></span>  
  
 <span data-ttu-id="9fa26-160">类默认为 [Friend](../modifiers/friend.md) 访问。</span><span class="sxs-lookup"><span data-stu-id="9fa26-160">Classes default to [Friend](../modifiers/friend.md) access.</span></span> <span data-ttu-id="9fa26-161">您可以使用访问修饰符调整其访问级别。</span><span class="sxs-lookup"><span data-stu-id="9fa26-161">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="9fa26-162">有关详细信息，请参阅 [Visual Basic 中的访问级别](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="9fa26-162">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="9fa26-163">规则</span><span class="sxs-lookup"><span data-stu-id="9fa26-163">Rules</span></span>  
  
- <span data-ttu-id="9fa26-164">**层.**</span><span class="sxs-lookup"><span data-stu-id="9fa26-164">**Nesting.**</span></span> <span data-ttu-id="9fa26-165">可以在另一个类中定义一个类。</span><span class="sxs-lookup"><span data-stu-id="9fa26-165">You can define one class within another.</span></span> <span data-ttu-id="9fa26-166">外部类称为 *包含类*，内部类称为 " *嵌套类*"。</span><span class="sxs-lookup"><span data-stu-id="9fa26-166">The outer class is called the *containing class*, and the inner class is called a *nested class*.</span></span>  
  
- <span data-ttu-id="9fa26-167">**继承.**</span><span class="sxs-lookup"><span data-stu-id="9fa26-167">**Inheritance.**</span></span> <span data-ttu-id="9fa26-168">如果类使用 [Inherits 语句](inherits-statement.md)，则只能指定一个基类或接口。</span><span class="sxs-lookup"><span data-stu-id="9fa26-168">If the class uses the [Inherits Statement](inherits-statement.md), you can specify only one base class or interface.</span></span> <span data-ttu-id="9fa26-169">类不能从多个元素继承。</span><span class="sxs-lookup"><span data-stu-id="9fa26-169">A class cannot inherit from more than one element.</span></span>  
  
     <span data-ttu-id="9fa26-170">类不能继承自具有限制性更强的访问级别的另一个类。</span><span class="sxs-lookup"><span data-stu-id="9fa26-170">A class cannot inherit from another class with a more restrictive access level.</span></span> <span data-ttu-id="9fa26-171">例如， `Public` 类不能从 `Friend` 类继承。</span><span class="sxs-lookup"><span data-stu-id="9fa26-171">For example, a `Public` class cannot inherit from a `Friend` class.</span></span>  
  
     <span data-ttu-id="9fa26-172">类不能从嵌套在它中的类继承。</span><span class="sxs-lookup"><span data-stu-id="9fa26-172">A class cannot inherit from a class nested within it.</span></span>  
  
- <span data-ttu-id="9fa26-173">**部署.**</span><span class="sxs-lookup"><span data-stu-id="9fa26-173">**Implementation.**</span></span> <span data-ttu-id="9fa26-174">如果类使用 [Implements 语句](implements-statement.md)，则必须实现在中指定的每个接口所定义的每个成员 `interfacenames` 。</span><span class="sxs-lookup"><span data-stu-id="9fa26-174">If the class uses the [Implements Statement](implements-statement.md), you must implement every member defined by every interface you specify in `interfacenames`.</span></span> <span data-ttu-id="9fa26-175">这种情况的一个例外是基类成员的重新实现。</span><span class="sxs-lookup"><span data-stu-id="9fa26-175">An exception to this is reimplementation of a base class member.</span></span> <span data-ttu-id="9fa26-176">有关详细信息，请参阅 [实现](implements-clause.md)中的 "重新实现"。</span><span class="sxs-lookup"><span data-stu-id="9fa26-176">For more information, see "Reimplementation" in [Implements](implements-clause.md).</span></span>  
  
- <span data-ttu-id="9fa26-177">**默认属性。**</span><span class="sxs-lookup"><span data-stu-id="9fa26-177">**Default Property.**</span></span> <span data-ttu-id="9fa26-178">一个类最多只能指定一个属性作为其 *默认属性*。</span><span class="sxs-lookup"><span data-stu-id="9fa26-178">A class can specify at most one property as its *default property*.</span></span> <span data-ttu-id="9fa26-179">有关详细信息，请参阅 [默认值](../modifiers/default.md)。</span><span class="sxs-lookup"><span data-stu-id="9fa26-179">For more information, see [Default](../modifiers/default.md).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="9fa26-180">行为</span><span class="sxs-lookup"><span data-stu-id="9fa26-180">Behavior</span></span>  
  
- <span data-ttu-id="9fa26-181">**访问级别。**</span><span class="sxs-lookup"><span data-stu-id="9fa26-181">**Access Level.**</span></span> <span data-ttu-id="9fa26-182">在类中，可以使用其自己的访问级别声明每个成员。</span><span class="sxs-lookup"><span data-stu-id="9fa26-182">Within a class, you can declare each member with its own access level.</span></span> <span data-ttu-id="9fa26-183">类成员默认为 [公共](../modifiers/public.md) 访问，变量和常量除外，默认为 [私有](../modifiers/private.md) 访问。</span><span class="sxs-lookup"><span data-stu-id="9fa26-183">Class members default to [Public](../modifiers/public.md) access, except variables and constants, which default to [Private](../modifiers/private.md) access.</span></span> <span data-ttu-id="9fa26-184">当某个类的访问权限超过其成员之一时，类访问级别将优先。</span><span class="sxs-lookup"><span data-stu-id="9fa26-184">When a class has more restricted access than one of its members, the class access level takes precedence.</span></span>  
  
- <span data-ttu-id="9fa26-185">**内.**</span><span class="sxs-lookup"><span data-stu-id="9fa26-185">**Scope.**</span></span> <span data-ttu-id="9fa26-186">类在其包含的命名空间、类、结构或模块的范围内。</span><span class="sxs-lookup"><span data-stu-id="9fa26-186">A class is in scope throughout its containing namespace, class, structure, or module.</span></span>  
  
     <span data-ttu-id="9fa26-187">每个类成员的作用域都是整个类。</span><span class="sxs-lookup"><span data-stu-id="9fa26-187">The scope of every class member is the entire class.</span></span>  
  
     <span data-ttu-id="9fa26-188">**生存期.**</span><span class="sxs-lookup"><span data-stu-id="9fa26-188">**Lifetime.**</span></span> <span data-ttu-id="9fa26-189">Visual Basic 不支持静态类。</span><span class="sxs-lookup"><span data-stu-id="9fa26-189">Visual Basic does not support static classes.</span></span> <span data-ttu-id="9fa26-190">与静态类等效的功能由模块提供。</span><span class="sxs-lookup"><span data-stu-id="9fa26-190">The functional equivalent of a static class is provided by a module.</span></span> <span data-ttu-id="9fa26-191">有关详细信息，请参阅 [Module 语句](module-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="9fa26-191">For more information, see [Module Statement](module-statement.md).</span></span>  
  
     <span data-ttu-id="9fa26-192">类成员的生存期取决于其声明的方式和位置。</span><span class="sxs-lookup"><span data-stu-id="9fa26-192">Class members have lifetimes depending on how and where they are declared.</span></span> <span data-ttu-id="9fa26-193">有关详细信息，请参阅 [Visual Basic 中的生存期](../../programming-guide/language-features/declared-elements/lifetime.md)。</span><span class="sxs-lookup"><span data-stu-id="9fa26-193">For more information, see [Lifetime in Visual Basic](../../programming-guide/language-features/declared-elements/lifetime.md).</span></span>  
  
- <span data-ttu-id="9fa26-194">**限定.**</span><span class="sxs-lookup"><span data-stu-id="9fa26-194">**Qualification.**</span></span> <span data-ttu-id="9fa26-195">类之外的代码必须使用该类的名称来限定成员的名称。</span><span class="sxs-lookup"><span data-stu-id="9fa26-195">Code outside a class must qualify a member's name with the name of that class.</span></span>  
  
     <span data-ttu-id="9fa26-196">如果嵌套类中的代码对编程元素进行了非限定引用，则 Visual Basic 首先在嵌套类中搜索元素，然后在其包含类中搜索元素，并将其放入外部的包含元素。</span><span class="sxs-lookup"><span data-stu-id="9fa26-196">If code inside a nested class makes an unqualified reference to a programming element, Visual Basic searches for the element first in the nested class, then in its containing class, and so on out to the outermost containing element.</span></span>  
  
## <a name="classes-and-modules"></a><span data-ttu-id="9fa26-197">类和模块</span><span class="sxs-lookup"><span data-stu-id="9fa26-197">Classes and Modules</span></span>  

 <span data-ttu-id="9fa26-198">这些元素具有许多相似之处，但也存在一些重要的差异。</span><span class="sxs-lookup"><span data-stu-id="9fa26-198">These elements have many similarities, but there are some important differences as well.</span></span>  
  
- <span data-ttu-id="9fa26-199">**术语。**</span><span class="sxs-lookup"><span data-stu-id="9fa26-199">**Terminology.**</span></span> <span data-ttu-id="9fa26-200">Visual Basic 的早期版本可识别两种类型的模块： *类模块* ( cls 文件) 和 *标准模块* ( bas 文件) 。</span><span class="sxs-lookup"><span data-stu-id="9fa26-200">Previous versions of Visual Basic recognize two types of modules: *class modules* (.cls files) and *standard modules* (.bas files).</span></span> <span data-ttu-id="9fa26-201">当前版本分别调用这些 *类* 和 *模块*。</span><span class="sxs-lookup"><span data-stu-id="9fa26-201">The current version calls these *classes* and *modules*, respectively.</span></span>  
  
- <span data-ttu-id="9fa26-202">**共享成员。**</span><span class="sxs-lookup"><span data-stu-id="9fa26-202">**Shared Members.**</span></span> <span data-ttu-id="9fa26-203">您可以控制某个类的成员是共享成员还是实例成员。</span><span class="sxs-lookup"><span data-stu-id="9fa26-203">You can control whether a member of a class is a shared or instance member.</span></span>  
  
- <span data-ttu-id="9fa26-204">**对象方向。**</span><span class="sxs-lookup"><span data-stu-id="9fa26-204">**Object Orientation.**</span></span> <span data-ttu-id="9fa26-205">类是面向对象的，但模块不是。</span><span class="sxs-lookup"><span data-stu-id="9fa26-205">Classes are object-oriented, but modules are not.</span></span> <span data-ttu-id="9fa26-206">你可以创建一个或多个类的实例。</span><span class="sxs-lookup"><span data-stu-id="9fa26-206">You can create one or more instances of a class.</span></span> <span data-ttu-id="9fa26-207">有关详细信息，请参阅 [对象和类](../../programming-guide/language-features/objects-and-classes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9fa26-207">For more information, see [Objects and Classes](../../programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fa26-208">示例</span><span class="sxs-lookup"><span data-stu-id="9fa26-208">Example</span></span>  

 <span data-ttu-id="9fa26-209">下面的示例使用 `Class` 语句定义一个类和多个成员。</span><span class="sxs-lookup"><span data-stu-id="9fa26-209">The following example uses a `Class` statement to define a class and several members.</span></span>  
  
 [!code-vb[VbVbalrStatements#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#62)]  
  
## <a name="see-also"></a><span data-ttu-id="9fa26-210">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9fa26-210">See also</span></span>

- [<span data-ttu-id="9fa26-211">对象和类</span><span class="sxs-lookup"><span data-stu-id="9fa26-211">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="9fa26-212">结构和类</span><span class="sxs-lookup"><span data-stu-id="9fa26-212">Structures and Classes</span></span>](../../programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="9fa26-213">Interface 语句</span><span class="sxs-lookup"><span data-stu-id="9fa26-213">Interface Statement</span></span>](interface-statement.md)
- [<span data-ttu-id="9fa26-214">Module 语句</span><span class="sxs-lookup"><span data-stu-id="9fa26-214">Module Statement</span></span>](module-statement.md)
- [<span data-ttu-id="9fa26-215">Property Statement</span><span class="sxs-lookup"><span data-stu-id="9fa26-215">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="9fa26-216">对象生存期：如何创建和销毁对象</span><span class="sxs-lookup"><span data-stu-id="9fa26-216">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [<span data-ttu-id="9fa26-217">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9fa26-217">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="9fa26-218">如何：使用泛型类</span><span class="sxs-lookup"><span data-stu-id="9fa26-218">How to: Use a Generic Class</span></span>](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
