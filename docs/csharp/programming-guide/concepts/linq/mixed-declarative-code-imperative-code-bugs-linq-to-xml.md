---
title: 混合声明性代码-命令性代码的问题 (LINQ to XML) (C#)
description: LINQ to XML 方法可以直接修改 XML 树。 在修改 XML 树期间循环访问其中一个轴可能会引发奇怪的 bug。
ms.date: 07/20/2015
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 4eaed10f0a2e64abeb7725dcd70816d75d8a0423
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165289"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-c"></a><span data-ttu-id="dbfd2-104">混合声明性代码/命令性代码的问题 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="dbfd2-104">Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="dbfd2-105">包含各种不同的方法，使您能够直接修改 XML 树。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-105">contains various methods that allow you to modify an XML tree directly.</span></span> <span data-ttu-id="dbfd2-106">您可以添加元素、删除元素、更改元素的内容、添加属性等等。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-106">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span></span> <span data-ttu-id="dbfd2-107">在[修改 XML 树 (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md) 中详细介绍了此编程接口。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-107">This programming interface is described in [Modifying XML Trees (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span> <span data-ttu-id="dbfd2-108">如果循环访问一个轴，例如 <xref:System.Xml.Linq.XContainer.Elements%2A>，而在循环访问该轴时正在修改 XML 树，那么可能会发生一些异常问题。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-108">If you are iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you are modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span></span>  
  
 <span data-ttu-id="dbfd2-109">此问题有时称为“万圣节问题”。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-109">This problem is sometimes known as "The Halloween Problem".</span></span>  
  
## <a name="definition-of-the-problem"></a><span data-ttu-id="dbfd2-110">问题的定义</span><span class="sxs-lookup"><span data-stu-id="dbfd2-110">Definition of the Problem</span></span>  
 <span data-ttu-id="dbfd2-111">如果你使用 LINQ 编写循环访问集合的代码，那么你是以声明性风格在编写代码。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-111">When you write some code using LINQ that iterates through a collection, you are writing code in a declarative style.</span></span> <span data-ttu-id="dbfd2-112">这种风格更像是描述要实现的内容，而不是描述所需要的实现方式。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-112">It is more akin to describing *what* you want, rather that *how* you want to get it done.</span></span> <span data-ttu-id="dbfd2-113">如果你编写的代码要执行以下操作：1) 获取第一个元素；2) 测试该元素是否符合某种条件；3) 修改该元素；4) 将该元素放回列表中。那么，此代码就是命令性代码。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-113">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span></span> <span data-ttu-id="dbfd2-114">你是在告诉计算机希望以何种方式完成任务。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-114">You are telling the computer *how* to do what you want done.</span></span>  
  
 <span data-ttu-id="dbfd2-115">在同一操作中混合这些代码风格正是导致问题的原因。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-115">Mixing these styles of code in the same operation is what leads to problems.</span></span> <span data-ttu-id="dbfd2-116">考虑以下情况：</span><span class="sxs-lookup"><span data-stu-id="dbfd2-116">Consider the following:</span></span>  
  
 <span data-ttu-id="dbfd2-117">假设您有一个链接列表，其中有三个项（a、b 和 c）：</span><span class="sxs-lookup"><span data-stu-id="dbfd2-117">Suppose you have a linked list with three items in it (a, b, and c):</span></span>  
  
 `a -> b -> c`  
  
 <span data-ttu-id="dbfd2-118">现在，假设您想在链接列表中移动，并添加三个新项（a'、b' 和 c'）。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-118">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span></span> <span data-ttu-id="dbfd2-119">您希望生成如下所示的链接列表：</span><span class="sxs-lookup"><span data-stu-id="dbfd2-119">You want the resulting linked list to look like this:</span></span>  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 <span data-ttu-id="dbfd2-120">因此您编写代码来循环访问该列表，在每一项后面紧接着添加一个新项。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-120">So you write code that iterates through the list, and for every item, adds a new item right after it.</span></span> <span data-ttu-id="dbfd2-121">而实际发生的情况是，您的代码首先将看到 `a` 元素，然后在它后面插入 `a'`。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-121">What happens is that your code will first see the `a` element, and insert `a'` after it.</span></span> <span data-ttu-id="dbfd2-122">现在，您的代码将移动到列表中的下一节点，此时下一节点是 `a'`！</span><span class="sxs-lookup"><span data-stu-id="dbfd2-122">Now, your code will move to the next node in the list, which is now `a'`!</span></span> <span data-ttu-id="dbfd2-123">它会不假思索地向列表中添加一个新项 `a''`。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-123">It happily adds a new item to the list, `a''`.</span></span>  
  
 <span data-ttu-id="dbfd2-124">在实际中该如何解决这一问题？</span><span class="sxs-lookup"><span data-stu-id="dbfd2-124">How would you solve this in the real world?</span></span> <span data-ttu-id="dbfd2-125">您可以创建原始链接列表的副本，然后创建一个全新的列表。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-125">Well, you might make a copy of the original linked list, and create a completely new list.</span></span> <span data-ttu-id="dbfd2-126">或者，如果您正在编写纯粹的命令性代码，您可以找到第一项，添加新项，然后在链接列表中前进两步，跳过刚添加的元素。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-126">Or if you are writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span></span>  
  
