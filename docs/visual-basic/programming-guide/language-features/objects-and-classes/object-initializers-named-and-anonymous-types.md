---
title: 对象初始值设定项：命名和匿名类型
ms.date: 07/20/2015
f1_keywords:
- vb.ObjectInitializer
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
ms.openlocfilehash: 5561812a53e2fe45c3ad4d12d0e18a8a1e948559
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411761"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a><span data-ttu-id="874f9-102">对象初始值设定项：命名类型和匿名类型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="874f9-102">Object Initializers: Named and Anonymous Types (Visual Basic)</span></span>
<span data-ttu-id="874f9-103">使用对象初始值设定项，您可以通过使用单个表达式来指定复杂对象的属性。</span><span class="sxs-lookup"><span data-stu-id="874f9-103">Object initializers enable you to specify properties for a complex object by using a single expression.</span></span> <span data-ttu-id="874f9-104">它们可用于创建命名类型和匿名类型的实例。</span><span class="sxs-lookup"><span data-stu-id="874f9-104">They can be used to create instances of named types and of anonymous types.</span></span>  
  
## <a name="declarations"></a><span data-ttu-id="874f9-105">声明</span><span class="sxs-lookup"><span data-stu-id="874f9-105">Declarations</span></span>  
 <span data-ttu-id="874f9-106">命名类型和匿名类型的实例的声明可能看起来几乎完全相同，但其效果并不相同。</span><span class="sxs-lookup"><span data-stu-id="874f9-106">Declarations of instances of named and anonymous types can look almost identical, but their effects are not the same.</span></span> <span data-ttu-id="874f9-107">每个类别都具有自己的功能和限制。</span><span class="sxs-lookup"><span data-stu-id="874f9-107">Each category has abilities and restrictions of its own.</span></span> <span data-ttu-id="874f9-108">下面的示例演示如何 `Customer` 使用对象初始值设定项列表来声明和初始化命名类的实例。</span><span class="sxs-lookup"><span data-stu-id="874f9-108">The following example shows a convenient way to declare and initialize an instance of a named class, `Customer`, by using an object initializer list.</span></span> <span data-ttu-id="874f9-109">请注意，类的名称在关键字之后指定 `New` 。</span><span class="sxs-lookup"><span data-stu-id="874f9-109">Notice that the name of the class is specified after the keyword `New`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#1)]  
  
 <span data-ttu-id="874f9-110">匿名类型没有可用的名称。</span><span class="sxs-lookup"><span data-stu-id="874f9-110">An anonymous type has no usable name.</span></span> <span data-ttu-id="874f9-111">因此，匿名类型的实例化不能包含类名。</span><span class="sxs-lookup"><span data-stu-id="874f9-111">Therefore an instantiation of an anonymous type cannot include a class name.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
 <span data-ttu-id="874f9-112">这两个声明的要求和结果不同。</span><span class="sxs-lookup"><span data-stu-id="874f9-112">The requirements and results of the two declarations are not the same.</span></span> <span data-ttu-id="874f9-113">对于 `namedCust` ， `Customer` 具有属性的类 `Name` 必须已经存在，并且声明将创建该类的实例。</span><span class="sxs-lookup"><span data-stu-id="874f9-113">For `namedCust`, a `Customer` class that has a `Name` property must already exist, and the declaration creates an instance of that class.</span></span> <span data-ttu-id="874f9-114">对于 `anonymousCust` ，编译器会定义一个新类，该类具有一个属性和一个名为的字符串， `Name` 并创建该类的一个新实例。</span><span class="sxs-lookup"><span data-stu-id="874f9-114">For `anonymousCust`, the compiler defines a new class that has one property, a string called `Name`, and creates a new instance of that class.</span></span>  
  
