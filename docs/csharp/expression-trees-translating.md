---
title: 转换表达式树
description: 介绍如何访问表达式树中的每个节点，同时生成该表达式树的已修改副本。
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: cb64e79d915a5c5567d5a3d25f1d747df9687c87
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537458"
---
# <a name="translate-expression-trees"></a><span data-ttu-id="c9612-103">转换表达式树</span><span class="sxs-lookup"><span data-stu-id="c9612-103">Translate expression trees</span></span>

[<span data-ttu-id="c9612-104">上一部分 -- 生成表达式</span><span class="sxs-lookup"><span data-stu-id="c9612-104">Previous -- Building Expressions</span></span>](expression-trees-building.md)

<span data-ttu-id="c9612-105">在此最后一节中，将介绍如何访问表达式树中的每个节点，同时生成该表达式树的已修改副本。</span><span class="sxs-lookup"><span data-stu-id="c9612-105">In this final section, you'll learn how to visit each node in an expression tree while building a modified copy of that expression tree.</span></span> <span data-ttu-id="c9612-106">以下是在两个重要方案中将使用的技巧。</span><span class="sxs-lookup"><span data-stu-id="c9612-106">These are the techniques that you will use in two important scenarios.</span></span> <span data-ttu-id="c9612-107">第一种是了解表达式树表示的算法，以便可以将其转换到另一个环境中。</span><span class="sxs-lookup"><span data-stu-id="c9612-107">The first is to understand the algorithms expressed by an expression tree so that it can be translated into another environment.</span></span> <span data-ttu-id="c9612-108">第二种是何时更改已创建的算法。</span><span class="sxs-lookup"><span data-stu-id="c9612-108">The second is when you want to change the algorithm that has been created.</span></span> <span data-ttu-id="c9612-109">这可能是为了添加日志记录、拦截方法调用并跟踪它们，或其他目的。</span><span class="sxs-lookup"><span data-stu-id="c9612-109">This might be to add logging, intercept method calls and track them, or other purposes.</span></span>

## <a name="translating-is-visiting"></a><span data-ttu-id="c9612-110">转换即访问</span><span class="sxs-lookup"><span data-stu-id="c9612-110">Translating is Visiting</span></span>

<span data-ttu-id="c9612-111">生成的用于转换表达式树的代码是你已看到的用于访问树中所有节点的代码的扩展。</span><span class="sxs-lookup"><span data-stu-id="c9612-111">The code you build to translate an expression tree is an extension of what you've already seen to visit all the nodes in a tree.</span></span> <span data-ttu-id="c9612-112">转换表达式树时，会访问所有节点，并在访问它们的同时生成新树。</span><span class="sxs-lookup"><span data-stu-id="c9612-112">When you translate an expression tree, you visit all the nodes, and while visiting them, build the new tree.</span></span> <span data-ttu-id="c9612-113">新树可包含对原始节点的引用或已放置在树中的新节点。</span><span class="sxs-lookup"><span data-stu-id="c9612-113">The new tree may contain references to the original nodes, or new nodes that you have placed in the tree.</span></span>

<span data-ttu-id="c9612-114">让我们通过访问表达式树，并创建具有一些替换节点的新树，来查看其工作原理。</span><span class="sxs-lookup"><span data-stu-id="c9612-114">Let's see this in action by visiting an expression tree, and creating a new tree with some replacement nodes.</span></span> <span data-ttu-id="c9612-115">在此示例中，我们将任何常数替换为其十倍大的常数。</span><span class="sxs-lookup"><span data-stu-id="c9612-115">In this example, let's replace any constant with a constant that is ten times larger.</span></span>
<span data-ttu-id="c9612-116">要么就保持表达式树不变。</span><span class="sxs-lookup"><span data-stu-id="c9612-116">Otherwise, we'll leave the expression tree intact.</span></span> <span data-ttu-id="c9612-117">我们通过将常数节点替换为执行乘法运算的新节点来进行此替换，而不必阅读常数的值并将其替换为新的常数。</span><span class="sxs-lookup"><span data-stu-id="c9612-117">Rather than reading the value of the constant, and replacing it with a new constant, we'll make this replacement by replacing the constant node with a new node that performs the multiplication.</span></span>

<span data-ttu-id="c9612-118">此处，在找到常数节点后，创建新乘法节点（其子节点是原始常数和常数 `10`）：</span><span class="sxs-lookup"><span data-stu-id="c9612-118">Here, once you find a constant node, you create a new multiplication node whose children are the original constant, and the constant `10`:</span></span>