## <a name="adding-while-iterating"></a><span data-ttu-id="dbfd2-127">循环访问时添加</span><span class="sxs-lookup"><span data-stu-id="dbfd2-127">Adding While Iterating</span></span>  
 <span data-ttu-id="dbfd2-128">例如，假设您希望编写一段代码，让它为树中的每个元素创建一个重复的元素：</span><span class="sxs-lookup"><span data-stu-id="dbfd2-128">For example, suppose you want to write some code that for every element in a tree, you want to create a duplicate element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 <span data-ttu-id="dbfd2-129">此代码将进入一个无限循环。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-129">This code goes into an infinite loop.</span></span> <span data-ttu-id="dbfd2-130">`foreach` 语句循环访问 `Elements()` 轴，将新元素添加到 `doc` 元素。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-130">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span></span> <span data-ttu-id="dbfd2-131">结果它也循环访问刚添加的元素。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-131">It ends up iterating also through the elements it just added.</span></span> <span data-ttu-id="dbfd2-132">由于它在每次循环访问中都分配新对象，最终将会耗尽所有可用内存。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-132">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span></span>  
  
 <span data-ttu-id="dbfd2-133">可以通过使用 <xref:System.Linq.Enumerable.ToList%2A> 标准查询运算符将集合放入内存来修复此问题，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dbfd2-133">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements().ToList())  
    root.Add(new XElement(e.Name, (string)e));  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="dbfd2-134">现在代码可以正常工作了。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-134">Now the code works.</span></span> <span data-ttu-id="dbfd2-135">生成的 XML 树如下所示：</span><span class="sxs-lookup"><span data-stu-id="dbfd2-135">The resulting XML tree is the following:</span></span>  
  
