---
title: 使用调试器显示特性增强调试
description: 开始在 .NET 中使用调试器显示属性，使类型开发人员还可以指定该类型在调试器中显示时的外观。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- debugger, display attributes
- DebuggerTypeProxyAttribute attribute
- debugging [.NET Framework], debugger display attributes
- DebuggerDisplayAttribute attribute
- display attributes for debugger
- DebuggerBrowsableAttribute attribute
ms.assetid: 72bb7aa9-459b-42c4-9163-9312fab4c410
ms.openlocfilehash: f266bf7278f472c51dd355df5ba04a123cbd7df0
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415961"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a><span data-ttu-id="e34fe-103">使用调试器显示特性增强调试</span><span class="sxs-lookup"><span data-stu-id="e34fe-103">Enhancing Debugging with the Debugger Display Attributes</span></span>

<span data-ttu-id="e34fe-104">最了解且可指定类型运行时行为的类型开发人员还可以使用调试器显示属性指定类型在调试器中的显示外观。</span><span class="sxs-lookup"><span data-stu-id="e34fe-104">Debugger display attributes allow the developer of the type, who specifies and best understands the runtime behavior of that type, to also specify what that type will look like when it is displayed in a debugger.</span></span> <span data-ttu-id="e34fe-105">此外，即使不了解源代码，用户也可将提供 `Target` 属性的调试器显示属性应用于程序集级别。</span><span class="sxs-lookup"><span data-stu-id="e34fe-105">In addition, debugger display attributes that provide a `Target` property can be applied at the assembly level by users without knowledge of the source code.</span></span> <span data-ttu-id="e34fe-106"><xref:System.Diagnostics.DebuggerDisplayAttribute> 属性控制类型或成员在调试器变量窗口中的显示方式。</span><span class="sxs-lookup"><span data-stu-id="e34fe-106">The <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute controls how a type or member is displayed in the debugger variable windows.</span></span> <span data-ttu-id="e34fe-107"><xref:System.Diagnostics.DebuggerBrowsableAttribute> 属性决定是否在调试器变量窗口中显示字段或属性，若要显示，则决定其显示方式。</span><span class="sxs-lookup"><span data-stu-id="e34fe-107">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute determines if and how a field or property is displayed in the debugger variable windows.</span></span> <span data-ttu-id="e34fe-108"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> 属性指定类型的替代类型或代理，并更改类型在调试器窗口中的显示方式。</span><span class="sxs-lookup"><span data-stu-id="e34fe-108">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute specifies a substitute type, or a proxy, for a type and changes the way the type is displayed in debugger windows.</span></span> <span data-ttu-id="e34fe-109">查看具有代理或替代类型的变量时，代理将代替调试器显示窗口中的原始类型。</span><span class="sxs-lookup"><span data-stu-id="e34fe-109">When you view a variable that has a proxy, or substitute type, the proxy stands in for the original type in the debugger display window.</span></span> <span data-ttu-id="e34fe-110">调试器变量窗口仅显示代理类型的公共成员。</span><span class="sxs-lookup"><span data-stu-id="e34fe-110">The debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="e34fe-111">不会显示私有成员。</span><span class="sxs-lookup"><span data-stu-id="e34fe-111">Private members are not displayed.</span></span>  
  
## <a name="using-the-debuggerdisplayattribute"></a><span data-ttu-id="e34fe-112">使用 DebuggerDisplayAttribute</span><span class="sxs-lookup"><span data-stu-id="e34fe-112">Using the DebuggerDisplayAttribute</span></span>  

