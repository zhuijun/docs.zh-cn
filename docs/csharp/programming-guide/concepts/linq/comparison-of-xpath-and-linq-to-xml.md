---
title: XPath 和 LINQ to XML 的比较
description: 了解 C# 中 XPath 和 LINQ to XML 之间功能的相似性和差异。 你可使用这两种方法来查询 XML 树。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: e2f34903b20a53dea6e5ff4858d4fadaebd9c37a
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104003"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a><span data-ttu-id="5d8ef-104">XPath 和 LINQ to XML 的比较</span><span class="sxs-lookup"><span data-stu-id="5d8ef-104">Comparison of XPath and LINQ to XML</span></span>
<span data-ttu-id="5d8ef-105">XPath 和 LINQ to XML 提供一些类似的功能。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-105">XPath and LINQ to XML offer some similar functionality.</span></span> <span data-ttu-id="5d8ef-106">二者都可用于查询 XML 树，返回诸如元素集合、属性集合、节点集合或者元素或属性的值等这样的结果。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-106">Both can be used to query an XML tree, returning such results as a collection of elements, a collection of attributes, a collection of nodes, or the value of an element or attribute.</span></span> <span data-ttu-id="5d8ef-107">但也有一些差异。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-107">However, there are also some differences.</span></span>  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a><span data-ttu-id="5d8ef-108">XPath 和 LINQ to XML 之间的差异</span><span class="sxs-lookup"><span data-stu-id="5d8ef-108">Differences Between XPath and LINQ to XML</span></span>  
 <span data-ttu-id="5d8ef-109">XPath 不允许新类型的投影。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-109">XPath does not allow projection of new types.</span></span> <span data-ttu-id="5d8ef-110">它只能从树中返回节点集合，而 LINQ to XML 可以执行查询并将对象图或 XML 树投影为新形状。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-110">It can only return collections of nodes from the tree, whereas LINQ to XML can execute a query and project an object graph or an XML tree in a new shape.</span></span> <span data-ttu-id="5d8ef-111">LINQ to XML 查询包含更多功能并且比 XPath 表达式的功能强大得多。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-111">LINQ to XML queries encompass much more functionality and are much more powerful than XPath expressions.</span></span>  
  
 <span data-ttu-id="5d8ef-112">XPath 表达式在字符串中孤立存在。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-112">XPath expressions exist in isolation within a string.</span></span> <span data-ttu-id="5d8ef-113">C# 编译器无法在编译时帮助分析 XPath 表达式。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-113">The C# compiler cannot help parse the XPath expression at compile time.</span></span> <span data-ttu-id="5d8ef-114">相反，C# 编译器可以分析和编译 LINQ to XML 查询。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-114">By contrast, LINQ to XML queries are parsed and compiled by the C# compiler.</span></span> <span data-ttu-id="5d8ef-115">编译器能够捕捉许多查询错误。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-115">The compiler is able to catch many query errors.</span></span>  
  
 <span data-ttu-id="5d8ef-116">XPath 结果不是强类型。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-116">XPath results are not strongly typed.</span></span> <span data-ttu-id="5d8ef-117">在许多情况下，XPath 表达式的计算结果是一个对象，并且该对象需要由开发人员确定属性类型并根据需要强制转换结果。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-117">In a number of circumstances, the result of evaluating an XPath expression is an object, and it is up to the developer to determine the proper type and cast the result as necessary.</span></span> <span data-ttu-id="5d8ef-118">相比之下，LINQ to XML 查询生成的投影是强类型。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-118">By contrast, the projections from a LINQ to XML query are strongly typed.</span></span>  
  
## <a name="result-ordering"></a><span data-ttu-id="5d8ef-119">结果排序</span><span class="sxs-lookup"><span data-stu-id="5d8ef-119">Result Ordering</span></span>  
 <span data-ttu-id="5d8ef-120">XPath 1.0 建议规定，作为 XPath 表达式计算结果的集合是无序的。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-120">The XPath 1.0 Recommendation states that a collection that is the result of evaluating an XPath expression is unordered.</span></span>  
  
 <span data-ttu-id="5d8ef-121">但在循环访问由 LINQ to XML XPath 轴方法返回的集合时，集合中的节点将按文档顺序返回。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-121">However, when iterating through a collection returned by a LINQ to XML XPath axis method, the nodes in the collection are returned in document order.</span></span> <span data-ttu-id="5d8ef-122">即使是在访问按反向文档顺序表示谓词的 XPath 轴（如 `preceding` 和 `preceding-sibling`）时，情况也如此。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-122">This is the case even when accessing the XPath axes where predicates are expressed in terms of reverse document order, such as `preceding` and `preceding-sibling`.</span></span>  
  
 <span data-ttu-id="5d8ef-123">相比之下，多数 LINQ to XML 轴都按文档顺序返回集合，但其中 <xref:System.Xml.Linq.XNode.Ancestors%2A> 和 <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A> 两个轴按反向文档顺序返回集合。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-123">By contrast, most of the LINQ to XML axes return collections in document order, but two of them, <xref:System.Xml.Linq.XNode.Ancestors%2A> and <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, return collections in reverse document order.</span></span> <span data-ttu-id="5d8ef-124">下表枚举各个轴并指示每个轴的集合顺序：</span><span class="sxs-lookup"><span data-stu-id="5d8ef-124">The following table enumerates the axes, and indicates collection order for each:</span></span>  
  
