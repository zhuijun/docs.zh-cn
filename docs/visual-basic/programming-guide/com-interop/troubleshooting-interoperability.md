---
title: 互操作性疑难解答
ms.date: 07/20/2015
helpviewer_keywords:
- interop, deploying assemblies
- assemblies [Visual Basic]
- interop, installing assemblies that share components
- COM objects, troubleshooting
- interop, sharing components
- troubleshooting interoperability [Visual Basic]
- interoperability, troubleshooting
- COM interop [Visual Basic], troubleshooting
- assemblies [Visual Basic], deploying
- troubleshooting Visual Basic, interoperability
- interop assemblies
- interoperability, sharing components
- shared components, using with assemblies
ms.assetid: b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37
ms.openlocfilehash: 135b121638b92adc5a3b0920aa29d10fd1d62d14
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075988"
---
# <a name="troubleshooting-interoperability-visual-basic"></a><span data-ttu-id="bf32b-102">互操作性疑难解答 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf32b-102">Troubleshooting Interoperability (Visual Basic)</span></span>

<span data-ttu-id="bf32b-103">当你在 COM 和 .NET Framework 的托管代码之间进行互操作时，你可能会遇到以下一个或多个常见问题。</span><span class="sxs-lookup"><span data-stu-id="bf32b-103">When you interoperate between COM and the managed code of the .NET Framework, you may encounter one or more of the following common issues.</span></span>  
  
## <a name="interop-marshaling"></a><a name="vbconinteroperabilitymarshalinganchor1"></a> <span data-ttu-id="bf32b-104">互操作封送</span><span class="sxs-lookup"><span data-stu-id="bf32b-104">Interop Marshaling</span></span>  

 <span data-ttu-id="bf32b-105">有时，可能需要使用不属于 .NET Framework 的数据类型。</span><span class="sxs-lookup"><span data-stu-id="bf32b-105">At times, you may have to use data types that are not part of the .NET Framework.</span></span> <span data-ttu-id="bf32b-106">互操作程序集处理 COM 对象的大部分工作，但您可能需要控制向 COM 公开托管对象时使用的数据类型。</span><span class="sxs-lookup"><span data-stu-id="bf32b-106">Interop assemblies handle most of the work for COM objects, but you may have to control the data types that are used when managed objects are exposed to COM.</span></span> <span data-ttu-id="bf32b-107">例如，类库中的结构必须 `BStr` 在发送到由 Visual Basic 6.0 及更早版本创建的 COM 对象的字符串上指定非托管类型。</span><span class="sxs-lookup"><span data-stu-id="bf32b-107">For example, structures in class libraries must specify the `BStr` unmanaged type on strings sent to COM objects created by Visual Basic 6.0 and earlier versions.</span></span> <span data-ttu-id="bf32b-108">在这种情况下，可以使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性来将托管类型公开为非托管类型。</span><span class="sxs-lookup"><span data-stu-id="bf32b-108">In such cases, you can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to cause managed types to be exposed as unmanaged types.</span></span>  
  
## <a name="exporting-fixed-length-strings-to-unmanaged-code"></a><a name="vbconinteroperabilitymarshalinganchor2"></a> <span data-ttu-id="bf32b-109">将固定长度的字符串导出到非托管代码</span><span class="sxs-lookup"><span data-stu-id="bf32b-109">Exporting Fixed-Length Strings to Unmanaged Code</span></span>  

 <span data-ttu-id="bf32b-110">在 Visual Basic 6.0 及更早版本中，字符串将以字节序列的形式导出到 COM 对象，而不包含 null 终止字符。</span><span class="sxs-lookup"><span data-stu-id="bf32b-110">In Visual Basic 6.0 and earlier versions, strings are exported to COM objects as sequences of bytes without a null termination character.</span></span> <span data-ttu-id="bf32b-111">为了与其他语言兼容，在导出字符串时 Visual Basic .NET 包含终止字符。</span><span class="sxs-lookup"><span data-stu-id="bf32b-111">For compatibility with other languages, Visual Basic .NET includes a termination character when exporting strings.</span></span> <span data-ttu-id="bf32b-112">解决这种不兼容问题的最佳方式是将缺少终止字符的字符串导出为 `Byte` 或数组 `Char` 。</span><span class="sxs-lookup"><span data-stu-id="bf32b-112">The best way to address this incompatibility is to export strings that lack the termination character as arrays of `Byte` or `Char`.</span></span>  
  
