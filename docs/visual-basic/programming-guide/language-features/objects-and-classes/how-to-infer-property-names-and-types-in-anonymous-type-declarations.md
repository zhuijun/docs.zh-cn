---
title: 如何：推断匿名类型声明中的属性名和类型
ms.date: 07/20/2015
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
ms.openlocfilehash: 9ebbbe9d2e6d36f5ab2bc7f7c916d18c9240a06d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404883"
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a><span data-ttu-id="29ec7-102">如何：推断匿名类型声明中的属性名和类型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29ec7-102">How to: Infer Property Names and Types in Anonymous Type Declarations (Visual Basic)</span></span>

<span data-ttu-id="29ec7-103">匿名类型不提供直接指定属性的数据类型的机制。</span><span class="sxs-lookup"><span data-stu-id="29ec7-103">Anonymous types provide no mechanism for directly specifying the data types of properties.</span></span> <span data-ttu-id="29ec7-104">所有属性的类型都是推断出来的。</span><span class="sxs-lookup"><span data-stu-id="29ec7-104">Types of all properties are inferred.</span></span> <span data-ttu-id="29ec7-105">下面的示例从用于初始化属性的值，直接推断 `Name` 和 `Price` 属性的类型。</span><span class="sxs-lookup"><span data-stu-id="29ec7-105">In the following example, the types of `Name` and `Price` are inferred directly from the values that are used to initialize them.</span></span>

[!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]

<span data-ttu-id="29ec7-106">匿名类型还可以从其他来源推断属性名和类型。</span><span class="sxs-lookup"><span data-stu-id="29ec7-106">Anonymous types can also infer property names and types from other sources.</span></span> <span data-ttu-id="29ec7-107">以下各部分提供了可以进行推断的情况列表，以及不能进行推断的情况的示例。</span><span class="sxs-lookup"><span data-stu-id="29ec7-107">The sections that follow provide a list of the circumstances where inference is possible, and examples of situations where it is not.</span></span>

## <a name="successful-inference"></a><span data-ttu-id="29ec7-108">成功推理</span><span class="sxs-lookup"><span data-stu-id="29ec7-108">Successful Inference</span></span>

#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a><span data-ttu-id="29ec7-109">匿名类型可以从以下来源推断属性名和类型：</span><span class="sxs-lookup"><span data-stu-id="29ec7-109">Anonymous types can infer property names and types from the following sources:</span></span>

- <span data-ttu-id="29ec7-110">从变量名称。</span><span class="sxs-lookup"><span data-stu-id="29ec7-110">From variable names.</span></span> <span data-ttu-id="29ec7-111">匿名类型 `anonProduct` 将具有两个属性： `productName` 和 `productPrice`。</span><span class="sxs-lookup"><span data-stu-id="29ec7-111">Anonymous type `anonProduct` will have two properties, `productName` and `productPrice`.</span></span> <span data-ttu-id="29ec7-112">它们的数据类型将是原始变量的数据类型，分别为 `String` 和 `Double`。</span><span class="sxs-lookup"><span data-stu-id="29ec7-112">Their data types will be those of the original variables, `String` and `Double`, respectively.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#11)]

