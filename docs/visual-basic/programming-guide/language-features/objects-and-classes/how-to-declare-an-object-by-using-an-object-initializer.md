---
title: 如何：使用对象初始值设定项声明对象
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: cf4954059a4b0bf015bed82a74357ecfd5f5987e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404870"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a><span data-ttu-id="688d1-102">如何：使用对象初始值设定项声明对象 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="688d1-102">How to: Declare an Object by Using an Object Initializer (Visual Basic)</span></span>
<span data-ttu-id="688d1-103">使用对象初始值设定项可在单个语句中声明和实例化类的实例。</span><span class="sxs-lookup"><span data-stu-id="688d1-103">Object initializers enable you to declare and instantiate an instance of a class in a single statement.</span></span> <span data-ttu-id="688d1-104">此外，您可以同时初始化实例的一个或多个成员，而无需调用参数化的构造函数。</span><span class="sxs-lookup"><span data-stu-id="688d1-104">In addition, you can initialize one or more members of the instance at the same time, without invoking a parameterized constructor.</span></span>  
  
 <span data-ttu-id="688d1-105">使用对象初始值设定项创建命名类型的实例时，将调用类的无参数构造函数，然后按照指定的顺序初始化指定成员。</span><span class="sxs-lookup"><span data-stu-id="688d1-105">When you use an object initializer to create an instance of a named type, the parameterless constructor for the class is called, followed by initialization of designated members in the order you specify.</span></span>  
  
 <span data-ttu-id="688d1-106">下面的过程演示了如何 `Student` 通过三种不同的方式创建类的实例。</span><span class="sxs-lookup"><span data-stu-id="688d1-106">The following procedure shows how to create an instance of a `Student` class in three different ways.</span></span> <span data-ttu-id="688d1-107">类具有名字、姓氏和类年属性以及其他属性。</span><span class="sxs-lookup"><span data-stu-id="688d1-107">The class has first name, last name, and class year properties, among others.</span></span> <span data-ttu-id="688d1-108">这三个声明都将创建的新实例 `Student` ，并将属性 `First` 设置为 "Michael"， `Last` 将属性设置为 "Tucker"，并将所有其他成员设置为其默认值。</span><span class="sxs-lookup"><span data-stu-id="688d1-108">Each of the three declarations creates a new instance of `Student`, with property `First` set to "Michael", property `Last` set to "Tucker", and all other members set to their default values.</span></span> <span data-ttu-id="688d1-109">此过程中每个声明的结果等效于下面的示例，该示例不使用对象初始值设定项。</span><span class="sxs-lookup"><span data-stu-id="688d1-109">The result of each declaration in the procedure is equivalent to the following example, which does not use an object initializer.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 <span data-ttu-id="688d1-110">有关类的实现 `Student` ，请参阅[如何：创建项列表](../../concepts/linq/how-to-create-a-list-of-items.md)。</span><span class="sxs-lookup"><span data-stu-id="688d1-110">For an implementation of the `Student` class, see [How to: Create a List of Items](../../concepts/linq/how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="688d1-111">你可以从该主题复制代码以设置类，并创建 `Student` 要使用的对象的列表。</span><span class="sxs-lookup"><span data-stu-id="688d1-111">You can copy the code from that topic to set up the class and create a list of `Student` objects to work with.</span></span>  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a><span data-ttu-id="688d1-112">使用对象初始值设定项创建命名类的对象</span><span class="sxs-lookup"><span data-stu-id="688d1-112">To create an object of a named class by using an object initializer</span></span>  
  
1. <span data-ttu-id="688d1-113">开始声明，就像计划使用构造函数一样。</span><span class="sxs-lookup"><span data-stu-id="688d1-113">Begin the declaration as if you planned to use a constructor.</span></span>  
  
     `Dim student1 As New Student`  
  
2. <span data-ttu-id="688d1-114">键入关键字 `With` ，后跟一个用大括号括起来的初始化列表。</span><span class="sxs-lookup"><span data-stu-id="688d1-114">Type the keyword `With`, followed by an initialization list in braces.</span></span>  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3. <span data-ttu-id="688d1-115">在初始化列表中，包含要初始化的每个属性，并为其分配初始值。</span><span class="sxs-lookup"><span data-stu-id="688d1-115">In the initialization list, include each property that you want to initialize and assign an initial value to it.</span></span> <span data-ttu-id="688d1-116">属性的名称前面有一个句点。</span><span class="sxs-lookup"><span data-stu-id="688d1-116">The name of the property is preceded by a period.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     <span data-ttu-id="688d1-117">可以初始化类的一个或多个成员。</span><span class="sxs-lookup"><span data-stu-id="688d1-117">You can initialize one or more members of the class.</span></span>  
  
4. <span data-ttu-id="688d1-118">或者，可以声明类的新实例，然后为其赋值。</span><span class="sxs-lookup"><span data-stu-id="688d1-118">Alternatively, you can declare a new instance of the class and then assign a value to it.</span></span> <span data-ttu-id="688d1-119">首先，声明的实例 `Student` ：</span><span class="sxs-lookup"><span data-stu-id="688d1-119">First, declare an instance of `Student`:</span></span>  
  
     `Dim student2 As Student`  
  
5. <span data-ttu-id="688d1-120">`Student`以正常方式开始创建实例。</span><span class="sxs-lookup"><span data-stu-id="688d1-120">Begin the creation of an instance of `Student` in the normal way.</span></span>  
  
     `Dim student2 As Student = New Student`  
  
6. <span data-ttu-id="688d1-121">键入 `With` ，然后键入一个对象初始值设定项来初始化新实例的一个或多个成员。</span><span class="sxs-lookup"><span data-stu-id="688d1-121">Type `With` and then an object initializer to initialize one or more members of the new instance.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7. <span data-ttu-id="688d1-122">您可以通过省略来简化前一步骤中的定义 `As Student` 。</span><span class="sxs-lookup"><span data-stu-id="688d1-122">You can simplify the definition in the previous step by omitting `As Student`.</span></span> <span data-ttu-id="688d1-123">如果执行此操作，编译器将 `student3` `Student` 通过使用局部类型推理来确定是否为的实例。</span><span class="sxs-lookup"><span data-stu-id="688d1-123">If you do this, the compiler determines that `student3` is an instance of `Student` by using local type inference.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     <span data-ttu-id="688d1-124">有关详细信息，请参阅[局部类型推理](../variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="688d1-124">For more information, see [Local Type Inference](../variables/local-type-inference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="688d1-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="688d1-125">See also</span></span>

- [<span data-ttu-id="688d1-126">局部类型推理</span><span class="sxs-lookup"><span data-stu-id="688d1-126">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="688d1-127">如何：创建项列表</span><span class="sxs-lookup"><span data-stu-id="688d1-127">How to: Create a List of Items</span></span>](../../concepts/linq/how-to-create-a-list-of-items.md)
- [<span data-ttu-id="688d1-128">对象初始值设定项：命名和匿名类型</span><span class="sxs-lookup"><span data-stu-id="688d1-128">Object Initializers: Named and Anonymous Types</span></span>](object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="688d1-129">匿名类型</span><span class="sxs-lookup"><span data-stu-id="688d1-129">Anonymous Types</span></span>](anonymous-types.md)
