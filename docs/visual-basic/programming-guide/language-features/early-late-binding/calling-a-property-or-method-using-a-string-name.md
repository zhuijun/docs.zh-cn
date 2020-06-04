---
title: 使用字符串名调用属性或方法
ms.date: 07/20/2015
helpviewer_keywords:
- passing operators [Visual Basic]
- strings [Visual Basic], passing new operators as
- objects [Visual Basic], setting properties
- setting properties, object properties at run time
- method calls [Visual Basic], strings
- methods [Visual Basic], calling with string names
- calling methods [Visual Basic], string names
- properties [Visual Basic], setting at run time
- CallByName function
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
ms.openlocfilehash: 29072479db36f9f8a81ffd7f3f5b10208ebaa984
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410652"
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a><span data-ttu-id="aec7d-102">使用字符串名调用属性或方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aec7d-102">Calling a Property or Method Using a String Name (Visual Basic)</span></span>
<span data-ttu-id="aec7d-103">在大多数情况下，你可以在设计时发现对象的属性和方法，并编写代码来处理它们。</span><span class="sxs-lookup"><span data-stu-id="aec7d-103">In most cases, you can discover the properties and methods of an object at design time, and write code to handle them.</span></span> <span data-ttu-id="aec7d-104">但是，在某些情况下，您可能事先不知道对象的属性和方法，或者您可能只是想让最终用户能够在运行时指定属性或执行方法。</span><span class="sxs-lookup"><span data-stu-id="aec7d-104">However, in some cases you may not know about an object's properties and methods in advance, or you may just want the flexibility of enabling an end user to specify properties or execute methods at run time.</span></span>  
  