```xml  
<Root>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
## <a name="deleting-while-iterating"></a><span data-ttu-id="dbfd2-136">循环访问时删除</span><span class="sxs-lookup"><span data-stu-id="dbfd2-136">Deleting While Iterating</span></span>  
 <span data-ttu-id="dbfd2-137">如果想要删除某一级别上的所有节点，您可能立即想到编写类似如下所示的代码：</span><span class="sxs-lookup"><span data-stu-id="dbfd2-137">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    e.Remove();  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="dbfd2-138">然而，此代码执行起来不会如您所愿。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-138">However, this does not do what you want.</span></span> <span data-ttu-id="dbfd2-139">在这种情况下，在移除第一个元素 A 之后，将从包含在根中的 XML 树中移除该元素，Elements 方法中执行循环访问的代码将找不到下一个元素。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-139">In this situation, after you have removed the first element, A, it is removed from the XML tree contained in root, and the code in the Elements method that is doing the iterating cannot find the next element.</span></span>  
  
 <span data-ttu-id="dbfd2-140">前面的代码产生以下输出：</span><span class="sxs-lookup"><span data-stu-id="dbfd2-140">The preceding code produces the following output:</span></span>  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 <span data-ttu-id="dbfd2-141">解决方法仍是调用 <xref:System.Linq.Enumerable.ToList%2A> 来具体化集合，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dbfd2-141">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements().ToList())  
    e.Remove();  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="dbfd2-142">此代码产生以下输出：</span><span class="sxs-lookup"><span data-stu-id="dbfd2-142">This produces the following output:</span></span>  
  
```xml  
<Root />  
```  
  
 <span data-ttu-id="dbfd2-143">或者，可以通过对父元素调用 <xref:System.Xml.Linq.XElement.RemoveAll%2A> 来完全消除循环：</span><span class="sxs-lookup"><span data-stu-id="dbfd2-143">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
root.RemoveAll();  
Console.WriteLine(root);  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a><span data-ttu-id="dbfd2-144">为何 LINQ 不能自动处理此问题？</span><span class="sxs-lookup"><span data-stu-id="dbfd2-144">Why Can't LINQ Automatically Handle This?</span></span>  
 <span data-ttu-id="dbfd2-145">一种方法是总是将所有内容放入内存，而不是执行迟缓计算。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-145">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span></span> <span data-ttu-id="dbfd2-146">但是，在性能和内存使用方面，这种方法开销非常大。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-146">However, it would be very expensive in terms of performance and memory use.</span></span> <span data-ttu-id="dbfd2-147">事实上，如果 LINQ 和 (LINQ to XML) 采用此方法，在实际情况中将会失败。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-147">In fact, if LINQ and (LINQ to XML) were to take this approach, it would fail in real-world situations.</span></span>  
  
 <span data-ttu-id="dbfd2-148">另一种可能的方法是将某种事务语法放入 LINQ，让编译器尝试分析代码并确定是否需要具体化任何特定的集合。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-148">Another possible approach would be to put in some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code and determine if any particular collection needed to be materialized.</span></span> <span data-ttu-id="dbfd2-149">但是，尝试确定具有副作用的所有代码将会非常复杂。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-149">However, attempting to determine all code that has side-effects is incredibly complex.</span></span> <span data-ttu-id="dbfd2-150">考虑下列代码：</span><span class="sxs-lookup"><span data-stu-id="dbfd2-150">Consider the following code:</span></span>  
  
```csharp  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 <span data-ttu-id="dbfd2-151">这种分析代码需要分析 TestSomeCondition 和 DoMyProjection 方法，以及这些方法调用的所有方法，以此来确定是否有任何代码会产生副作用。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-151">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span></span> <span data-ttu-id="dbfd2-152">但是，分析代码不能简单地查找所有具有副作用的代码。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-152">But the analysis code could not just look for any code that had side-effects.</span></span> <span data-ttu-id="dbfd2-153">在此情况下，它需要选择只对 `root` 的子元素具有副作用的代码。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-153">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span></span>  
  
 <span data-ttu-id="dbfd2-154">LINQ to XML 不会尝试进行任何这样的分析。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-154">LINQ to XML does not attempt to do any such analysis.</span></span>  
  
 <span data-ttu-id="dbfd2-155">因此，避免这些问题就靠您了。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-155">It is up to you to avoid these problems.</span></span>  
  
## <a name="guidance"></a><span data-ttu-id="dbfd2-156">指导</span><span class="sxs-lookup"><span data-stu-id="dbfd2-156">Guidance</span></span>  
 <span data-ttu-id="dbfd2-157">首先，不要将声明性代码和命令性代码混合。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-157">First, do not mix declarative and imperative code.</span></span>  
  
 <span data-ttu-id="dbfd2-158">即便您确切知道您的集合的语义以及修改 XML 树的方法的语义，可以更巧妙地编写代码来避免这类问题，但您的代码将来需要由其他开发人员来维护，而他们可能并不像您那样清楚这些问题。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-158">Even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree, if you write some clever code that avoids these categories of problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span></span> <span data-ttu-id="dbfd2-159">如果混合使用声明性和命令性编码风格，您的代码将更加脆弱。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-159">If you mix declarative and imperative coding styles, your code will be more brittle.</span></span>  
  
 <span data-ttu-id="dbfd2-160">如果您编写代码将集合具体化从而避免这些问题，应在代码中适当加以注释，使负责维护的程序员能够了解问题所在。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-160">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span></span>  
  
 <span data-ttu-id="dbfd2-161">其次，在性能和其他因素允许的情况下，仅使用声明性代码。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-161">Second, if performance and other considerations allow, use only declarative code.</span></span> <span data-ttu-id="dbfd2-162">不要修改现有的 XML 树，</span><span class="sxs-lookup"><span data-stu-id="dbfd2-162">Don't modify your existing XML tree.</span></span> <span data-ttu-id="dbfd2-163">而是生成一个新树。</span><span class="sxs-lookup"><span data-stu-id="dbfd2-163">Generate a new one.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
XElement newRoot = new XElement("Root",  
    root.Elements(),  
    root.Elements()  
);  
Console.WriteLine(newRoot);  
```  