## <a name="named-types"></a><span data-ttu-id="874f9-115">命名类型</span><span class="sxs-lookup"><span data-stu-id="874f9-115">Named Types</span></span>  
 <span data-ttu-id="874f9-116">对象初始值设定项提供一种简单的方法来调用类型的构造函数，然后在单个语句中设置部分或全部属性的值。</span><span class="sxs-lookup"><span data-stu-id="874f9-116">Object initializers provide a simple way to call the constructor of a type and then set the values of some or all properties in a single statement.</span></span> <span data-ttu-id="874f9-117">编译器将调用语句的相应构造函数：如果未提供任何参数，则为无参数构造函数; 或者，如果发送一个或多个参数，则为参数化构造函数。</span><span class="sxs-lookup"><span data-stu-id="874f9-117">The compiler invokes the appropriate constructor for the statement: the parameterless constructor if no arguments are presented, or a parameterized constructor if one or more arguments are sent.</span></span> <span data-ttu-id="874f9-118">之后，指定的属性将按照它们在初始值设定项列表中的显示顺序进行初始化。</span><span class="sxs-lookup"><span data-stu-id="874f9-118">After that, the specified properties are initialized in the order in which they are presented in the initializer list.</span></span>  
  
 <span data-ttu-id="874f9-119">初始值设定项列表中的每个初始化都包含将初始值分配给类的成员的。</span><span class="sxs-lookup"><span data-stu-id="874f9-119">Each initialization in the initializer list consists of the assignment of an initial value to a member of the class.</span></span> <span data-ttu-id="874f9-120">成员的名称和数据类型是在定义类时确定的。</span><span class="sxs-lookup"><span data-stu-id="874f9-120">The names and data types of the members are determined when the class is defined.</span></span> <span data-ttu-id="874f9-121">在下面的示例中， `Customer` 类必须存在，并且必须具有名为 `Name` 和 `City` 的成员，这些成员可以接受字符串值。</span><span class="sxs-lookup"><span data-stu-id="874f9-121">In the following examples, the `Customer` class must exist, and must have members named `Name` and `City` that can accept string values.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#3)]  
  
 <span data-ttu-id="874f9-122">或者，可以使用以下代码获取相同的结果：</span><span class="sxs-lookup"><span data-stu-id="874f9-122">Alternatively, you can obtain the same result by using the following code:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#4)]  
  
 <span data-ttu-id="874f9-123">其中每个声明都等效于下面的示例，该示例 `Customer` 使用无参数构造函数创建对象，然后 `Name` 使用语句指定和属性的初始值 `City` `With` 。</span><span class="sxs-lookup"><span data-stu-id="874f9-123">Each of these declarations is equivalent to the following example, which creates a `Customer` object by using the parameterless constructor, and then specifies initial values for the `Name` and `City` properties by using a `With` statement.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#5)]  
  
 <span data-ttu-id="874f9-124">如果 `Customer` 类包含一个参数化构造函数，该构造函数使你能够在的值中发送 `Name` ，则你还可以 `Customer` 通过以下方式声明和初始化对象：</span><span class="sxs-lookup"><span data-stu-id="874f9-124">If the `Customer` class contains a parameterized constructor that enables you to send in a value for `Name`, for example, you can also declare and initialize a `Customer` object in the following ways:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#6)]  
  
 <span data-ttu-id="874f9-125">您不必初始化所有属性，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="874f9-125">You do not have to initialize all properties, as the following code shows.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#7)]  
  
 <span data-ttu-id="874f9-126">但是，初始化列表不能为空。</span><span class="sxs-lookup"><span data-stu-id="874f9-126">However, the initialization list cannot be empty.</span></span> <span data-ttu-id="874f9-127">未初始化属性保留其默认值。</span><span class="sxs-lookup"><span data-stu-id="874f9-127">Uninitialized properties retain their default values.</span></span>  
  
### <a name="type-inference-with-named-types"></a><span data-ttu-id="874f9-128">具有命名类型的类型推理</span><span class="sxs-lookup"><span data-stu-id="874f9-128">Type Inference with Named Types</span></span>  
 <span data-ttu-id="874f9-129">您可以 `cust1` 通过组合对象初始值设定项和局部类型推理，缩短的声明的代码。</span><span class="sxs-lookup"><span data-stu-id="874f9-129">You can shorten the code for the declaration of `cust1` by combining object initializers and local type inference.</span></span> <span data-ttu-id="874f9-130">这使您可以省略 `As` 变量声明中的子句。</span><span class="sxs-lookup"><span data-stu-id="874f9-130">This enables you to omit the `As` clause in the variable declaration.</span></span> <span data-ttu-id="874f9-131">变量的数据类型是从由赋值创建的对象的类型推断出来的。</span><span class="sxs-lookup"><span data-stu-id="874f9-131">The data type of the variable is inferred from the type of the object that is created by the assignment.</span></span> <span data-ttu-id="874f9-132">在下面的示例中，的类型 `cust6` 为 `Customer` 。</span><span class="sxs-lookup"><span data-stu-id="874f9-132">In the following example, the type of `cust6` is `Customer`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#8)]  
  