<span data-ttu-id="e34fe-113"><xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> 构造函数有一个参数，此参数是一个字符串，将在类型实例的值列中显示。</span><span class="sxs-lookup"><span data-stu-id="e34fe-113">The <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> constructor has a single argument: a string to be displayed in the value column for instances of the type.</span></span> <span data-ttu-id="e34fe-114">此字符串可以包含大括号（{ 和 }）。</span><span class="sxs-lookup"><span data-stu-id="e34fe-114">This string can contain braces ({ and }).</span></span> <span data-ttu-id="e34fe-115">一对大括号之间的文本将作为表达式进行计算。</span><span class="sxs-lookup"><span data-stu-id="e34fe-115">The text within a pair of braces is evaluated as an expression.</span></span> <span data-ttu-id="e34fe-116">例如，选择加号 (+) 以展开 `MyHashtable` 实例的调试器显示时，以下 C# 代码将显示“Count = 4”。</span><span class="sxs-lookup"><span data-stu-id="e34fe-116">For example, the following C# code causes "Count = 4" to be displayed when the plus sign (+) is selected to expand the debugger display for an instance of `MyHashtable`.</span></span>  

```csharp
[DebuggerDisplay("Count = {count}")]
class MyHashtable
{
    public int count = 4;
}
```

<span data-ttu-id="e34fe-117">不会处理应用于表达式中所引用属性的特性。</span><span class="sxs-lookup"><span data-stu-id="e34fe-117">Attributes applied to properties referenced in the expression are not processed.</span></span> <span data-ttu-id="e34fe-118">对于 C# 编译器，允许只能隐式访问当前目标类型实例引用的常规表达式。</span><span class="sxs-lookup"><span data-stu-id="e34fe-118">For the C# compiler, a general expression is allowed that has only implicit access to this reference for the current instance of the target type.</span></span> <span data-ttu-id="e34fe-119">该表达式受限，不能访问别名、局部变量或指针。</span><span class="sxs-lookup"><span data-stu-id="e34fe-119">The expression is limited; there is no access to aliases, locals, or pointers.</span></span> <span data-ttu-id="e34fe-120">在 C# 代码中，可在大括号中使用只能隐式访问当前目标类型实例的 `this` 指针的常规表达式。</span><span class="sxs-lookup"><span data-stu-id="e34fe-120">In C# code, you can use a general expression between the braces that has implicit access to the `this` pointer for the current instance of the target type only.</span></span>

<span data-ttu-id="e34fe-121">例如，如果 C# 对象有重写的 `ToString()`，则调试器将调用该重写并显示重写的结果而不是标准 `{<typeName>}.`。因此，如果有重写的 `ToString()`，用户无需使用 <xref:System.Diagnostics.DebuggerDisplayAttribute>。</span><span class="sxs-lookup"><span data-stu-id="e34fe-121">For example, if a C# object has an overridden `ToString()`, the debugger will call the override and show its result instead of the standard `{<typeName>}.` Thus, if you have overridden `ToString()`, you do not need to use <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span></span> <span data-ttu-id="e34fe-122">在同时使用这两者时，<xref:System.Diagnostics.DebuggerDisplayAttribute> 特性将优先于 `ToString()` 重写。</span><span class="sxs-lookup"><span data-stu-id="e34fe-122">If you use both, the <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute takes precedence over the `ToString()` override.</span></span>

## <a name="using-the-debuggerbrowsableattribute"></a><span data-ttu-id="e34fe-123">使用 DebuggerBrowsableAttribute</span><span class="sxs-lookup"><span data-stu-id="e34fe-123">Using the DebuggerBrowsableAttribute</span></span>
 <span data-ttu-id="e34fe-124">将 <xref:System.Diagnostics.DebuggerBrowsableAttribute> 应用于字段或属性，指定字段或属性在调试器窗口中的显示方式。</span><span class="sxs-lookup"><span data-stu-id="e34fe-124">Apply the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to a field or property to specify how the field or property is to be displayed in the debugger window.</span></span> <span data-ttu-id="e34fe-125">此属性的构造函数采用一个 <xref:System.Diagnostics.DebuggerBrowsableState> 枚举值，指定以下任一状态：</span><span class="sxs-lookup"><span data-stu-id="e34fe-125">The constructor for this attribute takes one of the <xref:System.Diagnostics.DebuggerBrowsableState> enumeration values, which specifies one of the following states:</span></span>

