---
title: 使用 Override 和 New 关键字进行版本控制 - C# 编程指南
description: 了解 C# 中的基类和派生类的版本控制，并了解如何指定某方法是要替代一个继承方法还是要隐藏一个继承方法。
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, versioning
- C# language, override and new
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
ms.openlocfilehash: 13321cdc83637105a2b981902ce984e6a90a25d9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181812"
---
# <a name="versioning-with-the-override-and-new-keywords-c-programming-guide"></a><span data-ttu-id="33626-103">使用 Override 和 New 关键字进行版本控制（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="33626-103">Versioning with the Override and New Keywords (C# Programming Guide)</span></span>

<span data-ttu-id="33626-104">C# 语言经过专门设计，以便不同库中的[基类](../../language-reference/keywords/base.md)与派生类之间的版本控制可以不断向前发展，同时保持后向兼容。</span><span class="sxs-lookup"><span data-stu-id="33626-104">The C# language is designed so that versioning between [base](../../language-reference/keywords/base.md) and derived classes in different libraries can evolve and maintain backward compatibility.</span></span> <span data-ttu-id="33626-105">这具有多方面的意义。例如，这意味着在基[类](../../language-reference/keywords/class.md)中引入与派生类中的某个成员具有相同名称的新成员在 C# 中是完全支持的，不会导致意外行为。</span><span class="sxs-lookup"><span data-stu-id="33626-105">This means, for example, that the introduction of a new member in a base [class](../../language-reference/keywords/class.md) with the same name as a member in a derived class is completely supported by C# and does not lead to unexpected behavior.</span></span> <span data-ttu-id="33626-106">它还意味着类必须显式声明某方法是要替代一个继承方法，还是本身就是一个隐藏具有类似名称的继承方法的新方法。</span><span class="sxs-lookup"><span data-stu-id="33626-106">It also means that a class must explicitly state whether a method is intended to override an inherited method, or whether a method is a new method that hides a similarly named inherited method.</span></span>  
  
 <span data-ttu-id="33626-107">在 C# 中，派生类可以包含与基类方法同名的方法。</span><span class="sxs-lookup"><span data-stu-id="33626-107">In C#, derived classes can contain methods with the same name as base class methods.</span></span>  

- <span data-ttu-id="33626-108">如果派生类中的方法前面没有 [new](../../language-reference/keywords/new-modifier.md) 或 [override](../../language-reference/keywords/override.md) 关键字，则编译器将发出警告，该方法将如同存在 `new` 关键字一样执行操作。</span><span class="sxs-lookup"><span data-stu-id="33626-108">If the method in the derived class is not preceded by [new](../../language-reference/keywords/new-modifier.md) or [override](../../language-reference/keywords/override.md) keywords, the compiler will issue a warning and the method will behave as if the `new` keyword were present.</span></span>  
  
- <span data-ttu-id="33626-109">如果派生类中的方法前面带有 `new` 关键字，则该方法被定义为独立于基类中的方法。</span><span class="sxs-lookup"><span data-stu-id="33626-109">If the method in the derived class is preceded with the `new` keyword, the method is defined as being independent of the method in the base class.</span></span>  
  
- <span data-ttu-id="33626-110">如果派生类中的方法前面带有 `override` 关键字，则派生类的对象将调用该方法，而不是调用基类方法。</span><span class="sxs-lookup"><span data-stu-id="33626-110">If the method in the derived class is preceded with the `override` keyword, objects of the derived class will call that method instead of the base class method.</span></span>  

- <span data-ttu-id="33626-111">若要将 `override` 关键字应用于派生类中的方法，必须以[虚拟](../../language-reference/keywords/virtual.md)形式定义基类方法。</span><span class="sxs-lookup"><span data-stu-id="33626-111">In order to apply the `override` keyword to the method in the derived class, the base class method must be defined [virtual](../../language-reference/keywords/virtual.md).</span></span>
  
- <span data-ttu-id="33626-112">可以从派生类中使用 `base` 关键字调用基类方法。</span><span class="sxs-lookup"><span data-stu-id="33626-112">The base class method can be called from within the derived class using the `base` keyword.</span></span>  
  
