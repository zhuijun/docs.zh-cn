---
title: 如何声明、实例化和使用委托 - C# 编程指南
description: 了解如何声明、实例化和使用委托。 参阅涉及 C# 1.0、2.0 和 3.0 及更高版本的示例。
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: b741b3bc9c03faaa5fa2c01bd8f70d4be9b099c2
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063661"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="d9c7f-104">如何声明、实例化和使用委托（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="d9c7f-104">How to declare, instantiate, and use a Delegate (C# Programming Guide)</span></span>
<span data-ttu-id="d9c7f-105">在 C# 1.0 和更高版本中，可以如下面的示例所示声明委托。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-105">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#13)]  
  
 [!code-csharp[csProgGuideDelegates#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#14)]  
  
 <span data-ttu-id="d9c7f-106">C# 2.0 提供了更简单的方法来编写前面的声明，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-106">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#32)]  
  
 <span data-ttu-id="d9c7f-107">在 C# 2.0 和更高版本中，还可以使用匿名方法来声明和初始化[委托](../../language-reference/builtin-types/reference-types.md)，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-107">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../language-reference/builtin-types/reference-types.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#15)]  
  
 <span data-ttu-id="d9c7f-108">在 C# 3.0 和更高版本中，还可以通过使用 lambda 表达式声明和实例化委托，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-108">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#31)]  
  
 <span data-ttu-id="d9c7f-109">有关详细信息，请参阅 [Lambda 表达式](../../language-reference/operators/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-109">For more information, see [Lambda Expressions](../../language-reference/operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="d9c7f-110">下面的示例演示如何声明、实例化和使用委托。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-110">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="d9c7f-111">`BookDB` 类封装用来维护书籍数据库的书店数据库。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-111">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="d9c7f-112">它公开一个方法 `ProcessPaperbackBooks`，用于在数据库中查找所有平装书并为每本书调用委托。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-112">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="d9c7f-113">使用的 `delegate` 类型名为 `ProcessBookDelegate`。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-113">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="d9c7f-114">`Test` 类使用此类打印平装书的书名和平均价格。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-114">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="d9c7f-115">使用委托提升书店数据库和客户端代码之间的良好分隔功能。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-115">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="d9c7f-116">客户端代码程序不知道如何存储书籍或书店代码如何查找平装书。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-116">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="d9c7f-117">书店代码不知道它在找到平装书之后对其执行什么处理。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-117">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9c7f-118">示例</span><span class="sxs-lookup"><span data-stu-id="d9c7f-118">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d9c7f-119">可靠编程</span><span class="sxs-lookup"><span data-stu-id="d9c7f-119">Robust Programming</span></span>  
  
- <span data-ttu-id="d9c7f-120">声明委托。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-120">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="d9c7f-121">以下语句声明新的委托类型。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-121">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#16)]  
  
     <span data-ttu-id="d9c7f-122">每个委托类型描述自变量的数量和类型，以及它可以封装的方法的返回值类型。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-122">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="d9c7f-123">每当需要一组新的自变量类型或返回值类型，则必须声明一个新的委托类型。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-123">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
- <span data-ttu-id="d9c7f-124">实例化委托。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-124">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="d9c7f-125">声明委托类型后，则必须创建委托对象并将其与特定的方法相关联。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-125">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="d9c7f-126">在上例中，你通过将 `PrintTitle` 方法传递给 `ProcessPaperbackBooks` 方法执行此操作，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="d9c7f-126">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#17)]  
  
     <span data-ttu-id="d9c7f-127">这将创建一个新的与[静态](../../language-reference/keywords/static.md)方法 `Test.PrintTitle` 关联的委托对象。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-127">This creates a new delegate object associated with the [static](../../language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="d9c7f-128">同样，如下面的示例所示，传递对象 `totaller` 中的非静态方法 `AddBookToTotal`：</span><span class="sxs-lookup"><span data-stu-id="d9c7f-128">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#18)]  
  
     <span data-ttu-id="d9c7f-129">在这两种情况下，都将新的委托对象传递给 `ProcessPaperbackBooks` 方法。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-129">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="d9c7f-130">创建委托后，它与之关联的方法就永远不会更改；委托对象是不可变的。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-130">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
- <span data-ttu-id="d9c7f-131">调用委托。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-131">Calling a delegate.</span></span>  
  
     <span data-ttu-id="d9c7f-132">创建委托对象后，通常会将委托对象传递给将调用该委托的其他代码。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-132">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="d9c7f-133">委托对象是通过使用委托对象的名称调用的，后跟用圆括号括起来的将传递给委托的自变量。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-133">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="d9c7f-134">下面是一个委托调用示例：</span><span class="sxs-lookup"><span data-stu-id="d9c7f-134">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#19)]  
  
     <span data-ttu-id="d9c7f-135">委托可以同步调用（如在本例中）或通过使用 `BeginInvoke` 和 `EndInvoke` 方法异步调用。</span><span class="sxs-lookup"><span data-stu-id="d9c7f-135">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9c7f-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d9c7f-136">See also</span></span>

- [<span data-ttu-id="d9c7f-137">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="d9c7f-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d9c7f-138">事件</span><span class="sxs-lookup"><span data-stu-id="d9c7f-138">Events</span></span>](../events/index.md)
- [<span data-ttu-id="d9c7f-139">委托</span><span class="sxs-lookup"><span data-stu-id="d9c7f-139">Delegates</span></span>](./index.md)