### <a name="remarks-about-named-types"></a><span data-ttu-id="874f9-133">有关命名类型的备注</span><span class="sxs-lookup"><span data-stu-id="874f9-133">Remarks About Named Types</span></span>  
  
- <span data-ttu-id="874f9-134">类成员不能在对象初始值设定项列表中多次初始化。</span><span class="sxs-lookup"><span data-stu-id="874f9-134">A class member cannot be initialized more than one time in the object initializer list.</span></span> <span data-ttu-id="874f9-135">的声明 `cust7` 会导致错误。</span><span class="sxs-lookup"><span data-stu-id="874f9-135">The declaration of `cust7` causes an error.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#9)]  
  
- <span data-ttu-id="874f9-136">成员可用于初始化自身或另一个字段。</span><span class="sxs-lookup"><span data-stu-id="874f9-136">A member can be used to initialize itself or another field.</span></span> <span data-ttu-id="874f9-137">如果在初始化之前访问成员，则 `cust8` 将使用默认值，如在的以下声明中一样。</span><span class="sxs-lookup"><span data-stu-id="874f9-137">If a member is accessed before it has been initialized, as in the following declaration for `cust8`, the default value will be used.</span></span> <span data-ttu-id="874f9-138">请记住，当处理使用对象初始值设定项的声明时，首先要执行的操作是调用适当的构造函数。</span><span class="sxs-lookup"><span data-stu-id="874f9-138">Remember that when a declaration that uses an object initializer is processed, the first thing that happens is that the appropriate constructor is invoked.</span></span> <span data-ttu-id="874f9-139">然后，初始化初始值设定项列表中的各个字段。</span><span class="sxs-lookup"><span data-stu-id="874f9-139">After that, the individual fields in the initializer list are initialized.</span></span> <span data-ttu-id="874f9-140">在下面的示例中，为分配了的默认值 `Name` `cust8` ，并在中分配了一个初始化值 `cust9` 。</span><span class="sxs-lookup"><span data-stu-id="874f9-140">In the following examples, the default value for `Name` is assigned for `cust8`, and an initialized value is assigned in `cust9`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#10)]  
  
     <span data-ttu-id="874f9-141">下面的示例使用和中的参数化构造函数 `cust3` `cust4` 来声明和初始化 `cust10` 和 `cust11` 。</span><span class="sxs-lookup"><span data-stu-id="874f9-141">The following example uses the parameterized constructor from `cust3` and `cust4` to declare and initialize `cust10` and `cust11`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#11)]  
  
- <span data-ttu-id="874f9-142">对象初始值设定项可以嵌套。</span><span class="sxs-lookup"><span data-stu-id="874f9-142">Object initializers can be nested.</span></span> <span data-ttu-id="874f9-143">在下面的示例中， `AddressClass` 是一个具有两个属性（ `City` 和）的类， `State` 并且 `Customer` 类具有一个作为 `Address` 实例的属性 `AddressClass` 。</span><span class="sxs-lookup"><span data-stu-id="874f9-143">In the following example, `AddressClass` is a class that has two properties, `City` and `State`, and the `Customer` class has an `Address` property that is an instance of `AddressClass`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#12)]  
  
- <span data-ttu-id="874f9-144">初始化列表不能为空。</span><span class="sxs-lookup"><span data-stu-id="874f9-144">The initialization list cannot be empty.</span></span>  
  
- <span data-ttu-id="874f9-145">正在初始化的实例不能是 Object 类型。</span><span class="sxs-lookup"><span data-stu-id="874f9-145">The instance being initialized cannot be of type Object.</span></span>  
  
- <span data-ttu-id="874f9-146">要初始化的类成员不能为共享成员、只读成员、常量或方法调用。</span><span class="sxs-lookup"><span data-stu-id="874f9-146">Class members being initialized cannot be shared members, read-only members, constants, or method calls.</span></span>  
  
