---
title: 接口
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, interfaces
- interfaces [Visual Basic], Visual Basic
- interfaces
- interfaces [Visual Basic]
ms.assetid: 61b06674-12c9-430b-be68-cc67ecee1f5b
ms.openlocfilehash: 90f8e5d4eb7bb6b367ee5ffd4a4323097c6bde9c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405038"
---
# <a name="interfaces-visual-basic"></a><span data-ttu-id="3fad6-102">接口 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fad6-102">Interfaces (Visual Basic)</span></span>
<span data-ttu-id="3fad6-103">接口\*\* 定义了类可以实现的属性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="3fad6-103">*Interfaces* define the properties, methods, and events that classes can implement.</span></span> <span data-ttu-id="3fad6-104">接口允许将功能定义为一些紧密相关的属性、方法和事件的小组；这样就减少了兼容性问题，因为可以在不损害现有代码的情况下开发接口的增强型实现。</span><span class="sxs-lookup"><span data-stu-id="3fad6-104">Interfaces allow you to define features as small groups of closely related properties, methods, and events; this reduces compatibility problems because you can develop enhanced implementations for your interfaces without jeopardizing existing code.</span></span> <span data-ttu-id="3fad6-105">在任何时候都可以通过开发附加接口和实现来添加新的功能。</span><span class="sxs-lookup"><span data-stu-id="3fad6-105">You can add new features at any time by developing additional interfaces and implementations.</span></span>  
  
 <span data-ttu-id="3fad6-106">以下是为何要使用接口继承而不用类继承的一些其他原因：</span><span class="sxs-lookup"><span data-stu-id="3fad6-106">There are several other reasons why you might want to use interfaces instead of class inheritance:</span></span>  
  
- <span data-ttu-id="3fad6-107">在应用程序要求很多可能不相关的对象类型以提供某种功能的情况下，接口的适用性更强。</span><span class="sxs-lookup"><span data-stu-id="3fad6-107">Interfaces are better suited to situations in which your applications require many possibly unrelated object types to provide certain functionality.</span></span>  
  
- <span data-ttu-id="3fad6-108">接口比基类更灵活，因为可以定义单个实现来实现多个接口。</span><span class="sxs-lookup"><span data-stu-id="3fad6-108">Interfaces are more flexible than base classes because you can define a single implementation that can implement multiple interfaces.</span></span>  
  
- <span data-ttu-id="3fad6-109">在无需从基类继承实现的情况下，接口更好。</span><span class="sxs-lookup"><span data-stu-id="3fad6-109">Interfaces are better in situations in which you do not have to inherit implementation from a base class.</span></span>  
  
- <span data-ttu-id="3fad6-110">在无法使用类继承的情况下接口非常有用。</span><span class="sxs-lookup"><span data-stu-id="3fad6-110">Interfaces are useful when you cannot use class inheritance.</span></span> <span data-ttu-id="3fad6-111">例如，结构无法从类继承，但它们可以实现接口。</span><span class="sxs-lookup"><span data-stu-id="3fad6-111">For example, structures cannot inherit from classes, but they can implement interfaces.</span></span>  
  