## <a name="callbyname-function"></a><span data-ttu-id="aec7d-105">CallByName 函数</span><span class="sxs-lookup"><span data-stu-id="aec7d-105">CallByName Function</span></span>  
 <span data-ttu-id="aec7d-106">例如，考虑一个客户端应用程序，该应用程序通过将运算符传递到 COM 组件来计算用户输入的表达式。</span><span class="sxs-lookup"><span data-stu-id="aec7d-106">Consider, for example, a client application that evaluates expressions entered by the user by passing an operator to a COM component.</span></span> <span data-ttu-id="aec7d-107">假设您不断地向需要新运算符的组件添加新函数。</span><span class="sxs-lookup"><span data-stu-id="aec7d-107">Suppose you are constantly adding new functions to the component that require new operators.</span></span> <span data-ttu-id="aec7d-108">使用标准对象访问技术时，必须先重新编译并重新发布客户端应用程序，然后才能使用新的运算符。</span><span class="sxs-lookup"><span data-stu-id="aec7d-108">When you use standard object access techniques, you must recompile and redistribute the client application before it could use the new operators.</span></span> <span data-ttu-id="aec7d-109">若要避免这种情况，可以使用 `CallByName` 函数将新运算符作为字符串传递，而无需更改应用程序。</span><span class="sxs-lookup"><span data-stu-id="aec7d-109">To avoid this, you can use the `CallByName` function to pass the new operators as strings, without changing the application.</span></span>  
  
 <span data-ttu-id="aec7d-110">`CallByName`函数使您可以在运行时使用字符串来指定属性或方法。</span><span class="sxs-lookup"><span data-stu-id="aec7d-110">The `CallByName` function lets you use a string to specify a property or method at run time.</span></span> <span data-ttu-id="aec7d-111">函数的签名如下所 `CallByName` 示：</span><span class="sxs-lookup"><span data-stu-id="aec7d-111">The signature for the `CallByName` function looks like this:</span></span>  
  
 <span data-ttu-id="aec7d-112">*Result*  =  结果 `CallByName`（*Object*、 *ProcedureName*、 *CallType*、 *Arguments*（））</span><span class="sxs-lookup"><span data-stu-id="aec7d-112">*Result* = `CallByName`(*Object*, *ProcedureName*, *CallType*, *Arguments*())</span></span>  
  
 <span data-ttu-id="aec7d-113">第一个参数 "*对象*" 采用要对其执行操作的对象的名称。</span><span class="sxs-lookup"><span data-stu-id="aec7d-113">The first argument, *Object*, takes the name of the object you want to act upon.</span></span> <span data-ttu-id="aec7d-114">*ProcedureName*参数采用一个字符串，该字符串包含要调用的方法或属性过程的名称。</span><span class="sxs-lookup"><span data-stu-id="aec7d-114">The *ProcedureName* argument takes a string that contains the name of the method or property procedure to be invoked.</span></span> <span data-ttu-id="aec7d-115">*CallType*参数采用一个常数，该常数表示要调用的过程的类型：方法（ `Microsoft.VisualBasic.CallType.Method` ）、属性读取（ `Microsoft.VisualBasic.CallType.Get` ）或属性集（ `Microsoft.VisualBasic.CallType.Set` ）。</span><span class="sxs-lookup"><span data-stu-id="aec7d-115">The *CallType* argument takes a constant that represents the type of procedure to invoke: a method (`Microsoft.VisualBasic.CallType.Method`), a property read (`Microsoft.VisualBasic.CallType.Get`), or a property set (`Microsoft.VisualBasic.CallType.Set`).</span></span> <span data-ttu-id="aec7d-116">*参数*自变量是可选的，它采用类型为的数组， `Object` 该数组包含过程的所有参数。</span><span class="sxs-lookup"><span data-stu-id="aec7d-116">The *Arguments* argument, which is optional, takes an array of type `Object` that contains any arguments to the procedure.</span></span>  
  
 <span data-ttu-id="aec7d-117">你可以 `CallByName` 在当前解决方案中将与类一起使用，但它通常用于从 .NET Framework 程序集访问 COM 对象或对象。</span><span class="sxs-lookup"><span data-stu-id="aec7d-117">You can use `CallByName` with classes in your current solution, but it is most often used to access COM objects or objects from .NET Framework assemblies.</span></span>  
  
 <span data-ttu-id="aec7d-118">假设你添加对程序集的引用，该程序集包含名为的类 `MathClass` ，该类具有名为的新函数 `SquareRoot` ，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="aec7d-118">Suppose you add a reference to an assembly that contains a class named `MathClass`, which has a new function named `SquareRoot`, as shown in the following code:</span></span>  
  
 [!code-vb[VbVbalrOOP#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#53)]  
  
 <span data-ttu-id="aec7d-119">应用程序可以使用文本框控件控制将调用的方法及其参数。</span><span class="sxs-lookup"><span data-stu-id="aec7d-119">Your application could use text box controls to control which method will be called and its arguments.</span></span> <span data-ttu-id="aec7d-120">例如，如果 `TextBox1` 包含要计算的表达式，并 `TextBox2` 用于输入函数的名称，则可以使用以下代码在 `SquareRoot` 中对表达式调用函数 `TextBox1` ：</span><span class="sxs-lookup"><span data-stu-id="aec7d-120">For example, if `TextBox1` contains the expression to be evaluated, and `TextBox2` is used to enter the name of the function, you can use the following code to invoke the `SquareRoot` function on the expression in `TextBox1`:</span></span>  
  
 [!code-vb[VbVbalrOOP#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#54)]  
  
 <span data-ttu-id="aec7d-121">如果在中输入 "64" `TextBox1` ，在中输入 "SquareRoot"， `TextBox2` 然后调用该 `CallMath` 过程，则计算中的数字的平方根 `TextBox1` 。</span><span class="sxs-lookup"><span data-stu-id="aec7d-121">If you enter "64" in `TextBox1`, "SquareRoot" in `TextBox2`, and then call the `CallMath` procedure, the square root of the number in `TextBox1` is evaluated.</span></span> <span data-ttu-id="aec7d-122">该示例中的代码调用 `SquareRoot` 函数（该函数采用包含要作为必选参数进行计算的表达式的字符串）并返回中的 "8" `TextBox1` （64的平方根）。</span><span class="sxs-lookup"><span data-stu-id="aec7d-122">The code in the example invokes the `SquareRoot` function (which takes a string that contains the expression to be evaluated as a required argument) and returns "8" in `TextBox1` (the square root of 64).</span></span> <span data-ttu-id="aec7d-123">当然，如果用户在中输入了无效的字符串 `TextBox2` ，且该字符串包含属性的名称而不是方法，或者如果该方法有额外的必需参数，则会发生运行时错误。</span><span class="sxs-lookup"><span data-stu-id="aec7d-123">Of course, if the user enters an invalid string in `TextBox2`, if the string contains the name of a property instead of a method, or if the method had an additional required argument, a run-time error occurs.</span></span> <span data-ttu-id="aec7d-124">使用 `CallByName` 来预见这些错误或任何其他错误时，必须添加可靠的错误处理代码。</span><span class="sxs-lookup"><span data-stu-id="aec7d-124">You have to add robust error-handling code when you use `CallByName` to anticipate these or any other errors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aec7d-125">尽管 `CallByName` 函数在某些情况下可能有用，但你必须权衡其对性能影响的有用性，使用 `CallByName` 调用过程比后期绑定调用略慢。</span><span class="sxs-lookup"><span data-stu-id="aec7d-125">While the `CallByName` function may be useful in some cases, you must weigh its usefulness against the performance implications — using `CallByName` to invoke a procedure is slightly slower than a late-bound call.</span></span> <span data-ttu-id="aec7d-126">如果调用的是重复调用的函数（如循环内），则 `CallByName` 可能会对性能产生严重影响。</span><span class="sxs-lookup"><span data-stu-id="aec7d-126">If you are invoking a function that is called repeatedly, such as inside a loop, `CallByName` can have a severe effect on performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aec7d-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aec7d-127">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>
- [<span data-ttu-id="aec7d-128">确定对象类型</span><span class="sxs-lookup"><span data-stu-id="aec7d-128">Determining Object Type</span></span>](determining-object-type.md)
