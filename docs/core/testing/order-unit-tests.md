---
title: 对单元测试排序
description: 了解如何通过 .NET Core 对单元测试排序。
author: IEvangelist
ms.author: dapine
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: eb426b790e0623b0cf233a763e93d2bd501b8034
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100816"
---
# <a name="order-unit-tests"></a><span data-ttu-id="eb3d5-103">对单元测试排序</span><span class="sxs-lookup"><span data-stu-id="eb3d5-103">Order unit tests</span></span>

<span data-ttu-id="eb3d5-104">有时，你可能希望按特定顺序运行单元测试。</span><span class="sxs-lookup"><span data-stu-id="eb3d5-104">Occasionally, you may want to have unit tests run in a specific order.</span></span> <span data-ttu-id="eb3d5-105">理想情况下，单元测试的运行顺序__ 不重要，[最佳做法](unit-testing-best-practices.md)是避免对单元测试排序。</span><span class="sxs-lookup"><span data-stu-id="eb3d5-105">Ideally, the order in which unit tests run should _not_ matter, and it is [best practice](unit-testing-best-practices.md) to avoid ordering unit tests.</span></span> <span data-ttu-id="eb3d5-106">但无论如何，可能会有需要这样做。</span><span class="sxs-lookup"><span data-stu-id="eb3d5-106">Regardless, there may be a need to do so.</span></span> <span data-ttu-id="eb3d5-107">为此，本文将演示如何对测试运行进行排序。</span><span class="sxs-lookup"><span data-stu-id="eb3d5-107">In that case, this article demonstrates how to order test runs.</span></span>

<span data-ttu-id="eb3d5-108">如果你更喜欢浏览源代码，请参阅[对 .NET Core 单元测试排序](/samples/dotnet/samples/order-unit-tests-cs)示例存储库。</span><span class="sxs-lookup"><span data-stu-id="eb3d5-108">If you prefer to browse the source code, see the [order .NET Core unit tests](/samples/dotnet/samples/order-unit-tests-cs) sample repository.</span></span>