```csharp
private static Expression ReplaceNodes(Expression original)
{
    if (original.NodeType == ExpressionType.Constant)
    {
        return Expression.Multiply(original, Expression.Constant(10));
    }
    else if (original.NodeType == ExpressionType.Add)
    {
        var binaryExpression = (BinaryExpression)original;
        return Expression.Add(
            ReplaceNodes(binaryExpression.Left),
            ReplaceNodes(binaryExpression.Right));
    }
    return original;
}
```

<span data-ttu-id="c9612-119">通过替换原始节点，将形成一个包含修改的新树。</span><span class="sxs-lookup"><span data-stu-id="c9612-119">By replacing the original node with the substitute, a new tree is formed that contains our modifications.</span></span> <span data-ttu-id="c9612-120">可以通过编译并执行替换的树对此进行验证。</span><span class="sxs-lookup"><span data-stu-id="c9612-120">We can verify that by compiling and executing the replaced tree.</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
var sum = ReplaceNodes(addition);
var executableFunc = Expression.Lambda(sum);

var func = (Func<int>)executableFunc.Compile();
var answer = func();
Console.WriteLine(answer);
```

<span data-ttu-id="c9612-121">生成新树是两者的结合：访问现有树中的节点，和创建新节点并将其插入树中。</span><span class="sxs-lookup"><span data-stu-id="c9612-121">Building a new tree is a combination of visiting the nodes in the existing tree, and creating new nodes and inserting them into the tree.</span></span>

<span data-ttu-id="c9612-122">此示例演示了表达式树不可变这一点的重要性。</span><span class="sxs-lookup"><span data-stu-id="c9612-122">This example shows the importance of expression trees being immutable.</span></span> <span data-ttu-id="c9612-123">请注意，上面创建的新树混合了新创建的节点和现有树中的节点。</span><span class="sxs-lookup"><span data-stu-id="c9612-123">Notice that the new tree created above contains a mixture of newly created nodes, and nodes from the existing tree.</span></span> <span data-ttu-id="c9612-124">这是安全的，因为现有树中的节点无法进行修改。</span><span class="sxs-lookup"><span data-stu-id="c9612-124">That's safe, because the nodes in the existing tree cannot be modified.</span></span> <span data-ttu-id="c9612-125">这可以极大提高内存效率。</span><span class="sxs-lookup"><span data-stu-id="c9612-125">This can result in significant memory efficiencies.</span></span>
<span data-ttu-id="c9612-126">相同的节点可能会在整个树或多个表达式树中遍历使用。</span><span class="sxs-lookup"><span data-stu-id="c9612-126">The same nodes can be used throughout a tree, or in multiple expression trees.</span></span> <span data-ttu-id="c9612-127">由于不能修改节点，因此可以在需要时随时重用相同的节点。</span><span class="sxs-lookup"><span data-stu-id="c9612-127">Since nodes can't be modified, the same node can be reused whenever it's needed.</span></span>

## <a name="traversing-and-executing-an-addition"></a><span data-ttu-id="c9612-128">遍历并执行加法</span><span class="sxs-lookup"><span data-stu-id="c9612-128">Traversing and Executing an Addition</span></span>

<span data-ttu-id="c9612-129">让我们通过生成遍历加法节点的树并计算结果的第二个访问者来对此进行验证。</span><span class="sxs-lookup"><span data-stu-id="c9612-129">Let's verify this by building a second visitor that walks the tree of addition nodes and computes the result.</span></span> <span data-ttu-id="c9612-130">可以通过对目前见到的访问者进行一些修改来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="c9612-130">You can do this by making a couple modifications to the visitor that you've seen so far.</span></span> <span data-ttu-id="c9612-131">在此新版本中，访问者将返回到目前为止加法运算的部分总和。</span><span class="sxs-lookup"><span data-stu-id="c9612-131">In this new version, the visitor will return the partial sum of the addition operation up to this point.</span></span> <span data-ttu-id="c9612-132">对于常数表达式，该总和即为常数表达式的值。</span><span class="sxs-lookup"><span data-stu-id="c9612-132">For a constant expression, that is simply the value of the constant expression.</span></span> <span data-ttu-id="c9612-133">对于加法表达式，遍历这些树后，其结果为左操作数和右操作数的总和。</span><span class="sxs-lookup"><span data-stu-id="c9612-133">For an addition expression, the result is the sum of the left and right operands, once those trees have been traversed.</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var three= Expression.Constant(3, typeof(int));
var four = Expression.Constant(4, typeof(int));
var addition = Expression.Add(one, two);
var add2 = Expression.Add(three, four);
var sum = Expression.Add(addition, add2);

// Declare the delegate, so we can call it
// from itself recursively:
Func<Expression, int> aggregate = null;
// Aggregate, return constants, or the sum of the left and right operand.
// Major simplification: Assume every binary expression is an addition.
aggregate = (exp) =>
    exp.NodeType == ExpressionType.Constant ?
    (int)((ConstantExpression)exp).Value :
    aggregate(((BinaryExpression)exp).Left) + aggregate(((BinaryExpression)exp).Right);

var theSum = aggregate(sum);
Console.WriteLine(theSum);
```