- <span data-ttu-id="e34fe-126"><xref:System.Diagnostics.DebuggerBrowsableState.Never> 表示未在数据窗口中显示成员。</span><span class="sxs-lookup"><span data-stu-id="e34fe-126"><xref:System.Diagnostics.DebuggerBrowsableState.Never> indicates that the member is not displayed in the data window.</span></span>  <span data-ttu-id="e34fe-127">例如，将此值用于字段上的 <xref:System.Diagnostics.DebuggerBrowsableAttribute>，则会从层次结构中删除该字段，单击类型实例的加号 (+) 展开封闭类型时，不会显示该字段。</span><span class="sxs-lookup"><span data-stu-id="e34fe-127">For example, using this value for the <xref:System.Diagnostics.DebuggerBrowsableAttribute> on a field removes the field from the hierarchy; the field is not displayed when you expand the enclosing type by clicking the plus sign (+) for the type instance.</span></span>

- <span data-ttu-id="e34fe-128"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> 表示显示成员，但默认情况下不展开。</span><span class="sxs-lookup"><span data-stu-id="e34fe-128"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> indicates that the member is displayed but not expanded by default.</span></span>  <span data-ttu-id="e34fe-129">这是默认行为。</span><span class="sxs-lookup"><span data-stu-id="e34fe-129">This is the default behavior.</span></span>

- <span data-ttu-id="e34fe-130"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> 表示不显示成员本身，但如果成员是一个数组或集合，则会显示其组成对象。</span><span class="sxs-lookup"><span data-stu-id="e34fe-130"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> indicates that the member itself is not shown, but its constituent objects are displayed if it is an array or collection.</span></span>

> [!NOTE]
> <span data-ttu-id="e34fe-131">在 .NET Framework 2.0 中，Visual Basic 不支持 <xref:System.Diagnostics.DebuggerBrowsableAttribute>。</span><span class="sxs-lookup"><span data-stu-id="e34fe-131">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> is not supported by Visual Basic in the .NET Framework version 2.0.</span></span>

<span data-ttu-id="e34fe-132">以下代码示例显示如何使用 <xref:System.Diagnostics.DebuggerBrowsableAttribute> 防止其后面的属性出现在该类的调试窗口中。</span><span class="sxs-lookup"><span data-stu-id="e34fe-132">The following code example shows the use of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to prevent the property following it from appearing in the debug window for the class.</span></span>

```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]
public static string y = "Test String";
```

