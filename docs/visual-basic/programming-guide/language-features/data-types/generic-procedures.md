---
title: 泛型过程
ms.date: 07/20/2015
helpviewer_keywords:
- generic methods [Visual Basic], type inference
- generics [Visual Basic], type inference
- procedures [Visual Basic], generic
- generic procedures
- type inference, generics
- generic methods [Visual Basic]
- type inference
- generics [Visual Basic], procedures
- generic procedures [Visual Basic], type inference
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
ms.openlocfilehash: 558601f038fccdcb9b94acb7c796e2b49fb6e6f4
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059192"
---
# <a name="generic-procedures-in-visual-basic"></a><span data-ttu-id="db064-102">Generic Procedures in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="db064-102">Generic Procedures in Visual Basic</span></span>

<span data-ttu-id="db064-103">*泛型过程*（也称为*泛型方法*）是定义了至少一个类型参数的过程。</span><span class="sxs-lookup"><span data-stu-id="db064-103">A *generic procedure*, also called a *generic method*, is a procedure defined with at least one type parameter.</span></span> <span data-ttu-id="db064-104">这样，每次调用该过程时，调用代码都可以根据其需求来定制数据类型。</span><span class="sxs-lookup"><span data-stu-id="db064-104">This allows the calling code to tailor the data types to its requirements each time it calls the procedure.</span></span>  
  
 <span data-ttu-id="db064-105">过程不是泛型的，只是在泛型类或泛型结构中进行定义。</span><span class="sxs-lookup"><span data-stu-id="db064-105">A procedure is not generic simply by virtue of being defined inside a generic class or a generic structure.</span></span> <span data-ttu-id="db064-106">若要为泛型，该过程除了需要使用任何常规参数外，还必须使用至少一个类型参数。</span><span class="sxs-lookup"><span data-stu-id="db064-106">To be generic, the procedure must take at least one type parameter, in addition to any normal parameters it might take.</span></span> <span data-ttu-id="db064-107">泛型类或结构可以包含非泛型过程，非泛型类、结构或模块可以包含泛型过程。</span><span class="sxs-lookup"><span data-stu-id="db064-107">A generic class or structure can contain nongeneric procedures, and a nongeneric class, structure, or module can contain generic procedures.</span></span>  
  
 <span data-ttu-id="db064-108">泛型过程可以在其常规参数列表中使用其类型参数（如果有），并在其过程代码中使用它的返回类型。</span><span class="sxs-lookup"><span data-stu-id="db064-108">A generic procedure can use its type parameters in its normal parameter list, in its return type if it has one, and in its procedure code.</span></span>  
  
## <a name="type-inference"></a><span data-ttu-id="db064-109">类型推断</span><span class="sxs-lookup"><span data-stu-id="db064-109">Type Inference</span></span>  

 <span data-ttu-id="db064-110">无需提供任何类型参数即可调用泛型过程。</span><span class="sxs-lookup"><span data-stu-id="db064-110">You can call a generic procedure without supplying any type arguments at all.</span></span> <span data-ttu-id="db064-111">如果以这种方式对其进行调用，则编译器将尝试确定要传递给该过程的类型参数的相应数据类型。</span><span class="sxs-lookup"><span data-stu-id="db064-111">If you call it this way, the compiler attempts to determine the appropriate data types to pass to the procedure's type arguments.</span></span> <span data-ttu-id="db064-112">这称为 " *类型推理*"。</span><span class="sxs-lookup"><span data-stu-id="db064-112">This is called *type inference*.</span></span> <span data-ttu-id="db064-113">下面的代码演示了一个调用，其中编译器会推断它应将类型传递 `String` 到类型参数 `t` 。</span><span class="sxs-lookup"><span data-stu-id="db064-113">The following code shows a call in which the compiler infers that it should pass type `String` to the type parameter `t`.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#15)]  
  
 <span data-ttu-id="db064-114">如果编译器无法从调用的上下文推断类型参数，则会报告错误。</span><span class="sxs-lookup"><span data-stu-id="db064-114">If the compiler cannot infer the type arguments from the context of your call, it reports an error.</span></span> <span data-ttu-id="db064-115">导致这种错误的一个可能原因是数组秩不匹配。</span><span class="sxs-lookup"><span data-stu-id="db064-115">One possible cause of such an error is an array rank mismatch.</span></span> <span data-ttu-id="db064-116">例如，假设将普通参数定义为类型参数的数组。</span><span class="sxs-lookup"><span data-stu-id="db064-116">For example, suppose you define a normal parameter as an array of a type parameter.</span></span> <span data-ttu-id="db064-117">如果调用泛型过程来提供不同级别的数组 (维度) 数量，则不匹配会导致类型推理失败。</span><span class="sxs-lookup"><span data-stu-id="db064-117">If you call the generic procedure supplying an array of a different rank (number of dimensions), the mismatch causes type inference to fail.</span></span> <span data-ttu-id="db064-118">下面的代码演示一个调用，其中，二维数组传递到需要一维数组的过程中。</span><span class="sxs-lookup"><span data-stu-id="db064-118">The following code shows a call in which a two-dimensional array is passed to a procedure that expects a one-dimensional array.</span></span>  
  