## <a name="exporting-inheritance-hierarchies"></a><a name="vbconinteroperabilitymarshalinganchor3"></a> <span data-ttu-id="bf32b-113">导出继承层次结构</span><span class="sxs-lookup"><span data-stu-id="bf32b-113">Exporting Inheritance Hierarchies</span></span>  

 <span data-ttu-id="bf32b-114">公开为 COM 对象时，托管类层次结构将展开。</span><span class="sxs-lookup"><span data-stu-id="bf32b-114">Managed class hierarchies flatten out when exposed as COM objects.</span></span> <span data-ttu-id="bf32b-115">例如，如果您定义一个具有成员的基类，然后继承作为 COM 对象公开的派生类中的基类，则使用 COM 对象中的派生类的客户端将无法使用继承的成员。</span><span class="sxs-lookup"><span data-stu-id="bf32b-115">For example, if you define a base class with a member, and then inherit the base class in a derived class that is exposed as a COM object, clients that use the derived class in the COM object will not be able to use the inherited members.</span></span> <span data-ttu-id="bf32b-116">只能从 COM 对象访问基类成员作为基类的实例，并且仅当基类作为 COM 对象创建时才可以访问。</span><span class="sxs-lookup"><span data-stu-id="bf32b-116">Base class members can be accessed from COM objects only as instances of a base class, and then only if the base class is also created as a COM object.</span></span>  
  
## <a name="overloaded-methods"></a><span data-ttu-id="bf32b-117">重载方法</span><span class="sxs-lookup"><span data-stu-id="bf32b-117">Overloaded Methods</span></span>  

 <span data-ttu-id="bf32b-118">尽管可以使用 Visual Basic 创建重载方法，但 COM 不支持这些方法。</span><span class="sxs-lookup"><span data-stu-id="bf32b-118">Although you can create overloaded methods with Visual Basic, they are not supported by COM.</span></span> <span data-ttu-id="bf32b-119">当包含重载方法的类公开为 COM 对象时，将为重载方法生成新的方法名称。</span><span class="sxs-lookup"><span data-stu-id="bf32b-119">When a class that contains overloaded methods is exposed as a COM object, new method names are generated for the overloaded methods.</span></span>  
  
 <span data-ttu-id="bf32b-120">例如，假设有一个具有两个方法重载的类 `Synch` 。</span><span class="sxs-lookup"><span data-stu-id="bf32b-120">For example, consider a class that has two overloads of the `Synch` method.</span></span> <span data-ttu-id="bf32b-121">当类公开为 COM 对象时，生成的新方法名称可以是 `Synch` 和 `Synch_2` 。</span><span class="sxs-lookup"><span data-stu-id="bf32b-121">When the class is exposed as a COM object, the new generated method names could be `Synch` and `Synch_2`.</span></span>  
  
 <span data-ttu-id="bf32b-122">重命名可能会导致 COM 对象的使用者出现两个问题。</span><span class="sxs-lookup"><span data-stu-id="bf32b-122">The renaming can cause two problems for consumers of the COM object.</span></span>  
  
1. <span data-ttu-id="bf32b-123">客户端可能不需要生成的方法名称。</span><span class="sxs-lookup"><span data-stu-id="bf32b-123">Clients might not expect the generated method names.</span></span>  
  
2. <span data-ttu-id="bf32b-124">当向类或其基类添加新的重载时，公开为 COM 对象的类中生成的方法名可能会更改。</span><span class="sxs-lookup"><span data-stu-id="bf32b-124">The generated method names in the class exposed as a COM object can change when new overloads are added to the class or its base class.</span></span> <span data-ttu-id="bf32b-125">这可能会导致版本控制问题。</span><span class="sxs-lookup"><span data-stu-id="bf32b-125">This can cause versioning problems.</span></span>  
  
 <span data-ttu-id="bf32b-126">若要解决这两个问题，请在开发将作为 COM 对象公开的对象时，为每个方法指定唯一名称，而不是使用重载。</span><span class="sxs-lookup"><span data-stu-id="bf32b-126">To solve both problems, give each method a unique name, instead of using overloading, when you develop objects that will be exposed as COM objects.</span></span>  
  
