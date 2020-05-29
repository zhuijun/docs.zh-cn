---
title: 运行选择性单元测试
description: 如何使用筛选表达式通过 .NET Core 中的 dotnet 测试命令运行选择性单元测试。
author: smadala
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: 6a6bbb0687742d1e3288d64fb88f6825dc678e28
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702989"
---
# <a name="run-selective-unit-tests"></a><span data-ttu-id="eaa7b-103">运行选择性单元测试</span><span class="sxs-lookup"><span data-stu-id="eaa7b-103">Run selective unit tests</span></span>

<span data-ttu-id="eaa7b-104">借助 .NET Core 中的 [`dotnet test`](../tools/dotnet-test.md) 命令，可以使用筛选表达式来运行选择性测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-104">With the [`dotnet test`](../tools/dotnet-test.md) command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="eaa7b-105">本文演示如何筛选运行哪些测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-105">This article demonstrates how to filter which tests are run.</span></span> <span data-ttu-id="eaa7b-106">下面的示例使用 `dotnet test`。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="eaa7b-107">如果使用的是 `vstest.console.exe`，请将 `--filter` 替换成 `--testcasefilter:`。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

## <a name="character-escaping"></a><span data-ttu-id="eaa7b-108">字符转义</span><span class="sxs-lookup"><span data-stu-id="eaa7b-108">Character escaping</span></span>

<span data-ttu-id="eaa7b-109">在 `*nix` 上使用包含感叹号 `!` 的筛选器需要转义，因为保留了 `!`。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-109">Using filters that include exclamation mark `!` on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="eaa7b-110">例如，如果命名空间包含 IntegrationTests，则此筛选器将跳过所有测试：</span><span class="sxs-lookup"><span data-stu-id="eaa7b-110">For example, this filter skips all tests if the namespace contains IntegrationTests:</span></span>

```dotnetcli
dotnet test --filter FullyQualifiedName\!~IntegrationTests
```

> [!IMPORTANT]
> <span data-ttu-id="eaa7b-111">反斜杠位于感叹号之前，表示它是转义字符 `\!`。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-111">The backslash precedes the exclamation mark to indicate it is an escaped character `\!`.</span></span>

<span data-ttu-id="eaa7b-112">对于包含泛型类型参数的逗号的 `FullyQualifiedName` 值，请使用 `%2C` 来转义逗号。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-112">For `FullyQualifiedName` values that include a comma for generic type parameters, escape the comma with `%2C`.</span></span> <span data-ttu-id="eaa7b-113">例如：</span><span class="sxs-lookup"><span data-stu-id="eaa7b-113">For example:</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