## <a name="using-the-debuggertypeproxy"></a><span data-ttu-id="e34fe-133">使用 DebuggerTypeProxy</span><span class="sxs-lookup"><span data-stu-id="e34fe-133">Using the DebuggerTypeProxy</span></span>
 <span data-ttu-id="e34fe-134">如需从根本上大幅更改某个类型的调试视图，但不改变类型本身，请使用 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> 属性。</span><span class="sxs-lookup"><span data-stu-id="e34fe-134">Use the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute when you need to significantly and fundamentally change the debugging view of a type, but not change the type itself.</span></span> <span data-ttu-id="e34fe-135"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> 属性用于为类型指定显示代理，允许开发人员为类型定制视图。</span><span class="sxs-lookup"><span data-stu-id="e34fe-135">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute is used to specify a display proxy for a type, allowing a developer to tailor the view for the type.</span></span>  <span data-ttu-id="e34fe-136">该属性与 <xref:System.Diagnostics.DebuggerDisplayAttribute> 类似，可以在程序集级别使用，在这种情况下，<xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> 属性指定将使用代理的类型。</span><span class="sxs-lookup"><span data-stu-id="e34fe-136">This attribute, like the <xref:System.Diagnostics.DebuggerDisplayAttribute>, can be used at the assembly level, in which case the <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> property specifies the type for which the proxy will be used.</span></span> <span data-ttu-id="e34fe-137">建议使用该属性指定在应用属性的类型内发生的私有嵌套类型。</span><span class="sxs-lookup"><span data-stu-id="e34fe-137">The recommended usage is that this attribute specifies a private nested type that occurs within the type to which the attribute is applied.</span></span>  <span data-ttu-id="e34fe-138">显示类型时，支持类型查看器的表达式计算器将检查此属性。</span><span class="sxs-lookup"><span data-stu-id="e34fe-138">An expression evaluator that supports type viewers checks for this attribute when a type is displayed.</span></span> <span data-ttu-id="e34fe-139">如果找到该属性，表达式计算器会将显示代理类型替换为应用该属性的类型。</span><span class="sxs-lookup"><span data-stu-id="e34fe-139">If the attribute is found, the expression evaluator substitutes the display proxy type for the type the attribute is applied to.</span></span>

 <span data-ttu-id="e34fe-140">显示 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> 时，调试器变量窗口仅显示代理类型的公共成员。</span><span class="sxs-lookup"><span data-stu-id="e34fe-140">When the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> is present, the debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="e34fe-141">不会显示私有成员。</span><span class="sxs-lookup"><span data-stu-id="e34fe-141">Private members are not displayed.</span></span> <span data-ttu-id="e34fe-142">属性增强视图不会改变数据窗口的行为。</span><span class="sxs-lookup"><span data-stu-id="e34fe-142">The behavior of the data window is not changed by attribute-enhanced views.</span></span>

 <span data-ttu-id="e34fe-143">为避免不必要的性能损失，不会处理显示代理的属性，直到对象展开，无论是用户单击数据窗口中类型旁的加号 (+) 展开，还是通过应用 <xref:System.Diagnostics.DebuggerBrowsableAttribute> 属性展开。</span><span class="sxs-lookup"><span data-stu-id="e34fe-143">To avoid unnecessary performance penalties, attributes of the display proxy are not processed until the object is expanded, either through the user clicking the plus sign (+) next to the type in a data window, or through the application of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute.</span></span> <span data-ttu-id="e34fe-144">因此，建议不要对显示类型应用任何属性。</span><span class="sxs-lookup"><span data-stu-id="e34fe-144">Therefore, it is recommended that no attributes be applied to the display type.</span></span> <span data-ttu-id="e34fe-145">可以且应该在显示类型的正文中应用属性。</span><span class="sxs-lookup"><span data-stu-id="e34fe-145">Attributes can and should be applied within the body of the display type.</span></span>

 <span data-ttu-id="e34fe-146">以下代码示例显示了如何使用 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> 指定要用作调试器显示代理的类型。</span><span class="sxs-lookup"><span data-stu-id="e34fe-146">The following code example shows the use of the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> to specify a type to be used as a debugger display proxy.</span></span>

```csharp
[DebuggerTypeProxy(typeof(HashtableDebugView))]
class MyHashtable : Hashtable
{
    private const string TestString =
        "This should not appear in the debug window.";

    internal class HashtableDebugView
    {
        private Hashtable hashtable;
        public const string TestStringProxy =
            "This should appear in the debug window.";

        // The constructor for the type proxy class must have a
        // constructor that takes the target type as a parameter.
        public HashtableDebugView(Hashtable hashtable)
        {
            this.hashtable = hashtable;
        }
    }
}
```

## <a name="example"></a><span data-ttu-id="e34fe-147">示例</span><span class="sxs-lookup"><span data-stu-id="e34fe-147">Example</span></span>

### <a name="description"></a><span data-ttu-id="e34fe-148">说明</span><span class="sxs-lookup"><span data-stu-id="e34fe-148">Description</span></span>

<span data-ttu-id="e34fe-149">可在 Visual Studio 中查看下面的代码示例，以查看应用 <xref:System.Diagnostics.DebuggerDisplayAttribute> 、 <xref:System.Diagnostics.DebuggerBrowsableAttribute> 和特性的结果 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="e34fe-149">The following code example can be viewed in Visual Studio to see the results of applying the <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, and <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attributes.</span></span>

### <a name="code"></a><span data-ttu-id="e34fe-150">代码</span><span class="sxs-lookup"><span data-stu-id="e34fe-150">Code</span></span>

[!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
[!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
[!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="e34fe-151">请参阅</span><span class="sxs-lookup"><span data-stu-id="e34fe-151">See also</span></span>

- <xref:System.Diagnostics.DebuggerDisplayAttribute>
- <xref:System.Diagnostics.DebuggerBrowsableAttribute>
- <xref:System.Diagnostics.DebuggerTypeProxyAttribute>