|<span data-ttu-id="5d8ef-125">LINQ to XML 轴</span><span class="sxs-lookup"><span data-stu-id="5d8ef-125">LINQ to XML axis</span></span>|<span data-ttu-id="5d8ef-126">订购</span><span class="sxs-lookup"><span data-stu-id="5d8ef-126">Ordering</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="5d8ef-127">XContainer.DescendantNodes</span><span class="sxs-lookup"><span data-stu-id="5d8ef-127">XContainer.DescendantNodes</span></span>|<span data-ttu-id="5d8ef-128">文档顺序</span><span class="sxs-lookup"><span data-stu-id="5d8ef-128">Document order</span></span>|  
|<span data-ttu-id="5d8ef-129">XContainer.Descendants</span><span class="sxs-lookup"><span data-stu-id="5d8ef-129">XContainer.Descendants</span></span>|<span data-ttu-id="5d8ef-130">文档顺序</span><span class="sxs-lookup"><span data-stu-id="5d8ef-130">Document order</span></span>|  
|<span data-ttu-id="5d8ef-131">XContainer.Elements</span><span class="sxs-lookup"><span data-stu-id="5d8ef-131">XContainer.Elements</span></span>|<span data-ttu-id="5d8ef-132">文档顺序</span><span class="sxs-lookup"><span data-stu-id="5d8ef-132">Document order</span></span>|  
|<span data-ttu-id="5d8ef-133">XContainer.Nodes</span><span class="sxs-lookup"><span data-stu-id="5d8ef-133">XContainer.Nodes</span></span>|<span data-ttu-id="5d8ef-134">文档顺序</span><span class="sxs-lookup"><span data-stu-id="5d8ef-134">Document order</span></span>|  
|<span data-ttu-id="5d8ef-135">XContainer.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="5d8ef-135">XContainer.NodesAfterSelf</span></span>|<span data-ttu-id="5d8ef-136">文档顺序</span><span class="sxs-lookup"><span data-stu-id="5d8ef-136">Document order</span></span>|  
|<span data-ttu-id="5d8ef-137">XContainer.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="5d8ef-137">XContainer.NodesBeforeSelf</span></span>|<span data-ttu-id="5d8ef-138">文档顺序</span><span class="sxs-lookup"><span data-stu-id="5d8ef-138">Document order</span></span>|  
|<span data-ttu-id="5d8ef-139">XElement.AncestorsAndSelf</span><span class="sxs-lookup"><span data-stu-id="5d8ef-139">XElement.AncestorsAndSelf</span></span>|<span data-ttu-id="5d8ef-140">反向文档顺序</span><span class="sxs-lookup"><span data-stu-id="5d8ef-140">Reverse document order</span></span>|  
|<span data-ttu-id="5d8ef-141">XElement.Attributes</span><span class="sxs-lookup"><span data-stu-id="5d8ef-141">XElement.Attributes</span></span>|<span data-ttu-id="5d8ef-142">文档顺序</span><span class="sxs-lookup"><span data-stu-id="5d8ef-142">Document order</span></span>|  
|<span data-ttu-id="5d8ef-143">XElement.DescendantNodesAndSelf</span><span class="sxs-lookup"><span data-stu-id="5d8ef-143">XElement.DescendantNodesAndSelf</span></span>|<span data-ttu-id="5d8ef-144">文档顺序</span><span class="sxs-lookup"><span data-stu-id="5d8ef-144">Document order</span></span>|  
|<span data-ttu-id="5d8ef-145">XElement.DescendantsAndSelf</span><span class="sxs-lookup"><span data-stu-id="5d8ef-145">XElement.DescendantsAndSelf</span></span>|<span data-ttu-id="5d8ef-146">文档顺序</span><span class="sxs-lookup"><span data-stu-id="5d8ef-146">Document order</span></span>|  
|<span data-ttu-id="5d8ef-147">XNode.Ancestors</span><span class="sxs-lookup"><span data-stu-id="5d8ef-147">XNode.Ancestors</span></span>|<span data-ttu-id="5d8ef-148">反向文档顺序</span><span class="sxs-lookup"><span data-stu-id="5d8ef-148">Reverse document order</span></span>|  
|<span data-ttu-id="5d8ef-149">XNode.ElementsAfterSelf</span><span class="sxs-lookup"><span data-stu-id="5d8ef-149">XNode.ElementsAfterSelf</span></span>|<span data-ttu-id="5d8ef-150">文档顺序</span><span class="sxs-lookup"><span data-stu-id="5d8ef-150">Document order</span></span>|  
|<span data-ttu-id="5d8ef-151">XNode.ElementsBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="5d8ef-151">XNode.ElementsBeforeSelf</span></span>|<span data-ttu-id="5d8ef-152">文档顺序</span><span class="sxs-lookup"><span data-stu-id="5d8ef-152">Document order</span></span>|  
|<span data-ttu-id="5d8ef-153">XNode.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="5d8ef-153">XNode.NodesAfterSelf</span></span>|<span data-ttu-id="5d8ef-154">文档顺序</span><span class="sxs-lookup"><span data-stu-id="5d8ef-154">Document order</span></span>|  
|<span data-ttu-id="5d8ef-155">XNode.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="5d8ef-155">XNode.NodesBeforeSelf</span></span>|<span data-ttu-id="5d8ef-156">文档顺序</span><span class="sxs-lookup"><span data-stu-id="5d8ef-156">Document order</span></span>|  
  