## <a name="declaring-interfaces"></a><span data-ttu-id="3fad6-112">声明接口</span><span class="sxs-lookup"><span data-stu-id="3fad6-112">Declaring Interfaces</span></span>  
 <span data-ttu-id="3fad6-113">接口定义包含在 `Interface` 和 `End Interface` 语句内。</span><span class="sxs-lookup"><span data-stu-id="3fad6-113">Interface definitions are enclosed within the `Interface` and `End Interface` statements.</span></span> <span data-ttu-id="3fad6-114">在 `Interface` 语句后面，可以选择添加列出一个或多个继承的接口的 `Inherits` 语句。</span><span class="sxs-lookup"><span data-stu-id="3fad6-114">Following the `Interface` statement, you can add an optional `Inherits` statement that lists one or more inherited interfaces.</span></span> <span data-ttu-id="3fad6-115">在声明中，`Inherits` 语句必须出现在除注释外的所有其他语句之前。</span><span class="sxs-lookup"><span data-stu-id="3fad6-115">The `Inherits` statements must precede all other statements in the declaration except comments.</span></span> <span data-ttu-id="3fad6-116">接口定义中其余的语句应该包括 `Event`、`Sub`、`Function`、`Property`、`Interface`、`Class`、`Structure` 和 `Enum` 语句。</span><span class="sxs-lookup"><span data-stu-id="3fad6-116">The remaining statements in the interface definition should be `Event`, `Sub`, `Function`, `Property`, `Interface`, `Class`, `Structure`, and `Enum` statements.</span></span> <span data-ttu-id="3fad6-117">接口不能包含任何实现代码或与实现代码关联的语句，如 `End Sub` 或 `End Property`。</span><span class="sxs-lookup"><span data-stu-id="3fad6-117">Interfaces cannot contain any implementation code or statements associated with implementation code, such as `End Sub` or `End Property`.</span></span>  
  
 <span data-ttu-id="3fad6-118">在命名空间中，接口语句默认为 `Friend`，但也可以显式声明为 `Public` 或 `Friend`。</span><span class="sxs-lookup"><span data-stu-id="3fad6-118">In a namespace, interface statements are `Friend` by default, but they can also be explicitly declared as `Public` or `Friend`.</span></span> <span data-ttu-id="3fad6-119">在类、模块、接口和结构中定义的接口默认为 `Public`，但也可以显式声明为 `Public`、`Friend`、`Protected` 或 `Private`。</span><span class="sxs-lookup"><span data-stu-id="3fad6-119">Interfaces defined within classes, modules, interfaces, and structures are `Public` by default, but they can also be explicitly declared as `Public`, `Friend`, `Protected`, or `Private`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3fad6-120">`Shadows` 关键字可应用于所有界面成员。</span><span class="sxs-lookup"><span data-stu-id="3fad6-120">The `Shadows` keyword can be applied to all interface members.</span></span> <span data-ttu-id="3fad6-121">`Overloads` 关键字可应用于界面定义中声明的 `Sub`、`Function` 和 `Property` 语句。</span><span class="sxs-lookup"><span data-stu-id="3fad6-121">The `Overloads` keyword can be applied to `Sub`, `Function`, and `Property` statements declared in an interface definition.</span></span> <span data-ttu-id="3fad6-122">此外，`Property` 语句可以具有 `Default`、`ReadOnly` 或 `WriteOnly` 修饰符。</span><span class="sxs-lookup"><span data-stu-id="3fad6-122">In addition, `Property` statements can have the `Default`, `ReadOnly`, or `WriteOnly` modifiers.</span></span> <span data-ttu-id="3fad6-123">不允许使用任何其他修饰符：`Public`、`Private`、`Friend`、`Protected`、`Shared`、`Overrides`、`MustOverride` 或 `Overridable`。</span><span class="sxs-lookup"><span data-stu-id="3fad6-123">None of the other modifiers—`Public`, `Private`, `Friend`, `Protected`, `Shared`, `Overrides`, `MustOverride`, or `Overridable`—are allowed.</span></span> <span data-ttu-id="3fad6-124">有关详细信息，请参阅[声明上下文和默认访问级别](../../../language-reference/statements/declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="3fad6-124">For more information, see [Declaration Contexts and Default Access Levels](../../../language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="3fad6-125">例如，下面的代码定义了一个函数、一个属性和一个事件的接口。</span><span class="sxs-lookup"><span data-stu-id="3fad6-125">For example, the following code defines an interface with one function, one property, and one event.</span></span>  
  
 [!code-vb[VbVbalrOOP#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#17)]  
  
## <a name="implementing-interfaces"></a><span data-ttu-id="3fad6-126">实现接口</span><span class="sxs-lookup"><span data-stu-id="3fad6-126">Implementing Interfaces</span></span>  
 <span data-ttu-id="3fad6-127">`Implements`通过两种方式使用 Visual Basic 保留字。</span><span class="sxs-lookup"><span data-stu-id="3fad6-127">The Visual Basic reserved word `Implements` is used in two ways.</span></span> <span data-ttu-id="3fad6-128">`Implements` 语句表示类或结构实现接口。</span><span class="sxs-lookup"><span data-stu-id="3fad6-128">The `Implements` statement signifies that a class or structure implements an interface.</span></span> <span data-ttu-id="3fad6-129">`Implements` 关键字表示类成员或结构成员实现特定的接口成员。</span><span class="sxs-lookup"><span data-stu-id="3fad6-129">The `Implements` keyword signifies that a class member or structure member implements a specific interface member.</span></span>  
  
### <a name="implements-statement"></a><span data-ttu-id="3fad6-130">Implements 语句</span><span class="sxs-lookup"><span data-stu-id="3fad6-130">Implements Statement</span></span>  
 <span data-ttu-id="3fad6-131">如果一个类或结构实现一个或多个接口，则它必须紧随在 `Class` 或 `Structure` 语句之后包括 `Implements` 语句。</span><span class="sxs-lookup"><span data-stu-id="3fad6-131">If a class or structure implements one or more interfaces, it must include the `Implements` statement immediately after the `Class` or `Structure` statement.</span></span> <span data-ttu-id="3fad6-132">`Implements` 语句需要一个由类实现的接口的逗号分隔列表。</span><span class="sxs-lookup"><span data-stu-id="3fad6-132">The `Implements` statement requires a comma-separated list of interfaces to be implemented by a class.</span></span> <span data-ttu-id="3fad6-133">类或结构必须使用 `Implements` 关键字来实现所有的接口成员。</span><span class="sxs-lookup"><span data-stu-id="3fad6-133">The class or structure must implement all interface members using the `Implements` keyword.</span></span>  
  
### <a name="implements-keyword"></a><span data-ttu-id="3fad6-134">Implements 关键字</span><span class="sxs-lookup"><span data-stu-id="3fad6-134">Implements Keyword</span></span>  
 <span data-ttu-id="3fad6-135">`Implements` 关键字需要一个要实现的接口成员的逗号分隔列表。</span><span class="sxs-lookup"><span data-stu-id="3fad6-135">The `Implements` keyword requires a comma-separated list of interface members to be implemented.</span></span> <span data-ttu-id="3fad6-136">通常只指定单个接口成员，但也可以指定多个成员。</span><span class="sxs-lookup"><span data-stu-id="3fad6-136">Generally, only a single interface member is specified, but you can specify multiple members.</span></span> <span data-ttu-id="3fad6-137">接口成员的规范由接口名称（必须在类中的 implements 语句中指定）、句点和要实现的成员函数、属性或事件的名称组成。</span><span class="sxs-lookup"><span data-stu-id="3fad6-137">The specification of an interface member consists of the interface name, which must be specified in an implements statement within the class; a period; and the name of the member function, property, or event to be implemented.</span></span> <span data-ttu-id="3fad6-138">实现接口成员的成员的名称可以使用任何合法标识符，但并不限于 `InterfaceName_MethodName` Visual Basic 早期版本中使用的约定。</span><span class="sxs-lookup"><span data-stu-id="3fad6-138">The name of a member that implements an interface member can use any legal identifier, and it is not limited to the `InterfaceName_MethodName` convention used in earlier versions of Visual Basic.</span></span>  
  
 <span data-ttu-id="3fad6-139">例如，以下代码显示了如何声明一个名为 `Sub1` 的用于实现接口方法的子例程：</span><span class="sxs-lookup"><span data-stu-id="3fad6-139">For example, the following code shows how to declare a subroutine named `Sub1` that implements a method of an interface:</span></span>  
  
 [!code-vb[VbVbalrOOP#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#69)]  
  
 <span data-ttu-id="3fad6-140">实现成员的参数类型和返回类型必须与接口属性或接口中的成员声明匹配。</span><span class="sxs-lookup"><span data-stu-id="3fad6-140">The parameter types and return types of the implementing member must match the interface property or member declaration in the interface.</span></span> <span data-ttu-id="3fad6-141">实现接口元素的最常用方法是采用一个与接口同名的成员，如上述示例所示。</span><span class="sxs-lookup"><span data-stu-id="3fad6-141">The most common way to implement an element of an interface is with a member that has the same name as the interface, as shown in the previous example.</span></span>  
  
 <span data-ttu-id="3fad6-142">要声明接口方法的实现，可以使用任何在实例方法声明上合法的特性（包括 `Overloads`、`Overrides`、`Overridable`、`Public`、`Private`、`Protected`、`Friend`、`Protected Friend`、`MustOverride`、`Default` 和 `Static`）。</span><span class="sxs-lookup"><span data-stu-id="3fad6-142">To declare the implementation of an interface method, you can use any attributes that are legal on instance method declarations, including `Overloads`, `Overrides`, `Overridable`, `Public`, `Private`, `Protected`, `Friend`, `Protected Friend`, `MustOverride`, `Default`, and `Static`.</span></span> <span data-ttu-id="3fad6-143">`Shared` 特性是不合法的，因为它定义类而不是实例方法。</span><span class="sxs-lookup"><span data-stu-id="3fad6-143">The `Shared` attribute is not legal since it defines a class rather than an instance method.</span></span>  
  
 <span data-ttu-id="3fad6-144">使用 `Implements`，你还可以编写单个方法来实现接口中定义的多个方法，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="3fad6-144">Using `Implements`, you can also write a single method that implements multiple methods defined in an interface, as in the following example:</span></span>  
  
 [!code-vb[VbVbalrOOP#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#70)]  
  
 <span data-ttu-id="3fad6-145">可以使用私有成员来实现接口成员。</span><span class="sxs-lookup"><span data-stu-id="3fad6-145">You can use a private member to implement an interface member.</span></span> <span data-ttu-id="3fad6-146">在私有成员实现一个接口成员时，即使在类的对象变量上不能直接使用该成员，仍然可以通过接口将其变为可用成员。</span><span class="sxs-lookup"><span data-stu-id="3fad6-146">When a private member implements a member of an interface, that member becomes available by way of the interface even though it is not available directly on object variables for the class.</span></span>  
  
### <a name="interface-implementation-examples"></a><span data-ttu-id="3fad6-147">接口实现示例</span><span class="sxs-lookup"><span data-stu-id="3fad6-147">Interface Implementation Examples</span></span>  
 <span data-ttu-id="3fad6-148">实现接口的类必须实现其所有属性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="3fad6-148">Classes that implement an interface must implement all its properties, methods, and events.</span></span>  
  
 <span data-ttu-id="3fad6-149">下面的示例定义了两个接口。</span><span class="sxs-lookup"><span data-stu-id="3fad6-149">The following example defines two interfaces.</span></span> <span data-ttu-id="3fad6-150">第二个接口 `Interface2` 继承 `Interface1` 并定义附加属性和方法。</span><span class="sxs-lookup"><span data-stu-id="3fad6-150">The second interface, `Interface2`, inherits `Interface1` and defines an additional property and method.</span></span>  
  
 [!code-vb[VbVbalrOOP#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#39)]  
  
 <span data-ttu-id="3fad6-151">下一个示例则实现在上一示例中定义的接口 `Interface1`：</span><span class="sxs-lookup"><span data-stu-id="3fad6-151">The next example implements `Interface1`, the interface defined in the previous example:</span></span>  
  
 [!code-vb[VbVbalrOOP#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#40)]  
  
 <span data-ttu-id="3fad6-152">最后一个示例实现 `Interface2`，包括继承自 `Interface1` 的方法：</span><span class="sxs-lookup"><span data-stu-id="3fad6-152">The final example implements `Interface2`, including a method inherited from `Interface1`:</span></span>  
  
 [!code-vb[VbVbalrOOP#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#41)]  
  
 <span data-ttu-id="3fad6-153">可以使用 readwrite 属性实现 readonly 属性（也就是说，无需在实现类中将其声明为 readonly）。</span><span class="sxs-lookup"><span data-stu-id="3fad6-153">You can implement a readonly property with a readwrite property (that is, you do not have to declare it readonly in the implementing class).</span></span>  <span data-ttu-id="3fad6-154">实现接口承诺至少实现接口声明的成员，但你还可以提供更多功能，如允许对属性进行编写。</span><span class="sxs-lookup"><span data-stu-id="3fad6-154">Implementing an interface promises to implement at least the members that the interface declares, but you can offer more functionality, such as allowing your property to be writable.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="3fad6-155">相关主题</span><span class="sxs-lookup"><span data-stu-id="3fad6-155">Related Topics</span></span>  
  
|<span data-ttu-id="3fad6-156">Title</span><span class="sxs-lookup"><span data-stu-id="3fad6-156">Title</span></span>|<span data-ttu-id="3fad6-157">说明</span><span class="sxs-lookup"><span data-stu-id="3fad6-157">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="3fad6-158">演练：创建和实现接口</span><span class="sxs-lookup"><span data-stu-id="3fad6-158">Walkthrough: Creating and Implementing Interfaces</span></span>](walkthrough-creating-and-implementing-interfaces.md)|<span data-ttu-id="3fad6-159">提供引导你定义和实现自己的接口的详细过程。</span><span class="sxs-lookup"><span data-stu-id="3fad6-159">Provides a detailed procedure that takes you through the process of defining and implementing your own interface.</span></span>|  
|[<span data-ttu-id="3fad6-160">泛型接口中的变体</span><span class="sxs-lookup"><span data-stu-id="3fad6-160">Variance in Generic Interfaces</span></span>](../../concepts/covariance-contravariance/variance-in-generic-interfaces.md)|<span data-ttu-id="3fad6-161">讨论泛型接口中的协变和逆变，提供 .NET Framework 中的变体泛型接口列表。</span><span class="sxs-lookup"><span data-stu-id="3fad6-161">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|