## <a name="use-of-com-objects-through-interop-assemblies"></a><a name="vbconinteroperabilitymarshalinganchor4"></a> <span data-ttu-id="bf32b-127">通过互操作程序集使用 COM 对象</span><span class="sxs-lookup"><span data-stu-id="bf32b-127">Use of COM Objects Through Interop Assemblies</span></span>  

 <span data-ttu-id="bf32b-128">使用互操作程序集的方式与它们所表示的 COM 对象的托管代码替换几乎相同。</span><span class="sxs-lookup"><span data-stu-id="bf32b-128">You use interop assemblies almost as if they are managed code replacements for the COM objects they represent.</span></span> <span data-ttu-id="bf32b-129">但是，由于它们是包装器而不是实际的 COM 对象，因此使用互操作程序集和标准程序集之间存在一些差异。</span><span class="sxs-lookup"><span data-stu-id="bf32b-129">However, because they are wrappers and not actual COM objects, there are some differences between using interop assemblies and standard assemblies.</span></span> <span data-ttu-id="bf32b-130">这些差异区域包括类的公开以及参数和返回值的数据类型。</span><span class="sxs-lookup"><span data-stu-id="bf32b-130">These areas of difference include the exposure of classes, and data types for parameters and return values.</span></span>  
  
## <a name="classes-exposed-as-both-interfaces-and-classes"></a><a name="vbconinteroperabilitymarshalinganchor5"></a> <span data-ttu-id="bf32b-131">作为接口和类公开的类</span><span class="sxs-lookup"><span data-stu-id="bf32b-131">Classes Exposed as Both Interfaces and Classes</span></span>  

 <span data-ttu-id="bf32b-132">与标准程序集中的类不同，COM 类在互操作程序集中作为接口和表示 COM 类的类公开。</span><span class="sxs-lookup"><span data-stu-id="bf32b-132">Unlike classes in standard assemblies, COM classes are exposed in interop assemblies as both an interface and a class that represents the COM class.</span></span> <span data-ttu-id="bf32b-133">接口的名称与 COM 类的名称相同。</span><span class="sxs-lookup"><span data-stu-id="bf32b-133">The interface's name is identical to that of the COM class.</span></span> <span data-ttu-id="bf32b-134">互操作类的名称与原始 COM 类的名称相同，但附加了 "Class" 一词。</span><span class="sxs-lookup"><span data-stu-id="bf32b-134">The name of the interop class is the same as that of the original COM class, but with the word "Class" appended.</span></span> <span data-ttu-id="bf32b-135">例如，假设有一个项目，其中包含对 COM 对象的互操作程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="bf32b-135">For example, suppose you have a project with a reference to an interop assembly for a COM object.</span></span> <span data-ttu-id="bf32b-136">如果 COM 类命名为 `MyComClass` ，IntelliSense 和对象浏览器将显示一个名为的接口 `MyComClass` 和一个名为的类 `MyComClassClass` 。</span><span class="sxs-lookup"><span data-stu-id="bf32b-136">If the COM class is named `MyComClass`, IntelliSense and the Object Browser show an interface named `MyComClass` and a class named `MyComClassClass`.</span></span>  
  