- <span data-ttu-id="33626-113">`override`、`virtual` 和 `new` 关键字还可以用于属性、索引器和事件中。</span><span class="sxs-lookup"><span data-stu-id="33626-113">The `override`, `virtual`, and `new` keywords can also be applied to properties, indexers, and events.</span></span>  
  
 <span data-ttu-id="33626-114">默认情况下，C# 方法为非虚方法。</span><span class="sxs-lookup"><span data-stu-id="33626-114">By default, C# methods are not virtual.</span></span> <span data-ttu-id="33626-115">如果某个方法被声明为虚方法，则继承该方法的任何类都可以实现它自己的版本。</span><span class="sxs-lookup"><span data-stu-id="33626-115">If a method is declared as virtual, any class inheriting the method can implement its own version.</span></span> <span data-ttu-id="33626-116">若要使方法成为虚方法，需要在基类的方法声明中使用 `virtual` 修饰符。</span><span class="sxs-lookup"><span data-stu-id="33626-116">To make a method virtual, the `virtual` modifier is used in the method declaration of the base class.</span></span> <span data-ttu-id="33626-117">然后，派生类可以使用 `override` 关键字替代基虚方法，或使用 `new` 关键字隐藏基类中的虚方法。</span><span class="sxs-lookup"><span data-stu-id="33626-117">The derived class can then override the base virtual method by using the `override` keyword or hide the virtual method in the base class by using the `new` keyword.</span></span> <span data-ttu-id="33626-118">如果 `override` 关键字和 `new` 关键字均未指定，编译器将发出警告，并且派生类中的方法将隐藏基类中的方法。</span><span class="sxs-lookup"><span data-stu-id="33626-118">If neither the `override` keyword nor the `new` keyword is specified, the compiler will issue a warning and the method in the derived class will hide the method in the base class.</span></span>  
  
 <span data-ttu-id="33626-119">为了在实践中演示上述情况，暂时假定公司 A 创建了一个名为 `GraphicsClass` 的类，程序将使用此类。</span><span class="sxs-lookup"><span data-stu-id="33626-119">To demonstrate this in practice, assume for a moment that Company A has created a class named `GraphicsClass`, which your program uses.</span></span> <span data-ttu-id="33626-120">`GraphicsClass` 如下所示：</span><span class="sxs-lookup"><span data-stu-id="33626-120">The following is `GraphicsClass`:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#27)]  
  
 <span data-ttu-id="33626-121">公司使用此类，并且你在添加新方法时将其用于派生自己的类：</span><span class="sxs-lookup"><span data-stu-id="33626-121">Your company uses this class, and you use it to derive your own class, adding a new method:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#28)]  
  
 <span data-ttu-id="33626-122">你的应用程序运行正常，未出现问题，直到公司 A 发布了 `GraphicsClass` 的新版本，类似于以下代码：</span><span class="sxs-lookup"><span data-stu-id="33626-122">Your application is used without problems, until Company A releases a new version of `GraphicsClass`, which resembles the following code:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#29)]  
  
 <span data-ttu-id="33626-123">现在，`GraphicsClass` 的新版本中包含一个名为 `DrawRectangle` 的方法。</span><span class="sxs-lookup"><span data-stu-id="33626-123">The new version of `GraphicsClass` now contains a method named `DrawRectangle`.</span></span> <span data-ttu-id="33626-124">开始时，没有出现任何问题。</span><span class="sxs-lookup"><span data-stu-id="33626-124">Initially, nothing occurs.</span></span> <span data-ttu-id="33626-125">新版本仍然与旧版本保持二进制兼容。</span><span class="sxs-lookup"><span data-stu-id="33626-125">The new version is still binary compatible with the old version.</span></span> <span data-ttu-id="33626-126">已经部署的任何软件都将继续正常工作，即使新类已安装到这些计算机系统上。</span><span class="sxs-lookup"><span data-stu-id="33626-126">Any software that you have deployed will continue to work, even if the new class is installed on those computer systems.</span></span> <span data-ttu-id="33626-127">在你的派生类中，对方法 `DrawRectangle` 的任何现有调用将继续引用你的版本。</span><span class="sxs-lookup"><span data-stu-id="33626-127">Any existing calls to the method `DrawRectangle` will continue to reference your version, in your derived class.</span></span>  
  
 <span data-ttu-id="33626-128">但是，一旦你使用 `GraphicsClass` 的新版本重新编译应用程序，就会收到来自编译器的警告 CS0108。</span><span class="sxs-lookup"><span data-stu-id="33626-128">However, as soon as you recompile your application by using the new version of `GraphicsClass`, you will receive a warning from the compiler, CS0108.</span></span> <span data-ttu-id="33626-129">此警告提示，必须考虑你所期望的 `DrawRectangle` 方法在应用程序中的工作方式。</span><span class="sxs-lookup"><span data-stu-id="33626-129">This warning informs you that you have to consider how you want your `DrawRectangle` method to behave in your application.</span></span>  
  
 <span data-ttu-id="33626-130">如果需要自己的方法替代新的基类方法，请使用 `override` 关键字：</span><span class="sxs-lookup"><span data-stu-id="33626-130">If you want your method to override the new base class method, use the `override` keyword:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#30)]  
  
 <span data-ttu-id="33626-131">`override` 关键字可确保派生自 `YourDerivedGraphicsClass` 的任何对象都将使用 `DrawRectangle` 的派生类版本。</span><span class="sxs-lookup"><span data-stu-id="33626-131">The `override` keyword makes sure that any objects derived from `YourDerivedGraphicsClass` will use the derived class version of `DrawRectangle`.</span></span> <span data-ttu-id="33626-132">派生自 `YourDerivedGraphicsClass` 的对象仍可以使用 base 关键字访问 `DrawRectangle` 的基类版本：</span><span class="sxs-lookup"><span data-stu-id="33626-132">Objects derived from `YourDerivedGraphicsClass` can still access the base class version of `DrawRectangle` by using the base keyword:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#44)]  
  
 <span data-ttu-id="33626-133">如果不需要自己的方法替代新的基类方法，则需要注意以下事项。</span><span class="sxs-lookup"><span data-stu-id="33626-133">If you do not want your method to override the new base class method, the following considerations apply.</span></span> <span data-ttu-id="33626-134">为了避免这两个方法之间发生混淆，可以重命名你的方法。</span><span class="sxs-lookup"><span data-stu-id="33626-134">To avoid confusion between the two methods, you can rename your method.</span></span> <span data-ttu-id="33626-135">这可能很耗费时间且容易出错，而且在某些情况下并不可行。</span><span class="sxs-lookup"><span data-stu-id="33626-135">This can be time-consuming and error-prone, and just not practical in some cases.</span></span> <span data-ttu-id="33626-136">但是，如果项目相对较小，则可以使用 Visual Studio 的重构选项来重命名方法。</span><span class="sxs-lookup"><span data-stu-id="33626-136">However, if your project is relatively small, you can use Visual Studio's Refactoring options to rename the method.</span></span> <span data-ttu-id="33626-137">有关详细信息，请参阅[重构类和类型（类设计器）](/visualstudio/ide/class-designer/refactoring-classes-and-types)。</span><span class="sxs-lookup"><span data-stu-id="33626-137">For more information, see [Refactoring Classes and Types (Class Designer)](/visualstudio/ide/class-designer/refactoring-classes-and-types).</span></span>  
  
 <span data-ttu-id="33626-138">或者，也可以通过在派生类定义中使用关键字 `new` 来防止出现该警告：</span><span class="sxs-lookup"><span data-stu-id="33626-138">Alternatively, you can prevent the warning by using the keyword `new` in your derived class definition:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#31)]  
  
 <span data-ttu-id="33626-139">使用 `new` 关键字可告诉编译器你的定义将隐藏基类中包含的定义。</span><span class="sxs-lookup"><span data-stu-id="33626-139">Using the `new` keyword tells the compiler that your definition hides the definition that is contained in the base class.</span></span> <span data-ttu-id="33626-140">这是默认行为。</span><span class="sxs-lookup"><span data-stu-id="33626-140">This is the default behavior.</span></span>  
  
