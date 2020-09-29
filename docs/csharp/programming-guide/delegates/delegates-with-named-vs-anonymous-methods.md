---
title: 带有命名方法的委托与匿名方法 - C# 编程指南
description: 了解通过命名或匿名方法进行的委托。 查看代码示例和其他可用资源。
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: d8d2c6d8c7792b81f2fc2e25d0836e3780e58e52
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202495"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a><span data-ttu-id="6aa1a-104">带有命名方法的委托与匿名方法（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="6aa1a-104">Delegates with Named vs. Anonymous Methods (C# Programming Guide)</span></span>

<span data-ttu-id="6aa1a-105">[委托](../../language-reference/builtin-types/reference-types.md)可以与命名方法相关联。</span><span class="sxs-lookup"><span data-stu-id="6aa1a-105">A [delegate](../../language-reference/builtin-types/reference-types.md) can be associated with a named method.</span></span> <span data-ttu-id="6aa1a-106">使用命名方法实例化委托时，该方法作为参数传递，例如：</span><span class="sxs-lookup"><span data-stu-id="6aa1a-106">When you instantiate a delegate by using a named method, the method is passed as a parameter, for example:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#1)]  
  
 <span data-ttu-id="6aa1a-107">这称为使用命名方法。</span><span class="sxs-lookup"><span data-stu-id="6aa1a-107">This is called using a named method.</span></span> <span data-ttu-id="6aa1a-108">使用命名方法构造的委托可以封装[静态](../../language-reference/keywords/static.md)方法或实例方法。</span><span class="sxs-lookup"><span data-stu-id="6aa1a-108">Delegates constructed with a named method can encapsulate either a [static](../../language-reference/keywords/static.md) method or an instance method.</span></span> <span data-ttu-id="6aa1a-109">命名方法是在早期版本的 C# 中实例化委托的唯一方式。</span><span class="sxs-lookup"><span data-stu-id="6aa1a-109">Named methods are the only way to instantiate a delegate in earlier versions of C#.</span></span> <span data-ttu-id="6aa1a-110">但是，如果创建新方法会造成多余开销，C# 允许你实例化委托并立即指定调用委托时委托将处理的代码块。</span><span class="sxs-lookup"><span data-stu-id="6aa1a-110">However, in a situation where creating a new method is unwanted overhead, C# enables you to instantiate a delegate and immediately specify a code block that the delegate will process when it is called.</span></span> <span data-ttu-id="6aa1a-111">代码块可包含 Lambda 表达式或匿名方法。</span><span class="sxs-lookup"><span data-stu-id="6aa1a-111">The block can contain either a lambda expression or an anonymous method.</span></span> <span data-ttu-id="6aa1a-112">有关详细信息，请参阅[匿名函数](../statements-expressions-operators/anonymous-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="6aa1a-112">For more information, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6aa1a-113">备注</span><span class="sxs-lookup"><span data-stu-id="6aa1a-113">Remarks</span></span>  

 <span data-ttu-id="6aa1a-114">作为委托参数传递的方法必须具有与委托声明相同的签名。</span><span class="sxs-lookup"><span data-stu-id="6aa1a-114">The method that you pass as a delegate parameter must have the same signature as the delegate declaration.</span></span>  
  
 <span data-ttu-id="6aa1a-115">委托实例可以封装静态方法或实例方法。</span><span class="sxs-lookup"><span data-stu-id="6aa1a-115">A delegate instance may encapsulate either static or instance method.</span></span>  
  
 <span data-ttu-id="6aa1a-116">尽管委托可以使用 [out](../../language-reference/keywords/out-parameter-modifier.md) 参数，但不建议将该委托与多播事件委托配合使用，因为你无法知道将调用哪个委托。</span><span class="sxs-lookup"><span data-stu-id="6aa1a-116">Although the delegate can use an [out](../../language-reference/keywords/out-parameter-modifier.md) parameter, we do not recommend its use with multicast event delegates because you cannot know which delegate will be called.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="6aa1a-117">示例 1</span><span class="sxs-lookup"><span data-stu-id="6aa1a-117">Example 1</span></span>  

 <span data-ttu-id="6aa1a-118">以下是声明和使用委托的简单示例。</span><span class="sxs-lookup"><span data-stu-id="6aa1a-118">The following is a simple example of declaring and using a delegate.</span></span> <span data-ttu-id="6aa1a-119">请注意，委托 `Del` 与关联的方法 `MultiplyNumbers` 具有相同的签名</span><span class="sxs-lookup"><span data-stu-id="6aa1a-119">Notice that both the delegate, `Del`, and the associated method, `MultiplyNumbers`, have the same signature</span></span>  
  
 [!code-csharp[csProgGuideDelegates#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#2)]  
  
## <a name="example-2"></a><span data-ttu-id="6aa1a-120">示例 2</span><span class="sxs-lookup"><span data-stu-id="6aa1a-120">Example 2</span></span>  

 <span data-ttu-id="6aa1a-121">在下面的示例中，一个委托映射到静态方法和实例方法，并返回来自两种方法的具体信息。</span><span class="sxs-lookup"><span data-stu-id="6aa1a-121">In the following example, one delegate is mapped to both static and instance methods and returns specific information from each.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="6aa1a-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6aa1a-122">See also</span></span>

- [<span data-ttu-id="6aa1a-123">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="6aa1a-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6aa1a-124">委托</span><span class="sxs-lookup"><span data-stu-id="6aa1a-124">Delegates</span></span>](./index.md)
- [<span data-ttu-id="6aa1a-125">如何合并委托（多播委托）</span><span class="sxs-lookup"><span data-stu-id="6aa1a-125">How to combine delegates (Multicast Delegates)</span></span>](./how-to-combine-delegates-multicast-delegates.md)
- [<span data-ttu-id="6aa1a-126">事件</span><span class="sxs-lookup"><span data-stu-id="6aa1a-126">Events</span></span>](../events/index.md)