:::zone pivot="mstest"

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace MSTestNamespace
{
    [TestClass]
    public class UnitTest1
    {
        [TestMethod, Priority(1), TestCategory("CategoryA")]
        public void TestMethod1()
        {
        }

        [TestMethod, Priority(2)]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="eaa7b-114">表达式</span><span class="sxs-lookup"><span data-stu-id="eaa7b-114">Expression</span></span> | <span data-ttu-id="eaa7b-115">结果</span><span class="sxs-lookup"><span data-stu-id="eaa7b-115">Result</span></span> |
|--|--|
| `dotnet test --filter Method` | <span data-ttu-id="eaa7b-116">运行 <xref:System.Reflection.Module.FullyQualifiedName> 包含 `Method` 的测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-116">Runs tests whose <xref:System.Reflection.Module.FullyQualifiedName> contains `Method`.</span></span> <span data-ttu-id="eaa7b-117">在 `vstest 15.1+` 中可用。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-117">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="eaa7b-118">运行名称包含 `TestMethod1` 的测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-118">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="eaa7b-119">运行属于类 `MSTestNamespace.UnitTest1` 的测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-119">Runs tests that are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="eaa7b-120">**注意：** 由于 `ClassName` 值应有命名空间，因此 `ClassName=UnitTest1` 无效。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-120">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="eaa7b-121">运行除 `MSTestNamespace.UnitTest1.TestMethod1` 之外的其他所有测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-121">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="eaa7b-122">运行含 `[TestCategory("CategoryA")]` 批注的测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-122">Runs tests that are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="eaa7b-123">运行含 `[Priority(2)]` 批注的测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-123">Runs tests that are annotated with `[Priority(2)]`.</span></span> |

<span data-ttu-id="eaa7b-124">使用条件运算符 `|` 和 `&` 的示例：</span><span class="sxs-lookup"><span data-stu-id="eaa7b-124">Examples using the conditional operators `|` and `&`:</span></span>

<span data-ttu-id="eaa7b-125">运行 <xref:System.Reflection.Module.FullyQualifiedName> 中包含 `UnitTest1` 或 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> 为 `"CategoryA"` 的测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-125">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **or** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> is `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

<span data-ttu-id="eaa7b-126">运行 <xref:System.Reflection.Module.FullyQualifiedName> 中包含 `UnitTest1` 且 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> 为 `"CategoryA"` 的测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-126">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **and** have a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

<span data-ttu-id="eaa7b-127">运行 <xref:System.Reflection.Module.FullyQualifiedName> 中包含 `UnitTest1` 且 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> 为 `"CategoryA"` 或 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute> 的优先级为 `1` 的测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-127">To run tests that have either <xref:System.Reflection.Module.FullyQualifiedName> containing `UnitTest1` **and** have a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> of `"CategoryA"` **or** have a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute> with a priority of `1`.</span></span>

```dotnetcli
dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)|Priority=1"
```

:::zone-end
:::zone pivot="xunit"

```csharp
using Xunit;

namespace XUnitNamespace
{
    public class TestClass1
    {
        [Fact, Trait("Priority", "1"), Trait("Category", "CategoryA")]
        public void Test1()
        {
        }

        [Fact, Trait("Priority", "2")]
        public void Test2()
        {
        }
    }
}
```

| <span data-ttu-id="eaa7b-128">表达式</span><span class="sxs-lookup"><span data-stu-id="eaa7b-128">Expression</span></span> | <span data-ttu-id="eaa7b-129">结果</span><span class="sxs-lookup"><span data-stu-id="eaa7b-129">Result</span></span> |
|--|--|
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="eaa7b-130">仅运行一个测试，即 `XUnitNamespace.TestClass1.Test1`。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-130">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="eaa7b-131">运行除 `XUnitNamespace.TestClass1.Test1` 之外的其他所有测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-131">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="eaa7b-132">运行显示名称包含 `TestClass1` 的测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-132">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="eaa7b-133">在代码示例中，包含键 `"Category"` 和 `"Priority"` 的已定义特征可用于筛选。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-133">In the code example, the defined traits with keys `"Category"` and `"Priority"` can be used for filtering.</span></span>

| <span data-ttu-id="eaa7b-134">表达式</span><span class="sxs-lookup"><span data-stu-id="eaa7b-134">Expression</span></span> | <span data-ttu-id="eaa7b-135">结果</span><span class="sxs-lookup"><span data-stu-id="eaa7b-135">Result</span></span> |
|--|--|
| `dotnet test --filter XUnit` | <span data-ttu-id="eaa7b-136">运行 <xref:System.Reflection.Module.FullyQualifiedName> 包含 `XUnit` 的测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-136">Runs tests whose <xref:System.Reflection.Module.FullyQualifiedName> contains `XUnit`.</span></span>  <span data-ttu-id="eaa7b-137">在 `vstest 15.1+` 中可用。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-137">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="eaa7b-138">运行包含 `[Trait("Category", "CategoryA")]` 的测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-138">Runs tests that have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="eaa7b-139">使用条件运算符 `|` 和 `&` 的示例：</span><span class="sxs-lookup"><span data-stu-id="eaa7b-139">Examples using the conditional operators `|` and `&`:</span></span>

<span data-ttu-id="eaa7b-140">运行 <xref:System.Reflection.Module.FullyQualifiedName> 中包含 `TestClass1` 或 `Trait` 的键为 `"Category"` 且值为 `"CategoryA"` 的测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-140">To run tests that have `TestClass1` in their <xref:System.Reflection.Module.FullyQualifiedName> **or** have a `Trait` with a key of `"Category"` and value of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1|Category=CategoryA"
```

<span data-ttu-id="eaa7b-141">运行 <xref:System.Reflection.Module.FullyQualifiedName> 中包含 `TestClass1` 且 `Trait` 的键为 `"Category"` 且值为 `"CategoryA"` 的测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-141">To run tests that have `TestClass1` in their <xref:System.Reflection.Module.FullyQualifiedName> **and** have a `Trait` with a key of `"Category"` and value of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"
```

<span data-ttu-id="eaa7b-142">运行 <xref:System.Reflection.Module.FullyQualifiedName> 中包含 `TestClass1` 且 `Trait` 的键为 `"Category"` 且值为 `"CategoryA"` 或 `Trait` 的键为 `"Priority"` 且值为 `1` 的测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-142">To run tests that have either <xref:System.Reflection.Module.FullyQualifiedName> containing `TestClass1` **and** have a `Trait` with a key of `"Category"` and value of `"CategoryA"` **or** have a `Trait` with a key of `"Priority"` and value of `1`.</span></span>

```dotnetcli
dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)|Priority=1"
```

:::zone-end
:::zone pivot="nunit"

```csharp
using NUnit.Framework;

namespace NUnitNamespace
{
    public class UnitTest1
    {
        [Test, Property("Priority", 1), Category("CategoryA")]
        public void TestMethod1()
        {
        }

        [Test, Property("Priority", 2)]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="eaa7b-143">表达式</span><span class="sxs-lookup"><span data-stu-id="eaa7b-143">Expression</span></span> | <span data-ttu-id="eaa7b-144">结果</span><span class="sxs-lookup"><span data-stu-id="eaa7b-144">Result</span></span> |
|--|--|
| `dotnet test --filter Method` | <span data-ttu-id="eaa7b-145">运行 <xref:System.Reflection.Module.FullyQualifiedName> 包含 `Method` 的测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-145">Runs tests whose <xref:System.Reflection.Module.FullyQualifiedName> contains `Method`.</span></span> <span data-ttu-id="eaa7b-146">在 `vstest 15.1+` 中可用。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-146">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="eaa7b-147">运行名称包含 `TestMethod1` 的测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-147">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="eaa7b-148">运行属于类 `NUnitNamespace.UnitTest1` 的测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-148">Runs tests that are in class `NUnitNamespace.UnitTest1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="eaa7b-149">运行除 `NUnitNamespace.UnitTest1.TestMethod1` 之外的其他所有测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-149">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="eaa7b-150">运行含 `[Category("CategoryA")]` 批注的测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-150">Runs tests that are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="eaa7b-151">运行含 `[Priority(2)]` 批注的测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-151">Runs tests that are annotated with `[Priority(2)]`.</span></span> |

<span data-ttu-id="eaa7b-152">使用条件运算符 `|` 和 `&` 的示例：</span><span class="sxs-lookup"><span data-stu-id="eaa7b-152">Examples using the conditional operators `|` and `&`:</span></span>

<span data-ttu-id="eaa7b-153">运行 <xref:System.Reflection.Module.FullyQualifiedName> 中包含 `UnitTest1` 或 `Category` 为 `"CategoryA"` 的测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-153">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **or** have a `Category` of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

<span data-ttu-id="eaa7b-154">运行 <xref:System.Reflection.Module.FullyQualifiedName> 中包含 `UnitTest1` 且 `Category` 为 `"CategoryA"` 的测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-154">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **and** have a `Category` of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

<span data-ttu-id="eaa7b-155">运行 <xref:System.Reflection.Module.FullyQualifiedName> 中包含 `UnitTest1` 且 `Category` 为 `"CategoryA"` 或 `Property` 的 `"Priority"` 为 `1` 的测试。</span><span class="sxs-lookup"><span data-stu-id="eaa7b-155">To run tests that have either a <xref:System.Reflection.Module.FullyQualifiedName> containing `UnitTest1` **and** have a `Category` of `"CategoryA"` **or** have a `Property` with a `"Priority"` of `1`.</span></span>

```dotnetcli
dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)|Priority=1"
```

<span data-ttu-id="eaa7b-156">有关详细信息，请参阅 [TestCase 筛选器](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md)</span><span class="sxs-lookup"><span data-stu-id="eaa7b-156">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>

:::zone-end

## <a name="see-also"></a><span data-ttu-id="eaa7b-157">请参阅</span><span class="sxs-lookup"><span data-stu-id="eaa7b-157">See also</span></span>

- [<span data-ttu-id="eaa7b-158">dotnet test</span><span class="sxs-lookup"><span data-stu-id="eaa7b-158">dotnet test</span></span>](../tools/dotnet-test.md)
- [<span data-ttu-id="eaa7b-159">dotnet test -- 筛选器</span><span class="sxs-lookup"><span data-stu-id="eaa7b-159">dotnet test --filter</span></span>](../tools/dotnet-test.md#filter-option-details)

## <a name="next-steps"></a><span data-ttu-id="eaa7b-160">后续步骤</span><span class="sxs-lookup"><span data-stu-id="eaa7b-160">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="eaa7b-161">对单元测试排序</span><span class="sxs-lookup"><span data-stu-id="eaa7b-161">Order unit tests</span></span>](order-unit-tests.md)