> [!TIP]
> <span data-ttu-id="eb3d5-109">除了本文中所述的排序功能，还应考虑将[使用 Visual Studio 创建自定义播放列表](/visualstudio/test/run-unit-tests-with-test-explorer?view=vs-2019#create-custom-playlists)作为替代方法。</span><span class="sxs-lookup"><span data-stu-id="eb3d5-109">In addition to the ordering capabilities outlined in this article, consider [creating custom playlists with Visual Studio](/visualstudio/test/run-unit-tests-with-test-explorer?view=vs-2019#create-custom-playlists) as an alternative.</span></span>

:::zone pivot="mstest"

## <a name="order-alphabetically"></a><span data-ttu-id="eb3d5-110">按字母顺序排序</span><span class="sxs-lookup"><span data-stu-id="eb3d5-110">Order alphabetically</span></span>

<span data-ttu-id="eb3d5-111">使用 MSTest，测试将按其测试名称自动排序。</span><span class="sxs-lookup"><span data-stu-id="eb3d5-111">With MSTest, tests are automatically ordered by their test name.</span></span>

> [!NOTE]
> <span data-ttu-id="eb3d5-112">名为 `Test14` 的测试将在 `Test2` 之前运行，即使数字 `2` 小于 `14` 也是如此。</span><span class="sxs-lookup"><span data-stu-id="eb3d5-112">A test named `Test14` will run before `Test2` even though the number  `2` is less than `14`.</span></span> <span data-ttu-id="eb3d5-113">这是因为，测试名称排序使用的是测试的文本名称。</span><span class="sxs-lookup"><span data-stu-id="eb3d5-113">This is because, test name ordering uses the text name of the test.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/MSTest.Project/ByAlphabeticalOrder.cs":::

:::zone-end
:::zone pivot="xunit"

<span data-ttu-id="eb3d5-114">xUnit 测试框架允许对测试运行顺序进行更细致的控制。</span><span class="sxs-lookup"><span data-stu-id="eb3d5-114">The xUnit test framework allows for more granularity and control of test run order.</span></span> <span data-ttu-id="eb3d5-115">可以实现 `ITestCaseOrderer` 和 `ITestCollectionOrderer` 接口，以控制类或测试集合的测试用例的顺序。</span><span class="sxs-lookup"><span data-stu-id="eb3d5-115">You implement the `ITestCaseOrderer` and `ITestCollectionOrderer` interfaces to control the order of test cases for a class, or test collections.</span></span>

## <a name="order-by-test-case-alphabetically"></a><span data-ttu-id="eb3d5-116">按测试用例的字母顺序排序</span><span class="sxs-lookup"><span data-stu-id="eb3d5-116">Order by test case alphabetically</span></span>

<span data-ttu-id="eb3d5-117">若要按其方法名称对测试用例排序，可以实现 `ITestCaseOrderer` 并提供排序机制。</span><span class="sxs-lookup"><span data-stu-id="eb3d5-117">To order test cases by their method name, you implement the `ITestCaseOrderer` and provide an ordering mechanism.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/AlphabeticalOrderer.cs":::

<span data-ttu-id="eb3d5-118">然后，在测试类中，使用 `TestCaseOrdererAttribute` 设置测试用例的顺序。</span><span class="sxs-lookup"><span data-stu-id="eb3d5-118">Then in a test class you set the test case order with the `TestCaseOrdererAttribute`.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByAlphabeticalOrder.cs":::

## <a name="order-by-collection-alphabetically"></a><span data-ttu-id="eb3d5-119">按集合的字母顺序排序</span><span class="sxs-lookup"><span data-stu-id="eb3d5-119">Order by collection alphabetically</span></span>

<span data-ttu-id="eb3d5-120">若要按其显示名称对测试集合排序，可以实现 `ITestCollectionOrderer` 并提供排序机制。</span><span class="sxs-lookup"><span data-stu-id="eb3d5-120">To order test collections by their display name, you implement the `ITestCollectionOrderer` and provide an ordering mechanism.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/DisplayNameOrderer.cs":::

<span data-ttu-id="eb3d5-121">由于测试集合可能会并行运行，因此必须使用 `CollectionBehaviorAttribute` 显式禁用集合的测试并行化。</span><span class="sxs-lookup"><span data-stu-id="eb3d5-121">Since test collections potentially run in parallel, you must explicitly disable test parallelization of the collections with the `CollectionBehaviorAttribute`.</span></span> <span data-ttu-id="eb3d5-122">然后，将实现指定到 `TestCollectionOrdererAttribute`。</span><span class="sxs-lookup"><span data-stu-id="eb3d5-122">Then specify the implementation to the `TestCollectionOrdererAttribute`.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByDisplayName.cs":::

## <a name="order-by-custom-attribute"></a><span data-ttu-id="eb3d5-123">按自定义属性排序</span><span class="sxs-lookup"><span data-stu-id="eb3d5-123">Order by custom attribute</span></span>

<span data-ttu-id="eb3d5-124">若要使用自定义属性对 xUnit 测试排序，首先需要一个要依赖的属性。</span><span class="sxs-lookup"><span data-stu-id="eb3d5-124">To order xUnit tests with custom attributes, you first need an attribute to rely on.</span></span> <span data-ttu-id="eb3d5-125">按如下所示定义 `TestPriorityAttribute`：</span><span class="sxs-lookup"><span data-stu-id="eb3d5-125">Define a `TestPriorityAttribute` as follows:</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Attributes/TestPriorityAttribute.cs":::

<span data-ttu-id="eb3d5-126">接下来，请考虑 `ITestCaseOrderer` 接口的以下 `PriorityOrderer` 实现。</span><span class="sxs-lookup"><span data-stu-id="eb3d5-126">Next, consider the following `PriorityOrderer` implementation of the `ITestCaseOrderer` interface.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/PriorityOrderer.cs":::

<span data-ttu-id="eb3d5-127">然后，在测试类中，使用 `TestCaseOrdererAttribute` 将测试用例的顺序设置为 `PriorityOrderer`。</span><span class="sxs-lookup"><span data-stu-id="eb3d5-127">Then in a test class you set the test case order with the `TestCaseOrdererAttribute` to the `PriorityOrderer`.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByPriorityOrder.cs":::

:::zone-end
:::zone pivot="nunit"

## <a name="order-by-priority"></a><span data-ttu-id="eb3d5-128">按优先级排序</span><span class="sxs-lookup"><span data-stu-id="eb3d5-128">Order by priority</span></span>

<span data-ttu-id="eb3d5-129">为了显式对测试排序，NUnit 提供了 [`OrderAttribute`](https://github.com/nunit/docs/wiki/Order-Attribute)。</span><span class="sxs-lookup"><span data-stu-id="eb3d5-129">To order tests explicitly, NUnit provides an [`OrderAttribute`](https://github.com/nunit/docs/wiki/Order-Attribute).</span></span> <span data-ttu-id="eb3d5-130">具有此属性的测试先于没有此属性的测试启动。</span><span class="sxs-lookup"><span data-stu-id="eb3d5-130">Tests with this attribute are started before tests without.</span></span> <span data-ttu-id="eb3d5-131">顺序值用于确定运行单元测试的顺序。</span><span class="sxs-lookup"><span data-stu-id="eb3d5-131">The order value is used to determined the order to run the unit tests.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/NUnit.TestProject/ByOrder.cs":::

:::zone-end

## <a name="next-steps"></a><span data-ttu-id="eb3d5-132">后续步骤</span><span class="sxs-lookup"><span data-stu-id="eb3d5-132">Next Steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="eb3d5-133">单元测试代码覆盖率</span><span class="sxs-lookup"><span data-stu-id="eb3d5-133">Unit test code coverage</span></span>](unit-testing-code-coverage.md)