```vb  
Public Sub demoSub(Of t)(ByVal arg() As t)
End Sub

Public Sub callDemoSub()
    Dim twoDimensions(,) As Integer
    demoSub(twoDimensions)
End Sub
```
  
 <span data-ttu-id="db064-119">您只能通过省略所有类型参数来调用类型推理。</span><span class="sxs-lookup"><span data-stu-id="db064-119">You can invoke type inference only by omitting all the type arguments.</span></span> <span data-ttu-id="db064-120">如果提供了一个类型参数，则必须提供所有参数。</span><span class="sxs-lookup"><span data-stu-id="db064-120">If you supply one type argument, you must supply them all.</span></span>  
  
 <span data-ttu-id="db064-121">仅泛型过程支持类型推理。</span><span class="sxs-lookup"><span data-stu-id="db064-121">Type inference is supported only for generic procedures.</span></span> <span data-ttu-id="db064-122">不能对泛型类、结构、接口或委托调用类型推理。</span><span class="sxs-lookup"><span data-stu-id="db064-122">You cannot invoke type inference on generic classes, structures, interfaces, or delegates.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db064-123">示例</span><span class="sxs-lookup"><span data-stu-id="db064-123">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="db064-124">描述</span><span class="sxs-lookup"><span data-stu-id="db064-124">Description</span></span>  

 <span data-ttu-id="db064-125">下面的示例定义了一个泛型 `Function` 过程，用于查找数组中的特定元素。</span><span class="sxs-lookup"><span data-stu-id="db064-125">The following example defines a generic `Function` procedure to find a particular element in an array.</span></span> <span data-ttu-id="db064-126">它定义了一个类型参数，并使用它在参数列表中构造两个参数。</span><span class="sxs-lookup"><span data-stu-id="db064-126">It defines one type parameter and uses it to construct the two parameters in the parameter list.</span></span>  
  
### <a name="code"></a><span data-ttu-id="db064-127">代码</span><span class="sxs-lookup"><span data-stu-id="db064-127">Code</span></span>  

 [!code-vb[VbVbalrDataTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#14)]  
  
### <a name="comments"></a><span data-ttu-id="db064-128">注释</span><span class="sxs-lookup"><span data-stu-id="db064-128">Comments</span></span>  

 <span data-ttu-id="db064-129">前面的示例需要能够与 `searchValue` 的每个元素进行比较 `searchArray` 。</span><span class="sxs-lookup"><span data-stu-id="db064-129">The preceding example requires the ability to compare `searchValue` against each element of `searchArray`.</span></span> <span data-ttu-id="db064-130">为了保证这种能力，它约束类型参数 `T` 来实现 <xref:System.IComparable%601> 接口。</span><span class="sxs-lookup"><span data-stu-id="db064-130">To guarantee this ability, it constrains the type parameter `T` to implement the <xref:System.IComparable%601> interface.</span></span> <span data-ttu-id="db064-131">此代码使用 <xref:System.IComparable%601.CompareTo%2A> 方法而不是 `=` 运算符，因为无法保证为提供的类型自变量 `T` 支持 `=` 运算符。</span><span class="sxs-lookup"><span data-stu-id="db064-131">The code uses the <xref:System.IComparable%601.CompareTo%2A> method instead of the `=` operator, because there is no guarantee that a type argument supplied for `T` supports the `=` operator.</span></span>  
  
 <span data-ttu-id="db064-132">可以 `findElement` 通过以下代码测试该过程。</span><span class="sxs-lookup"><span data-stu-id="db064-132">You can test the `findElement` procedure with the following code.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#13)]  
  
 <span data-ttu-id="db064-133">上述调用 `MsgBox` 分别显示 "0"、"1" 和 "-1"。</span><span class="sxs-lookup"><span data-stu-id="db064-133">The preceding calls to `MsgBox` display "0", "1", and "-1" respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db064-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="db064-134">See also</span></span>

- [<span data-ttu-id="db064-135">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="db064-135">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="db064-136">如何：定义可对不同数据类型提供相同功能的类</span><span class="sxs-lookup"><span data-stu-id="db064-136">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](how-to-define-a-class-that-can-provide-identical-functionality.md)
- [<span data-ttu-id="db064-137">如何：使用泛型类</span><span class="sxs-lookup"><span data-stu-id="db064-137">How to: Use a Generic Class</span></span>](how-to-use-a-generic-class.md)
- [<span data-ttu-id="db064-138">过程</span><span class="sxs-lookup"><span data-stu-id="db064-138">Procedures</span></span>](../procedures/index.md)
- [<span data-ttu-id="db064-139">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="db064-139">Procedure Parameters and Arguments</span></span>](../procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="db064-140">Type List</span><span class="sxs-lookup"><span data-stu-id="db064-140">Type List</span></span>](../../../language-reference/statements/type-list.md)
- [<span data-ttu-id="db064-141">参数列表</span><span class="sxs-lookup"><span data-stu-id="db064-141">Parameter List</span></span>](../../../language-reference/statements/parameter-list.md)