<span data-ttu-id="c9612-134">此处有相当多的代码，但这些概念是非常容易理解的。</span><span class="sxs-lookup"><span data-stu-id="c9612-134">There's quite a bit of code here, but the concepts are very approachable.</span></span>
<span data-ttu-id="c9612-135">此代码访问首次深度搜索后的子级。</span><span class="sxs-lookup"><span data-stu-id="c9612-135">This code visits children in a depth first search.</span></span> <span data-ttu-id="c9612-136">当它遇到常数节点时，访问者将返回该常数的值。</span><span class="sxs-lookup"><span data-stu-id="c9612-136">When it encounters a constant node, the visitor returns the value of the constant.</span></span> <span data-ttu-id="c9612-137">访问者访问这两个子级之后，这些子级将计算出为该子树计算的总和。</span><span class="sxs-lookup"><span data-stu-id="c9612-137">After the visitor has visited both children, those children will have computed the sum computed for that subtree.</span></span> <span data-ttu-id="c9612-138">加法节点现在可以计算其总和。</span><span class="sxs-lookup"><span data-stu-id="c9612-138">The addition node can now compute its sum.</span></span>
<span data-ttu-id="c9612-139">在访问了表达式树中的所有节点后，将计算出总和。</span><span class="sxs-lookup"><span data-stu-id="c9612-139">Once all the nodes in the expression tree have been visited, the sum will have been computed.</span></span> <span data-ttu-id="c9612-140">可以通过在调试器中运行示例并跟踪执行来跟踪执行。</span><span class="sxs-lookup"><span data-stu-id="c9612-140">You can trace the execution by running the sample in the debugger and tracing the execution.</span></span>

<span data-ttu-id="c9612-141">让我们通过遍历树，来更轻松地跟踪如何分析节点以及如何计算总和。</span><span class="sxs-lookup"><span data-stu-id="c9612-141">Let's make it easier to trace how the nodes are analyzed and how the sum is computed by traversing the tree.</span></span> <span data-ttu-id="c9612-142">下面是包含大量跟踪信息的聚合方法的更新版本：</span><span class="sxs-lookup"><span data-stu-id="c9612-142">Here's an updated version of the Aggregate method that includes quite a bit of tracing information:</span></span>

```csharp
private static int Aggregate(Expression exp)
{
    if (exp.NodeType == ExpressionType.Constant)
    {
        var constantExp = (ConstantExpression)exp;
        Console.Error.WriteLine($"Found Constant: {constantExp.Value}");
        return (int)constantExp.Value;
    }
    else if (exp.NodeType == ExpressionType.Add)
    {
        var addExp = (BinaryExpression)exp;
        Console.Error.WriteLine("Found Addition Expression");
        Console.Error.WriteLine("Computing Left node");
        var leftOperand = Aggregate(addExp.Left);
        Console.Error.WriteLine($"Left is: {leftOperand}");
        Console.Error.WriteLine("Computing Right node");
        var rightOperand = Aggregate(addExp.Right);
        Console.Error.WriteLine($"Right is: {rightOperand}");
        var sum = leftOperand + rightOperand;
        Console.Error.WriteLine($"Computed sum: {sum}");
        return sum;
    }
    else throw new NotSupportedException("Haven't written this yet");
}
```

<span data-ttu-id="c9612-143">在同一表达式中运行该版本将生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="c9612-143">Running it on the same expression yields the following output:</span></span>

```output
10
Found Addition Expression
Computing Left node
Found Addition Expression
Computing Left node
Found Constant: 1
Left is: 1
Computing Right node
Found Constant: 2
Right is: 2
Computed sum: 3
Left is: 3
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 3
Left is: 3
Computing Right node
Found Constant: 4
Right is: 4
Computed sum: 7
Right is: 7
Computed sum: 10
10
```