## <a name="positional-predicates"></a><span data-ttu-id="5d8ef-157">位置谓词</span><span class="sxs-lookup"><span data-stu-id="5d8ef-157">Positional Predicates</span></span>  
 <span data-ttu-id="5d8ef-158">在 XPath 表达式中，很多轴的位置谓词都按文档顺序表示，但是反向轴 `preceding`、`preceding-sibling`、`ancestor` 和 `ancestor-or-self` 则按反向文档顺序表示。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-158">Within an XPath expression, positional predicates are expressed in terms of document order for many axes, but are expressed in reverse document order for reverse axes, which are `preceding`, `preceding-sibling`, `ancestor`, and `ancestor-or-self`.</span></span> <span data-ttu-id="5d8ef-159">例如，XPath 表达式 `preceding-sibling::*[1]` 返回前面紧邻的同级。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-159">For example, the XPath expression `preceding-sibling::*[1]` returns the immediately preceding sibling.</span></span> <span data-ttu-id="5d8ef-160">即使最终结果集按文档顺序表示，情况也是这样。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-160">This is the case even though the final result set is presented in document order.</span></span>  
  
 <span data-ttu-id="5d8ef-161">相比之下，LINQ to XML 中的所有位置谓词始终按轴顺序表示。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-161">By contrast, all positional predicates in LINQ to XML are always expressed in terms of the order of the axis.</span></span> <span data-ttu-id="5d8ef-162">例如，`anElement.ElementsBeforeSelf().ElementAt(0)` 返回所查询元素的父级的第一个子元素，而不是前面紧邻的同级。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-162">For example, `anElement.ElementsBeforeSelf().ElementAt(0)` returns the first child element of the parent of the queried element, not the immediate preceding sibling.</span></span> <span data-ttu-id="5d8ef-163">再例如：`anElement.Ancestors().ElementAt(0)` 返回父元素。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-163">Another example: `anElement.Ancestors().ElementAt(0)` returns the parent element.</span></span>  
  
 <span data-ttu-id="5d8ef-164">如果要查找 LINQ to XML 中的前面紧邻元素，则应编写下面的表达式：</span><span class="sxs-lookup"><span data-stu-id="5d8ef-164">If you wanted to find the immediately preceding element in LINQ to XML, you would write the following expression:</span></span>  
  
```csharp
ElementsBeforeSelf().Last()
```
  
```vb
ElementsBeforeSelf().Last()
```
  
## <a name="performance-differences"></a><span data-ttu-id="5d8ef-165">性能差异</span><span class="sxs-lookup"><span data-stu-id="5d8ef-165">Performance Differences</span></span>  
 <span data-ttu-id="5d8ef-166">使用 LINQ to XML 中 XPath 功能的 XPath 查询的执行性能比 LINQ to XML 查询低。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-166">XPath queries that use the XPath functionality in LINQ to XML will not perform as well as LINQ to XML queries.</span></span>  
  