## <a name="override-and-method-selection"></a><span data-ttu-id="33626-141">替代和方法选择</span><span class="sxs-lookup"><span data-stu-id="33626-141">Override and Method Selection</span></span>  

 <span data-ttu-id="33626-142">当在类中对方法进行命名时，如果有多个方法与调用兼容（例如，存在两种同名的方法，并且其参数与传递的参数兼容），则 C# 编译器将选择最佳方法进行调用。</span><span class="sxs-lookup"><span data-stu-id="33626-142">When a method is named on a class, the C# compiler selects the best method to call if more than one method is compatible with the call, such as when there are two methods with the same name, and parameters that are compatible with the parameter passed.</span></span> <span data-ttu-id="33626-143">以下方法将是兼容的：</span><span class="sxs-lookup"><span data-stu-id="33626-143">The following methods would be compatible:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#32)]  
  
 <span data-ttu-id="33626-144">在 `Derived` 的一个实例中调用 `DoWork` 时，C# 编译器将首先尝试使该调用与最初在 `Derived` 上声明的 `DoWork` 版本兼容。</span><span class="sxs-lookup"><span data-stu-id="33626-144">When `DoWork` is called on an instance of `Derived`, the C# compiler will first try to make the call compatible with the versions of `DoWork` declared originally on `Derived`.</span></span> <span data-ttu-id="33626-145">替代方法不被视为是在类上进行声明的，而是在基类上声明的方法的新实现。</span><span class="sxs-lookup"><span data-stu-id="33626-145">Override methods are not considered as declared on a class, they are new implementations of a method declared on a base class.</span></span> <span data-ttu-id="33626-146">仅当 C# 编译器无法将方法调用与 `Derived` 上的原始方法匹配时，才尝试将该调用与具有相同名称和兼容参数的替代方法匹配。</span><span class="sxs-lookup"><span data-stu-id="33626-146">Only if the C# compiler cannot match the method call to an original method on `Derived` will it try to match the call to an overridden method with the same name and compatible parameters.</span></span> <span data-ttu-id="33626-147">例如：</span><span class="sxs-lookup"><span data-stu-id="33626-147">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#33)]  
  
 <span data-ttu-id="33626-148">由于变量 `val` 可以隐式转换为 double 类型，因此 C# 编译器将调用 `DoWork(double)`，而不是 `DoWork(int)`。</span><span class="sxs-lookup"><span data-stu-id="33626-148">Because the variable `val` can be converted to a double implicitly, the C# compiler calls `DoWork(double)` instead of `DoWork(int)`.</span></span> <span data-ttu-id="33626-149">有两种方法可以避免此情况。</span><span class="sxs-lookup"><span data-stu-id="33626-149">There are two ways to avoid this.</span></span> <span data-ttu-id="33626-150">首先，避免将新方法声明为与虚方法相同的名称。</span><span class="sxs-lookup"><span data-stu-id="33626-150">First, avoid declaring new methods with the same name as virtual methods.</span></span> <span data-ttu-id="33626-151">其次，可以通过将 `Derived` 的实例强制转换为 `Base` 来使 C# 编译器搜索基类方法列表，从而使其调用虚方法。</span><span class="sxs-lookup"><span data-stu-id="33626-151">Second, you can instruct the C# compiler to call the virtual method by making it search the base class method list by casting the instance of `Derived` to `Base`.</span></span> <span data-ttu-id="33626-152">由于是虚方法，因此将调用 `Derived` 上的 `DoWork(int)` 的实现。</span><span class="sxs-lookup"><span data-stu-id="33626-152">Because the method is virtual, the implementation of `DoWork(int)` on `Derived` will be called.</span></span> <span data-ttu-id="33626-153">例如：</span><span class="sxs-lookup"><span data-stu-id="33626-153">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#34)]  
  
 <span data-ttu-id="33626-154">有关 `new` 和 `override` 的更多示例，请参阅[了解何时使用 Override 和 New 关键字](./knowing-when-to-use-override-and-new-keywords.md)。</span><span class="sxs-lookup"><span data-stu-id="33626-154">For more examples of `new` and `override`, see [Knowing When to Use Override and New Keywords](./knowing-when-to-use-override-and-new-keywords.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33626-155">请参阅</span><span class="sxs-lookup"><span data-stu-id="33626-155">See also</span></span>

- [<span data-ttu-id="33626-156">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="33626-156">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="33626-157">类和结构</span><span class="sxs-lookup"><span data-stu-id="33626-157">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="33626-158">方法</span><span class="sxs-lookup"><span data-stu-id="33626-158">Methods</span></span>](./methods.md)
- [<span data-ttu-id="33626-159">继承</span><span class="sxs-lookup"><span data-stu-id="33626-159">Inheritance</span></span>](./inheritance.md)