- <span data-ttu-id="29ec7-113">从其他对象的属性或字段名称。</span><span class="sxs-lookup"><span data-stu-id="29ec7-113">From property or field names of other objects.</span></span> <span data-ttu-id="29ec7-114">例如，考虑包含 `car` 和 `CarClass` 属性的 `Name` 类型的 `ID` 对象。</span><span class="sxs-lookup"><span data-stu-id="29ec7-114">For example, consider a `car` object of a `CarClass` type that includes `Name` and `ID` properties.</span></span> <span data-ttu-id="29ec7-115">若要创建一个匿名类型实例 `car1`，并且其 `Name` 和 `ID` 属性使用 `car` 对象的值进行初始化，则可以编写下面的代码：</span><span class="sxs-lookup"><span data-stu-id="29ec7-115">To create a new anonymous type instance, `car1`, with `Name` and `ID` properties that are initialized with the values from the `car` object, you can write the following:</span></span>

  [!code-vb[VbVbalrAnonymousTypes#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#34)]

  <span data-ttu-id="29ec7-116">以上声明等效于定义匿名类型 `car2`的一行较长的代码。</span><span class="sxs-lookup"><span data-stu-id="29ec7-116">The previous declaration is equivalent to the longer line of code that defines anonymous type `car2`.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#35)]

- <span data-ttu-id="29ec7-117">从 XML 成员名称。</span><span class="sxs-lookup"><span data-stu-id="29ec7-117">From XML member names.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#12)]

  <span data-ttu-id="29ec7-118">为 `anon` 产生的类型将具有一个属性 `Book`，其类型为 <xref:System.Collections.IEnumerable>(Of XElement)。</span><span class="sxs-lookup"><span data-stu-id="29ec7-118">The resulting type for `anon` would have one property, `Book`, of type <xref:System.Collections.IEnumerable>(Of XElement).</span></span>

- <span data-ttu-id="29ec7-119">从没有参数的函数，例如下面示例中的 `SomeFunction` 。</span><span class="sxs-lookup"><span data-stu-id="29ec7-119">From a function that has no parameters, such as `SomeFunction` in the following example.</span></span>

  ```vb
  Dim sc As New SomeClass
  Dim anon1 = New With {Key sc.SomeFunction()}
  ```

  <span data-ttu-id="29ec7-120">下面代码中的变量 `anon2` 是具有一个属性（一个名为 `First`的字符）的匿名类型。</span><span class="sxs-lookup"><span data-stu-id="29ec7-120">The variable `anon2` in the following code is an anonymous type that has one property, a character named `First`.</span></span> <span data-ttu-id="29ec7-121">这段代码将显示函数 <xref:System.Linq.Enumerable.First%2A>返回的字母“E”。</span><span class="sxs-lookup"><span data-stu-id="29ec7-121">This code will display a letter "E," the letter that is returned by function <xref:System.Linq.Enumerable.First%2A>.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#13)]

## <a name="inference-failures"></a><span data-ttu-id="29ec7-122">推理失败</span><span class="sxs-lookup"><span data-stu-id="29ec7-122">Inference Failures</span></span>

#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a><span data-ttu-id="29ec7-123">名称推理在许多情况下将失败，包括：</span><span class="sxs-lookup"><span data-stu-id="29ec7-123">Name inference will fail in many circumstances, including the following:</span></span>

- <span data-ttu-id="29ec7-124">推理派生自对方法、构造函数或需要参数的参数化属性的调用。</span><span class="sxs-lookup"><span data-stu-id="29ec7-124">The inference derives from the invocation of a method, a constructor, or a parameterized property that requires arguments.</span></span> <span data-ttu-id="29ec7-125">如果 `anon1` 具有一个或多个参数，则上面的 `someFunction` 声明将失败。</span><span class="sxs-lookup"><span data-stu-id="29ec7-125">The previous declaration of `anon1` fails if `someFunction` has one or more arguments.</span></span>

  ```vb
  ' Not valid.
  ' Dim anon3 = New With {Key sc.someFunction(someArg)}
  ```

  <span data-ttu-id="29ec7-126">向新属性名赋值可以解决这一问题。</span><span class="sxs-lookup"><span data-stu-id="29ec7-126">Assignment to a new property name solves the problem.</span></span>

  ```vb
  ' Valid.
  Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}
  ```

- <span data-ttu-id="29ec7-127">推理派生自复杂表达式。</span><span class="sxs-lookup"><span data-stu-id="29ec7-127">The inference derives from a complex expression.</span></span>

  ```vb
  Dim aString As String = "Act "
  ' Not valid.
  ' Dim label = New With {Key aString & "IV"}
  ```

  <span data-ttu-id="29ec7-128">将表达式的结果赋给属性名可以消除此错误。</span><span class="sxs-lookup"><span data-stu-id="29ec7-128">The error can be resolved by assigning the result of the expression to a property name.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#14)]

- <span data-ttu-id="29ec7-129">对多个属性的推理会产生两个或更多的同名属性。</span><span class="sxs-lookup"><span data-stu-id="29ec7-129">Inference for multiple properties produces two or more properties that have the same name.</span></span> <span data-ttu-id="29ec7-130">回到前面示例中的声明，在那些声明中，不能将 `product.Name` 和 `car1.Name` 同时列为同一匿名类型的属性。</span><span class="sxs-lookup"><span data-stu-id="29ec7-130">Referring back to declarations in earlier examples, you cannot list both `product.Name` and `car1.Name` as properties of the same anonymous type.</span></span> <span data-ttu-id="29ec7-131">这是因为这些属性的推断标识符都是 `Name`。</span><span class="sxs-lookup"><span data-stu-id="29ec7-131">This is because the inferred identifier for each of these would be `Name`.</span></span>

  ```vb
  ' Not valid.
  ' Dim anon5 = New With {Key product.Name, Key car1.Name}
  ```

  <span data-ttu-id="29ec7-132">通过为不同属性名赋值可以解决此问题。</span><span class="sxs-lookup"><span data-stu-id="29ec7-132">The problem can be solved by assigning the values to distinct property names.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#36)]

  <span data-ttu-id="29ec7-133">请注意，更改大小写（在大写和小写字母之间切换）不能区分两个名称。</span><span class="sxs-lookup"><span data-stu-id="29ec7-133">Note that changes in case (changes between uppercase and lowercase letters) do not make two names distinct.</span></span>

  ```vb
  Dim price = 0
  ' Not valid, because Price and price are the same name.
  ' Dim anon7 = New With {Key product.Price, Key price}
  ```

- <span data-ttu-id="29ec7-134">属性的初始类型和值取决于尚未建立的另一个属性。</span><span class="sxs-lookup"><span data-stu-id="29ec7-134">The initial type and value of one property depends on another property that is not yet established.</span></span> <span data-ttu-id="29ec7-135">例如， `.IDName = .LastName` 在匿名类型声明中无效，除非 `.LastName` 已经初始化。</span><span class="sxs-lookup"><span data-stu-id="29ec7-135">For example, `.IDName = .LastName` is not valid in an anonymous type declaration unless `.LastName` is already initialized.</span></span>

  ```vb
  ' Not valid.
  ' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}
  ```

  <span data-ttu-id="29ec7-136">在此示例中，可以通过逆转声明属性的顺序来解决问题。</span><span class="sxs-lookup"><span data-stu-id="29ec7-136">In this example, you can fix the problem by reversing the order in which the properties are declared.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#15)]

- <span data-ttu-id="29ec7-137">匿名类型的属性名和 <xref:System.Object>的成员的名称相同。</span><span class="sxs-lookup"><span data-stu-id="29ec7-137">A property name of the anonymous type is the same as the name of a member of <xref:System.Object>.</span></span> <span data-ttu-id="29ec7-138">例如，因为 `Equals` 是 <xref:System.Object>的一个方法，所以下面的声明会失败。</span><span class="sxs-lookup"><span data-stu-id="29ec7-138">For example, the following declaration fails because `Equals` is a method of <xref:System.Object>.</span></span>

  ```vb
  ' Not valid.
  ' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _
  '                       "greater than", Key .Less = "less than"}
  ```

  <span data-ttu-id="29ec7-139">可以通过更改属性名来修复该问题：</span><span class="sxs-lookup"><span data-stu-id="29ec7-139">You can fix the problem by changing the property name:</span></span>

  [!code-vb[VbVbalrAnonymousTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#16)]

## <a name="see-also"></a><span data-ttu-id="29ec7-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="29ec7-140">See also</span></span>

- [<span data-ttu-id="29ec7-141">对象初始值设定项：命名和匿名类型</span><span class="sxs-lookup"><span data-stu-id="29ec7-141">Object Initializers: Named and Anonymous Types</span></span>](object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="29ec7-142">局部类型推理</span><span class="sxs-lookup"><span data-stu-id="29ec7-142">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="29ec7-143">匿名类型</span><span class="sxs-lookup"><span data-stu-id="29ec7-143">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="29ec7-144">密钥</span><span class="sxs-lookup"><span data-stu-id="29ec7-144">Key</span></span>](../../../language-reference/modifiers/key.md)