## <a name="comparison-of-composition"></a><span data-ttu-id="5d8ef-167">撰写方式的比较</span><span class="sxs-lookup"><span data-stu-id="5d8ef-167">Comparison of Composition</span></span>  
 <span data-ttu-id="5d8ef-168">LINQ to XML 查询的撰写在某种程度上类似于 XPath 表达式的撰写，但其语法大不相同。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-168">Composition of a LINQ to XML query is somewhat parallel to composition of an XPath expression, although very different in syntax.</span></span>  
  
 <span data-ttu-id="5d8ef-169">例如，如果名为 `customers` 的变量中有一个元素，并且您想在所有名为 `CompanyName` 的子级元素下查找名为 `Customer` 的孙级元素，则应编写如下所示的 XPath 表达式：</span><span class="sxs-lookup"><span data-stu-id="5d8ef-169">For example, if you have an element in a variable named `customers`, and you want to find a grandchild element named `CompanyName` under all child elements named `Customer`, you would write an XPath expression as follows:</span></span>  
  
```csharp  
customers.XPathSelectElements("./Customer/CompanyName")
```  
  
```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

 <span data-ttu-id="5d8ef-170">等效的 LINQ to XML 查询是：</span><span class="sxs-lookup"><span data-stu-id="5d8ef-170">The equivalent LINQ to XML query is:</span></span>  
  
```csharp  
customers.Elements("Customer").Elements("CompanyName")
```  
  
```vb
customers.Elements("Customer").Elements("CompanyName")
```  

 <span data-ttu-id="5d8ef-171">每个 XPath 轴都有一些相似处。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-171">There are similar parallels for each of the XPath axes.</span></span>  
  
|<span data-ttu-id="5d8ef-172">XPath 轴</span><span class="sxs-lookup"><span data-stu-id="5d8ef-172">XPath axis</span></span>|<span data-ttu-id="5d8ef-173">LINQ to XML 轴</span><span class="sxs-lookup"><span data-stu-id="5d8ef-173">LINQ to XML axis</span></span>|  
|----------------|----------------------|  
|<span data-ttu-id="5d8ef-174">子级（默认轴）</span><span class="sxs-lookup"><span data-stu-id="5d8ef-174">child (the default axis)</span></span>|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5d8ef-175">父级 (..)</span><span class="sxs-lookup"><span data-stu-id="5d8ef-175">Parent (..)</span></span>|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5d8ef-176">属性轴 (@)</span><span class="sxs-lookup"><span data-stu-id="5d8ef-176">attribute axis (@)</span></span>|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="5d8ef-177">or</span><span class="sxs-lookup"><span data-stu-id="5d8ef-177">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5d8ef-178">上级轴</span><span class="sxs-lookup"><span data-stu-id="5d8ef-178">ancestor axis</span></span>|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5d8ef-179">上级或自身轴</span><span class="sxs-lookup"><span data-stu-id="5d8ef-179">ancestor-or-self axis</span></span>|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5d8ef-180">后代轴 (//)</span><span class="sxs-lookup"><span data-stu-id="5d8ef-180">descendant axis (//)</span></span>|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="5d8ef-181">或</span><span class="sxs-lookup"><span data-stu-id="5d8ef-181">or</span></span><br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5d8ef-182">后代或自身</span><span class="sxs-lookup"><span data-stu-id="5d8ef-182">descendant-or-self</span></span>|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="5d8ef-183">或</span><span class="sxs-lookup"><span data-stu-id="5d8ef-183">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5d8ef-184">后面同级</span><span class="sxs-lookup"><span data-stu-id="5d8ef-184">following-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="5d8ef-185">或</span><span class="sxs-lookup"><span data-stu-id="5d8ef-185">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5d8ef-186">前面同级</span><span class="sxs-lookup"><span data-stu-id="5d8ef-186">preceding-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="5d8ef-187">or</span><span class="sxs-lookup"><span data-stu-id="5d8ef-187">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5d8ef-188">后面</span><span class="sxs-lookup"><span data-stu-id="5d8ef-188">following</span></span>|<span data-ttu-id="5d8ef-189">无直接等效项。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-189">No direct equivalent.</span></span>|  
|<span data-ttu-id="5d8ef-190">前面</span><span class="sxs-lookup"><span data-stu-id="5d8ef-190">preceding</span></span>|<span data-ttu-id="5d8ef-191">无直接等效项。</span><span class="sxs-lookup"><span data-stu-id="5d8ef-191">No direct equivalent.</span></span>|  
  