<span data-ttu-id="c9612-144">跟踪输出，并在上面的代码中跟随。</span><span class="sxs-lookup"><span data-stu-id="c9612-144">Trace the output and follow along in the code above.</span></span> <span data-ttu-id="c9612-145">应当能够看出代码如何在遍历树的同时访问代码和计算总和，并得出总和。</span><span class="sxs-lookup"><span data-stu-id="c9612-145">You should be able to work out how the code visits each node and computes the sum as it goes through the tree and finds the sum.</span></span>

<span data-ttu-id="c9612-146">现在，让我们来看看另一个运行，其表达式由 `sum1` 给出：</span><span class="sxs-lookup"><span data-stu-id="c9612-146">Now, let's look at a different run, with the expression given by `sum1`:</span></span>

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

<span data-ttu-id="c9612-147">下面是通过检查此表达式得到的输出：</span><span class="sxs-lookup"><span data-stu-id="c9612-147">Here's the output from examining this expression:</span></span>

```output
Found Addition Expression
Computing Left node
Found Constant: 1
Left is: 1
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 2
Left is: 2
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 3
Left is: 3
Computing Right node
Found Constant: 4
Right is: 4
Computed sum: 7
Right is: 7
Computed sum: 9
Right is: 9
Computed sum: 10
10
```

<span data-ttu-id="c9612-148">虽然最终结果是相同的，但树遍历完全不同。</span><span class="sxs-lookup"><span data-stu-id="c9612-148">While the final answer is the same, the tree traversal is completely different.</span></span> <span data-ttu-id="c9612-149">节点的访问顺序不同，因为树是以首先发生的不同运算构造的。</span><span class="sxs-lookup"><span data-stu-id="c9612-149">The nodes are traveled in a different order, because the tree was constructed with different operations occurring first.</span></span>

## <a name="learning-more"></a><span data-ttu-id="c9612-150">了解更多信息</span><span class="sxs-lookup"><span data-stu-id="c9612-150">Learning More</span></span>

<span data-ttu-id="c9612-151">此示例演示了要生成的用于遍历和解释表达式树表示的算法的代码的一小部分。</span><span class="sxs-lookup"><span data-stu-id="c9612-151">This sample shows a small subset of the code you would build to traverse and interpret the algorithms represented by an expression tree.</span></span> <span data-ttu-id="c9612-152">有关生成将表达式树转换为其他语言的通用库所需的所有工作的完整讨论，请阅读 Matt Warren 的[这一系列](/archive/blogs/mattwar/linq-building-an-iqueryable-provider-series)。</span><span class="sxs-lookup"><span data-stu-id="c9612-152">For a complete discussion of all the work necessary to build a general purpose library that translates expression trees into another language, please read [this series](/archive/blogs/mattwar/linq-building-an-iqueryable-provider-series) by Matt Warren.</span></span> <span data-ttu-id="c9612-153">它详细介绍了如何转换可能在表达式树中找到的任意代码。</span><span class="sxs-lookup"><span data-stu-id="c9612-153">It goes into great detail on how to translate any of the code you might find in an expression tree.</span></span>

<span data-ttu-id="c9612-154">希望你现在已经见识到了表达式树的真正强大功能。</span><span class="sxs-lookup"><span data-stu-id="c9612-154">I hope you've now seen the true power of expression trees.</span></span>
<span data-ttu-id="c9612-155">你可以检查一组代码、对该代码进行任意更改，并执行更改后的版本。</span><span class="sxs-lookup"><span data-stu-id="c9612-155">You can examine a set of code, make any changes you'd like to that code, and execute the changed version.</span></span> <span data-ttu-id="c9612-156">由于表达式树是不可变的，你可以通过使用现有树的组件创建新树。</span><span class="sxs-lookup"><span data-stu-id="c9612-156">Because the expression trees are immutable, you can create new trees by using the components of existing trees.</span></span> <span data-ttu-id="c9612-157">这样可使创建修改的表达式树所需的内存量最小。</span><span class="sxs-lookup"><span data-stu-id="c9612-157">This minimizes the amount of memory needed to create modified expression trees.</span></span>

[<span data-ttu-id="c9612-158">下一部分 -- 总结</span><span class="sxs-lookup"><span data-stu-id="c9612-158">Next -- Summing up</span></span>](expression-trees-summary.md)