- <span data-ttu-id="874f9-147">无法对初始化的类成员进行索引或限定。</span><span class="sxs-lookup"><span data-stu-id="874f9-147">Class members being initialized cannot be indexed or qualified.</span></span> <span data-ttu-id="874f9-148">下面的示例引发编译器错误：</span><span class="sxs-lookup"><span data-stu-id="874f9-148">The following examples raise compiler errors:</span></span>  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a><span data-ttu-id="874f9-149">匿名类型</span><span class="sxs-lookup"><span data-stu-id="874f9-149">Anonymous Types</span></span>  
 <span data-ttu-id="874f9-150">匿名类型使用对象初始值设定项来创建未显式定义和命名的新类型的实例。</span><span class="sxs-lookup"><span data-stu-id="874f9-150">Anonymous types use object initializers to create instances of new types that you do not explicitly define and name.</span></span> <span data-ttu-id="874f9-151">相反，编译器将根据您在对象初始值设定项列表中指定的属性生成类型。</span><span class="sxs-lookup"><span data-stu-id="874f9-151">Instead, the compiler generates a type according to the properties you designate in the object initializer list.</span></span> <span data-ttu-id="874f9-152">由于未指定类型的名称，因此称为*匿名类型*。</span><span class="sxs-lookup"><span data-stu-id="874f9-152">Because the name of the type is not specified, it is referred to as an *anonymous type*.</span></span> <span data-ttu-id="874f9-153">例如，将以下声明与的早期声明进行比较 `cust6` 。</span><span class="sxs-lookup"><span data-stu-id="874f9-153">For example, compare the following declaration to the earlier one for `cust6`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#13)]  
  
 <span data-ttu-id="874f9-154">唯一的不同之处在于，不在数据类型后指定名称 `New` 。</span><span class="sxs-lookup"><span data-stu-id="874f9-154">The only difference syntactically is that no name is specified after `New` for the data type.</span></span> <span data-ttu-id="874f9-155">但发生了什么变化。</span><span class="sxs-lookup"><span data-stu-id="874f9-155">However, what happens is quite different.</span></span> <span data-ttu-id="874f9-156">编译器会定义一个新的匿名类型，该类型具有两个属性： `Name` 和 `City` ，并使用指定的值创建它的实例。</span><span class="sxs-lookup"><span data-stu-id="874f9-156">The compiler defines a new anonymous type that has two properties, `Name` and `City`, and creates an instance of it with the specified values.</span></span> <span data-ttu-id="874f9-157">类型推理确定 `Name` `City` 要作为字符串的示例中和的类型。</span><span class="sxs-lookup"><span data-stu-id="874f9-157">Type inference determines the types of `Name` and `City` in the example to be strings.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="874f9-158">匿名类型的名称由编译器生成，并且可能因编译而异。</span><span class="sxs-lookup"><span data-stu-id="874f9-158">The name of the anonymous type is generated by the compiler, and may vary from compilation to compilation.</span></span> <span data-ttu-id="874f9-159">你的代码不应使用或依赖于匿名类型的名称。</span><span class="sxs-lookup"><span data-stu-id="874f9-159">Your code should not use or rely on the name of an anonymous type.</span></span>  
  
 <span data-ttu-id="874f9-160">由于类型名称不可用，因此不能使用 `As` 子句来声明 `cust13` 。</span><span class="sxs-lookup"><span data-stu-id="874f9-160">Because the name of the type is not available, you cannot use an `As` clause to declare `cust13`.</span></span> <span data-ttu-id="874f9-161">必须推断其类型。</span><span class="sxs-lookup"><span data-stu-id="874f9-161">Its type must be inferred.</span></span> <span data-ttu-id="874f9-162">如果不使用后期绑定，则这会将匿名类型限制为本地变量。</span><span class="sxs-lookup"><span data-stu-id="874f9-162">Without using late binding, this limits the use of anonymous types to local variables.</span></span>  
  
 <span data-ttu-id="874f9-163">匿名类型为 LINQ 查询提供关键支持。</span><span class="sxs-lookup"><span data-stu-id="874f9-163">Anonymous types provide critical support for LINQ queries.</span></span> <span data-ttu-id="874f9-164">有关在查询中使用匿名类型的详细信息，请参阅 Visual Basic 中的[匿名类型](anonymous-types.md)和[LINQ 简介](../linq/introduction-to-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="874f9-164">For more information about the use of anonymous types in queries, see [Anonymous Types](anonymous-types.md) and [Introduction to LINQ in Visual Basic](../linq/introduction-to-linq.md).</span></span>  
  
### <a name="remarks-about-anonymous-types"></a><span data-ttu-id="874f9-165">有关匿名类型的备注</span><span class="sxs-lookup"><span data-stu-id="874f9-165">Remarks About Anonymous Types</span></span>  
  
- <span data-ttu-id="874f9-166">通常，匿名类型声明中的所有属性或大多数属性都是关键属性，这些属性通过 `Key` 在属性名称前面键入关键字来指示。</span><span class="sxs-lookup"><span data-stu-id="874f9-166">Typically, all or most of the properties in an anonymous type declaration will be key properties, which are indicated by typing the keyword `Key` in front of the property name.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#14)]  
  
     <span data-ttu-id="874f9-167">有关密钥属性的详细信息，请参阅 "[密钥](../../../language-reference/modifiers/key.md)"。</span><span class="sxs-lookup"><span data-stu-id="874f9-167">For more information about key properties, see [Key](../../../language-reference/modifiers/key.md).</span></span>  
  
- <span data-ttu-id="874f9-168">与命名类型一样，匿名类型定义的初始化表达式列表必须声明至少一个属性。</span><span class="sxs-lookup"><span data-stu-id="874f9-168">Like named types, initializer lists for anonymous type definitions must declare at least one property.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
- <span data-ttu-id="874f9-169">声明匿名类型的实例时，编译器将生成匹配的匿名类型定义。</span><span class="sxs-lookup"><span data-stu-id="874f9-169">When an instance of an anonymous type is declared, the compiler generates a matching anonymous type definition.</span></span> <span data-ttu-id="874f9-170">属性的名称和数据类型取自实例声明，由编译器包含在定义中。</span><span class="sxs-lookup"><span data-stu-id="874f9-170">The names and data types of the properties are taken from the instance declaration, and are included by the compiler in the definition.</span></span> <span data-ttu-id="874f9-171">属性并未事先命名和定义，因为它们适用于命名类型。</span><span class="sxs-lookup"><span data-stu-id="874f9-171">The properties are not named and defined in advance, as they would be for a named type.</span></span> <span data-ttu-id="874f9-172">它们的类型会被推断。</span><span class="sxs-lookup"><span data-stu-id="874f9-172">Their types are inferred.</span></span> <span data-ttu-id="874f9-173">不能使用子句来指定属性的数据类型 `As` 。</span><span class="sxs-lookup"><span data-stu-id="874f9-173">You cannot specify the data types of the properties by using an `As` clause.</span></span>  
  
- <span data-ttu-id="874f9-174">匿名类型还可以通过多种其他方式建立其属性的名称和值。</span><span class="sxs-lookup"><span data-stu-id="874f9-174">Anonymous types can also establish the names and values of their properties in several other ways.</span></span> <span data-ttu-id="874f9-175">例如，匿名类型属性可以同时采用变量的名称和值，也可以同时采用另一对象的属性的名称和值。</span><span class="sxs-lookup"><span data-stu-id="874f9-175">For example, an anonymous type property can take both the name and the value of a variable, or the name and value of a property of another object.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#15)]  
  
     <span data-ttu-id="874f9-176">有关在匿名类型中定义属性的选项的详细信息，请参阅[如何：推断匿名类型声明中的属性名称和类型](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)。</span><span class="sxs-lookup"><span data-stu-id="874f9-176">For more information about the options for defining properties in anonymous types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="874f9-177">另请参阅</span><span class="sxs-lookup"><span data-stu-id="874f9-177">See also</span></span>

- [<span data-ttu-id="874f9-178">局部类型推理</span><span class="sxs-lookup"><span data-stu-id="874f9-178">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="874f9-179">匿名类型</span><span class="sxs-lookup"><span data-stu-id="874f9-179">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="874f9-180">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="874f9-180">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
- [<span data-ttu-id="874f9-181">如何：推断匿名类型声明中的属性名和类型</span><span class="sxs-lookup"><span data-stu-id="874f9-181">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="874f9-182">密钥</span><span class="sxs-lookup"><span data-stu-id="874f9-182">Key</span></span>](../../../language-reference/modifiers/key.md)
- [<span data-ttu-id="874f9-183">如何：使用对象初始值设定项声明对象</span><span class="sxs-lookup"><span data-stu-id="874f9-183">How to: Declare an Object by Using an Object Initializer</span></span>](how-to-declare-an-object-by-using-an-object-initializer.md)