## <a name="creating-instances-of-a-net-framework-class"></a><a name="vbconinteroperabilitymarshalinganchor6"></a> <span data-ttu-id="bf32b-137">创建 .NET Framework 类的实例</span><span class="sxs-lookup"><span data-stu-id="bf32b-137">Creating Instances of a .NET Framework Class</span></span>  

 <span data-ttu-id="bf32b-138">通常，使用具有类名的语句创建 .NET Framework 类的实例 `New` 。</span><span class="sxs-lookup"><span data-stu-id="bf32b-138">Generally, you create an instance of a .NET Framework class using the `New` statement with a class name.</span></span> <span data-ttu-id="bf32b-139">具有由互操作程序集表示的 COM 类是一种情况，您可以在其中使用 `New` 带有接口的语句。</span><span class="sxs-lookup"><span data-stu-id="bf32b-139">Having a COM class represented by an interop assembly is the one case in which you can use the `New` statement with an interface.</span></span> <span data-ttu-id="bf32b-140">除非您将 COM 类与语句一起使用 `Inherits` ，否则您可以像使用类一样使用接口。</span><span class="sxs-lookup"><span data-stu-id="bf32b-140">Unless you are using the COM class with an `Inherits` statement, you can use the interface just as you would a class.</span></span> <span data-ttu-id="bf32b-141">下面的代码演示如何 `Command` 在项目中创建一个对象，该对象具有对 Microsoft ActiveX 数据对象2.8 库 COM 对象的引用：</span><span class="sxs-lookup"><span data-stu-id="bf32b-141">The following code demonstrates how to create a `Command` object in a project that has a reference to the Microsoft ActiveX Data Objects 2.8 Library COM object:</span></span>  
  
 [!code-vb[VbVbalrInterop#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#20)]  
  
 <span data-ttu-id="bf32b-142">但是，如果使用 COM 类作为派生类的基类，则必须使用表示 COM 类的互操作类，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="bf32b-142">However, if you are using the COM class as the base for a derived class, you must use the interop class that represents the COM class, as in the following code:</span></span>  
  
 [!code-vb[VbVbalrInterop#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#21)]  
  
> [!NOTE]
> <span data-ttu-id="bf32b-143">互操作程序集隐式实现表示 COM 类的接口。</span><span class="sxs-lookup"><span data-stu-id="bf32b-143">Interop assemblies implicitly implement interfaces that represent COM classes.</span></span> <span data-ttu-id="bf32b-144">不应尝试使用 `Implements` 语句来实现这些接口，否则将产生错误。</span><span class="sxs-lookup"><span data-stu-id="bf32b-144">You should not try to use the `Implements` statement to implement these interfaces or an error will result.</span></span>  
  
## <a name="data-types-for-parameters-and-return-values"></a><a name="vbconinteroperabilitymarshalinganchor7"></a> <span data-ttu-id="bf32b-145">参数和返回值的数据类型</span><span class="sxs-lookup"><span data-stu-id="bf32b-145">Data Types for Parameters and Return Values</span></span>  

 <span data-ttu-id="bf32b-146">与标准程序集的成员不同，互操作程序集成员的数据类型可能不同于原始对象声明中使用的类型。</span><span class="sxs-lookup"><span data-stu-id="bf32b-146">Unlike members of standard assemblies, interop assembly members may have data types that differ from those used in the  original object declaration.</span></span> <span data-ttu-id="bf32b-147">尽管互操作程序集将 COM 类型隐式转换为兼容的公共语言运行时类型，但您应注意双方使用的数据类型，以防止运行时错误。</span><span class="sxs-lookup"><span data-stu-id="bf32b-147">Although interop assemblies implicitly convert COM types to compatible common language runtime types, you should pay attention to the data types that are used by both sides to prevent runtime errors.</span></span> <span data-ttu-id="bf32b-148">例如，在 Visual Basic 6.0 及更早版本中创建的 COM 对象中，类型的值 `Integer` 采用 .NET Framework 等效类型 `Short` 。</span><span class="sxs-lookup"><span data-stu-id="bf32b-148">For example, in COM objects created in Visual Basic 6.0 and earlier versions, values of type `Integer` assume the .NET Framework equivalent type, `Short`.</span></span> <span data-ttu-id="bf32b-149">建议在使用之前，使用对象浏览器来检查导入成员的特征。</span><span class="sxs-lookup"><span data-stu-id="bf32b-149">It is recommended that you use the Object Browser to examine the characteristics of imported members before you use them.</span></span>  
  
## <a name="module-level-com-methods"></a><a name="vbconinteroperabilitymarshalinganchor8"></a> <span data-ttu-id="bf32b-150">模块级 COM 方法</span><span class="sxs-lookup"><span data-stu-id="bf32b-150">Module level COM methods</span></span>  

 <span data-ttu-id="bf32b-151">大多数 COM 对象的使用方法是：使用关键字创建 COM 类的实例 `New` ，然后调用该对象的方法。</span><span class="sxs-lookup"><span data-stu-id="bf32b-151">Most COM objects are used by creating an instance of a COM class using the `New` keyword and then calling methods of the object.</span></span> <span data-ttu-id="bf32b-152">此规则的一个例外涉及包含 `AppObj` 或 com 类的 com 对象 `GlobalMultiUse` 。</span><span class="sxs-lookup"><span data-stu-id="bf32b-152">One exception to this rule involves COM objects that contain `AppObj` or `GlobalMultiUse` COM classes.</span></span> <span data-ttu-id="bf32b-153">此类类类似于 Visual Basic .NET 类中的模块级方法。</span><span class="sxs-lookup"><span data-stu-id="bf32b-153">Such classes resemble module level methods in Visual Basic .NET classes.</span></span> <span data-ttu-id="bf32b-154">Visual Basic 6.0 及更早版本在你首次调用其中一个方法时，会隐式创建此类对象的实例。</span><span class="sxs-lookup"><span data-stu-id="bf32b-154">Visual Basic 6.0 and earlier versions implicitly create instances of such objects for you the first time that you call one of their methods.</span></span> <span data-ttu-id="bf32b-155">例如，在 Visual Basic 6.0 中，可以添加对 Microsoft DAO 3.6 对象库的引用，并在 `DBEngine` 不首先创建实例的情况下调用方法：</span><span class="sxs-lookup"><span data-stu-id="bf32b-155">For example, in Visual Basic 6.0 you can add a reference to the Microsoft DAO 3.6 Object Library and call the `DBEngine` method without first creating an instance:</span></span>  
  
```vb  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 <span data-ttu-id="bf32b-156">Visual Basic .NET 要求始终创建 COM 对象的实例，然后才能使用其方法。</span><span class="sxs-lookup"><span data-stu-id="bf32b-156">Visual Basic .NET requires that you always create instances of COM objects before you can use their methods.</span></span> <span data-ttu-id="bf32b-157">若要在 Visual Basic 中使用这些方法，请声明所需类的变量，并使用 new 关键字将对象分配给对象变量。</span><span class="sxs-lookup"><span data-stu-id="bf32b-157">To use these methods in Visual Basic, declare a variable of the desired class and use the new keyword to assign the object to the object variable.</span></span> <span data-ttu-id="bf32b-158">`Shared`若要确保仅创建类的一个实例，可以使用关键字。</span><span class="sxs-lookup"><span data-stu-id="bf32b-158">The `Shared` keyword can be used when you want to make sure that only one instance of the class is created.</span></span>  
  
 [!code-vb[VbVbalrInterop#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#23)]  
  
## <a name="unhandled-errors-in-event-handlers"></a><a name="vbconinteroperabilitymarshalinganchor9"></a> <span data-ttu-id="bf32b-159">事件处理程序中的未处理错误</span><span class="sxs-lookup"><span data-stu-id="bf32b-159">Unhandled Errors in Event Handlers</span></span>  

 <span data-ttu-id="bf32b-160">一个常见的互操作问题涉及事件处理程序中的错误，这些事件处理程序处理 COM 对象引发的事件。</span><span class="sxs-lookup"><span data-stu-id="bf32b-160">One common interop problem involves errors in event handlers that handle events raised by COM objects.</span></span> <span data-ttu-id="bf32b-161">此类错误将被忽略，除非使用或语句具体检查错误 `On Error` `Try...Catch...Finally` 。</span><span class="sxs-lookup"><span data-stu-id="bf32b-161">Such errors are ignored unless you specifically check for errors using `On Error` or `Try...Catch...Finally` statements.</span></span> <span data-ttu-id="bf32b-162">例如，下面的示例来自一个 Visual Basic 的 .NET 项目，该项目具有对 Microsoft ActiveX 数据对象2.8 库 COM 对象的引用。</span><span class="sxs-lookup"><span data-stu-id="bf32b-162">For example, the following example is from a Visual Basic .NET project that has a reference to the Microsoft ActiveX Data Objects 2.8 Library COM object.</span></span>  
  
 [!code-vb[VbVbalrInterop#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#24)]  
  
 <span data-ttu-id="bf32b-163">此示例将按预期方式引发错误。</span><span class="sxs-lookup"><span data-stu-id="bf32b-163">This example raises an error as expected.</span></span> <span data-ttu-id="bf32b-164">但是，如果您尝试不带块的相同示例，则将 `Try...Catch...Finally` 忽略该错误，就像您使用了 `OnError Resume Next` 语句一样。</span><span class="sxs-lookup"><span data-stu-id="bf32b-164">However, if you try the same example without the `Try...Catch...Finally` block, the error is ignored as if you used the `OnError Resume Next` statement.</span></span> <span data-ttu-id="bf32b-165">如果没有错误处理，被零除会失败。</span><span class="sxs-lookup"><span data-stu-id="bf32b-165">Without error handling, the division by zero silently fails.</span></span> <span data-ttu-id="bf32b-166">由于此类错误从不引发未经处理的异常错误，因此在处理 COM 对象的事件的事件处理程序中使用某种形式的异常处理是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="bf32b-166">Because such errors never raise unhandled exception errors, it is important that you use some form of exception handling in event handlers that handle events from COM objects.</span></span>  
  
### <a name="understanding-com-interop-errors"></a><span data-ttu-id="bf32b-167">了解 COM 互操作错误</span><span class="sxs-lookup"><span data-stu-id="bf32b-167">Understanding COM interop errors</span></span>  

 <span data-ttu-id="bf32b-168">如果没有错误处理，互操作调用通常会生成提供少量信息的错误。</span><span class="sxs-lookup"><span data-stu-id="bf32b-168">Without error handling, interop calls often generate errors that provide little information.</span></span> <span data-ttu-id="bf32b-169">尽可能使用结构化错误处理来提供有关发生问题的详细信息。</span><span class="sxs-lookup"><span data-stu-id="bf32b-169">Whenever possible, use structured error handling to provide more information about problems when they occur.</span></span> <span data-ttu-id="bf32b-170">调试应用程序时，这会特别有用。</span><span class="sxs-lookup"><span data-stu-id="bf32b-170">This can be especially helpful when you debug applications.</span></span> <span data-ttu-id="bf32b-171">例如：</span><span class="sxs-lookup"><span data-stu-id="bf32b-171">For example:</span></span>  
  
 [!code-vb[VbVbalrInterop#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#25)]  
  
 <span data-ttu-id="bf32b-172">可以通过检查 exception 对象的内容来查找错误说明、HRESULT 和 COM 错误源等信息。</span><span class="sxs-lookup"><span data-stu-id="bf32b-172">You can find information such as the error description, HRESULT, and the source of COM errors by examining the contents of the exception object.</span></span>  
  
## <a name="activex-control-issues"></a><a name="vbconinteroperabilitymarshalinganchor10"></a> <span data-ttu-id="bf32b-173">ActiveX 控件问题</span><span class="sxs-lookup"><span data-stu-id="bf32b-173">ActiveX Control Issues</span></span>  

 <span data-ttu-id="bf32b-174">大多数与 Visual Basic 6.0 一起使用的 ActiveX 控件都适用于 Visual Basic .NET，而不会出现问题。</span><span class="sxs-lookup"><span data-stu-id="bf32b-174">Most ActiveX controls that work with Visual Basic 6.0 work with Visual Basic .NET without trouble.</span></span> <span data-ttu-id="bf32b-175">主要异常是容器控件，或以可视方式包含其他控件的控件。</span><span class="sxs-lookup"><span data-stu-id="bf32b-175">The main exceptions are container controls, or controls that visually contain other controls.</span></span> <span data-ttu-id="bf32b-176">以下是无法正常使用 Visual Studio 的较旧控件的一些示例：</span><span class="sxs-lookup"><span data-stu-id="bf32b-176">Some examples of older controls that do not work correctly with Visual Studio are as follows:</span></span>  
  
- <span data-ttu-id="bf32b-177">Microsoft Forms 2.0 框架控件</span><span class="sxs-lookup"><span data-stu-id="bf32b-177">Microsoft Forms 2.0 Frame control</span></span>  
  
- <span data-ttu-id="bf32b-178">Up-down 控件，也称为数值调节钮控件</span><span class="sxs-lookup"><span data-stu-id="bf32b-178">Up-Down control, also known as the spin control</span></span>  
  
- <span data-ttu-id="bf32b-179">Sheridan 选项卡控件</span><span class="sxs-lookup"><span data-stu-id="bf32b-179">Sheridan Tab Control</span></span>  
  
 <span data-ttu-id="bf32b-180">对于不支持的 ActiveX 控件问题，只需解决几个问题。</span><span class="sxs-lookup"><span data-stu-id="bf32b-180">There are only a few workarounds for unsupported ActiveX control problems.</span></span> <span data-ttu-id="bf32b-181">如果你拥有原始源代码，则可以将现有控件迁移到 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="bf32b-181">You can migrate existing controls to Visual Studio if you own the original source code.</span></span> <span data-ttu-id="bf32b-182">否则，你可以咨询软件供应商以进行更新。用于替换不受支持的 ActiveX 控件的 NET 兼容版本的控件。</span><span class="sxs-lookup"><span data-stu-id="bf32b-182">Otherwise, you can check with software vendors for updated .NET-compatible versions of controls to replace unsupported ActiveX controls.</span></span>  
  
## <a name="passing-readonly-properties-of-controls-byref"></a><a name="vbconinteroperabilitymarshalinganchor11"></a> <span data-ttu-id="bf32b-183">传递控件的 ReadOnly 属性 ByRef</span><span class="sxs-lookup"><span data-stu-id="bf32b-183">Passing ReadOnly Properties of Controls ByRef</span></span>  

 <span data-ttu-id="bf32b-184">当你将 `ReadOnly` 一些较旧的 ActiveX 控件的属性作为 `ByRef` 参数传递给其他过程时，Visual Basic .net 有时会引发 COM 错误，如 "错误 0x800A017F CTL_E_SETNOTSUPPORTED"。</span><span class="sxs-lookup"><span data-stu-id="bf32b-184">Visual Basic .NET sometimes raises COM errors such as, "Error 0x800A017F CTL_E_SETNOTSUPPORTED", when you pass `ReadOnly` properties of some older ActiveX controls as `ByRef` parameters to other procedures.</span></span> <span data-ttu-id="bf32b-185">来自 Visual Basic 6.0 的类似过程调用不会引发错误，并且这些参数被视为按值传递。</span><span class="sxs-lookup"><span data-stu-id="bf32b-185">Similar procedure calls from Visual Basic 6.0 do not raise an error, and the parameters are treated as if you passed them by value.</span></span> <span data-ttu-id="bf32b-186">Visual Basic .NET 错误消息指示您尝试更改不具有属性过程的属性 `Set` 。</span><span class="sxs-lookup"><span data-stu-id="bf32b-186">The Visual Basic .NET error message indicates that you are trying to change a property that does not have a property `Set` procedure.</span></span>  
  
 <span data-ttu-id="bf32b-187">如果有权访问被调用的过程，则可以通过使用 `ByVal` 关键字声明接受属性的参数来防止此错误 `ReadOnly` 。</span><span class="sxs-lookup"><span data-stu-id="bf32b-187">If you have access to the procedure being called, you can prevent this error by using the `ByVal` keyword to declare parameters that accept `ReadOnly` properties.</span></span> <span data-ttu-id="bf32b-188">例如：</span><span class="sxs-lookup"><span data-stu-id="bf32b-188">For example:</span></span>  
  
 [!code-vb[VbVbalrInterop#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#26)]  
  
 <span data-ttu-id="bf32b-189">如果您无法访问所调用过程的源代码，则可以通过在调用过程的前后添加一组额外的括号来强制通过值传递属性。</span><span class="sxs-lookup"><span data-stu-id="bf32b-189">If you do not have access to the source code for the procedure being called, you can force the property to be passed by value by adding an extra set of brackets around the calling procedure.</span></span> <span data-ttu-id="bf32b-190">例如，在引用 Microsoft ActiveX 数据对象2.8 库 COM 对象的项目中，您可以使用：</span><span class="sxs-lookup"><span data-stu-id="bf32b-190">For example, in a project that has a reference to the Microsoft ActiveX Data Objects 2.8 Library COM object, you can use:</span></span>  
  
 [!code-vb[VbVbalrInterop#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#27)]  
  
## <a name="deploying-assemblies-that-expose-interop"></a><a name="vbconinteroperabilitymarshalinganchor12"></a> <span data-ttu-id="bf32b-191">部署公开互操作的程序集</span><span class="sxs-lookup"><span data-stu-id="bf32b-191">Deploying Assemblies That Expose Interop</span></span>  

 <span data-ttu-id="bf32b-192">部署公开 COM 接口的程序集会带来一些独特的挑战。</span><span class="sxs-lookup"><span data-stu-id="bf32b-192">Deploying assemblies that expose COM interfaces presents some unique challenges.</span></span> <span data-ttu-id="bf32b-193">例如，当单独的应用程序引用同一 COM 程序集时，可能会出现问题。</span><span class="sxs-lookup"><span data-stu-id="bf32b-193">For example, a potential problem occurs when separate applications reference the same COM assembly.</span></span> <span data-ttu-id="bf32b-194">当安装了新版本的程序集，而另一个应用程序仍在使用旧版本的程序集时，这种情况很常见。</span><span class="sxs-lookup"><span data-stu-id="bf32b-194">This situation is common when a new version of an assembly is installed and another application is still using the old version of the assembly.</span></span> <span data-ttu-id="bf32b-195">如果卸载共享 DLL 的程序集，则可能会无意中使其对其他程序集不可用。</span><span class="sxs-lookup"><span data-stu-id="bf32b-195">If you uninstall an assembly that shares a DLL, you can unintentionally make it unavailable to the other assemblies.</span></span>  
  
 <span data-ttu-id="bf32b-196">若要避免此问题，应将共享程序集安装到全局程序集缓存 (GAC) 并使用组件的用于合并模块。</span><span class="sxs-lookup"><span data-stu-id="bf32b-196">To avoid this problem, you should install shared assemblies to the Global Assembly Cache (GAC) and use a MergeModule for the component.</span></span> <span data-ttu-id="bf32b-197">如果无法在 GAC 中安装应用程序，则应将其安装到特定于版本的子目录中的 CommonFilesFolder。</span><span class="sxs-lookup"><span data-stu-id="bf32b-197">If you cannot install the application in the GAC, it should be installed to CommonFilesFolder in a version-specific subdirectory.</span></span>  
  
 <span data-ttu-id="bf32b-198">未共享的程序集应与调用应用程序并排放置在目录中。</span><span class="sxs-lookup"><span data-stu-id="bf32b-198">Assemblies that are not shared should be located side by side in the directory with the calling application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf32b-199">请参阅</span><span class="sxs-lookup"><span data-stu-id="bf32b-199">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="bf32b-200">COM 互操作</span><span class="sxs-lookup"><span data-stu-id="bf32b-200">COM Interop</span></span>](index.md)
- [<span data-ttu-id="bf32b-201">Tlbimp.exe（类型库导入程序）</span><span class="sxs-lookup"><span data-stu-id="bf32b-201">Tlbimp.exe (Type Library Importer)</span></span>](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [<span data-ttu-id="bf32b-202">Tlbexp.exe（类型库导出程序）</span><span class="sxs-lookup"><span data-stu-id="bf32b-202">Tlbexp.exe (Type Library Exporter)</span></span>](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="bf32b-203">演练：使用 COM 对象实现继承</span><span class="sxs-lookup"><span data-stu-id="bf32b-203">Walkthrough: Implementing Inheritance with COM Objects</span></span>](walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="bf32b-204">Inherits Statement</span><span class="sxs-lookup"><span data-stu-id="bf32b-204">Inherits Statement</span></span>](../../language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="bf32b-205">全局程序集缓存</span><span class="sxs-lookup"><span data-stu-id="bf32b-205">Global Assembly Cache</span></span>](../../../framework/app-domains/gac.md)
