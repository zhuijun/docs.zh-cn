---
title: .NET Core 和 .NET Standard 中的单元测试
description: 本文简要概述了 .NET Core 和.NET Standard 项目的单元测试。
author: ardalis
ms.author: wiwagn
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: e15f80b173389cdff86c6e62013e9c0f21171dd6
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703102"
---
# <a name="unit-testing-in-net-core-and-net-standard"></a><span data-ttu-id="252bb-103">.NET Core 和 .NET Standard 中的单元测试</span><span class="sxs-lookup"><span data-stu-id="252bb-103">Unit testing in .NET Core and .NET Standard</span></span>

<span data-ttu-id="252bb-104">通过 .NET Core，可以轻松创建单元测试。</span><span class="sxs-lookup"><span data-stu-id="252bb-104">.NET Core makes it easy to create unit tests.</span></span> <span data-ttu-id="252bb-105">本文介绍了单元测试及其与其他类型的测试的不同之处。</span><span class="sxs-lookup"><span data-stu-id="252bb-105">This article introduces unit tests and illustrates how they differ from other kinds of tests.</span></span> <span data-ttu-id="252bb-106">页面底部附近的链接资源介绍了如何向解决方案添加测试项目。</span><span class="sxs-lookup"><span data-stu-id="252bb-106">The linked resources near the bottom of the page show you how to add a test project to your solution.</span></span> <span data-ttu-id="252bb-107">设置测试项目后，可使用命令行或 Visual Studio 运行单元测试。</span><span class="sxs-lookup"><span data-stu-id="252bb-107">After you set up your test project, you will be able to run your unit tests using the command line or Visual Studio.</span></span>

<span data-ttu-id="252bb-108">如果要测试 ASP.NET Core 项目，请参阅 [ASP.NET Core 中的集成测试](/aspnet/core/test/integration-tests#test-app-prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="252bb-108">If you're testing an **ASP.NET Core** project, see [Integration tests in ASP.NET Core](/aspnet/core/test/integration-tests#test-app-prerequisites).</span></span>

<span data-ttu-id="252bb-109">.NET Core 2.0 及更高版本支持 [.NET Standard 2.0](../../standard/net-standard.md)，我们将使用它的库来演示单元测试。</span><span class="sxs-lookup"><span data-stu-id="252bb-109">.NET Core 2.0 and later supports [.NET Standard 2.0](../../standard/net-standard.md), and we will use its libraries to demonstrate unit tests.</span></span>

<span data-ttu-id="252bb-110">可以使用适用于 C#、F# 和 Visual Basic 的内置 .NET Core 2.0 及更高版本单元测试项目模板作为个人项目的起始点。</span><span class="sxs-lookup"><span data-stu-id="252bb-110">You are able to use built-in .NET Core 2.0 and later unit test project templates for C#, F# and Visual Basic as a starting point for your personal project.</span></span>

## <a name="what-are-unit-tests"></a><span data-ttu-id="252bb-111">什么是单元测试？</span><span class="sxs-lookup"><span data-stu-id="252bb-111">What are unit tests?</span></span>

<span data-ttu-id="252bb-112">使用自动测试是确保软件应用程序按作者期望执行操作的一种绝佳方式。</span><span class="sxs-lookup"><span data-stu-id="252bb-112">Having automated tests is a great way to ensure a software application does what its authors intend it to do.</span></span> <span data-ttu-id="252bb-113">软件应用程序有多种类型的测试。</span><span class="sxs-lookup"><span data-stu-id="252bb-113">There are multiple types of tests for software applications.</span></span> <span data-ttu-id="252bb-114">其中包括集成测试、Web 测试、负载测试和其他测试。</span><span class="sxs-lookup"><span data-stu-id="252bb-114">These include integration tests, web tests, load tests, and others.</span></span> <span data-ttu-id="252bb-115">“单元测试”用于测试个人软件组件或方法。</span><span class="sxs-lookup"><span data-stu-id="252bb-115">**Unit tests** test individual software components and methods.</span></span> <span data-ttu-id="252bb-116">单元测试仅应测试开发人员控件内的代码。</span><span class="sxs-lookup"><span data-stu-id="252bb-116">Unit tests should only test code within the developer’s control.</span></span> <span data-ttu-id="252bb-117">它们不应测试基础结构问题。</span><span class="sxs-lookup"><span data-stu-id="252bb-117">They should not test infrastructure concerns.</span></span> <span data-ttu-id="252bb-118">基础结构问题包括数据库、文件系统和网络资源。</span><span class="sxs-lookup"><span data-stu-id="252bb-118">Infrastructure concerns include databases, file systems, and network resources.</span></span>

<span data-ttu-id="252bb-119">此外，请记住还可使用编写测试的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="252bb-119">Also, keep in mind there are best practices for writing tests.</span></span> <span data-ttu-id="252bb-120">例如，[测试驱动开发 (TDD)](https://deviq.com/test-driven-development/) 是指先编写单元测试，再编写该单元测试要检查的代码。</span><span class="sxs-lookup"><span data-stu-id="252bb-120">For example, [Test Driven Development (TDD)](https://deviq.com/test-driven-development/) is when a unit test is written before the code it is meant to check.</span></span> <span data-ttu-id="252bb-121">TDD 就像先编写书籍大纲，再编写该书籍。</span><span class="sxs-lookup"><span data-stu-id="252bb-121">TDD is like creating an outline for a book before we write it.</span></span> <span data-ttu-id="252bb-122">它旨在帮助开发人员编写更简单、更具可读性的高效代码。</span><span class="sxs-lookup"><span data-stu-id="252bb-122">It is meant to help developers write simpler, more readable, and efficient code.</span></span>

> [!NOTE]
> <span data-ttu-id="252bb-123">ASP.NET 团队遵循[这些约定](https://github.com/dotnet/aspnetcore/wiki/Engineering-guidelines#unit-tests-and-functional-tests)帮助开发人员为测试类和方法提供合适的名称。</span><span class="sxs-lookup"><span data-stu-id="252bb-123">The ASP.NET team follows [these conventions](https://github.com/dotnet/aspnetcore/wiki/Engineering-guidelines#unit-tests-and-functional-tests) to help developers come up with good names for test classes and methods.</span></span>

<span data-ttu-id="252bb-124">编写单元测试时，尽量不要引入基础结构依赖项。</span><span class="sxs-lookup"><span data-stu-id="252bb-124">Try not to introduce dependencies on infrastructure when writing unit tests.</span></span> <span data-ttu-id="252bb-125">这些依赖项会降低测试速度，使测试更加脆弱，应将其保留供集成测试使用。</span><span class="sxs-lookup"><span data-stu-id="252bb-125">These make the tests slow and brittle, and should be reserved for integration tests.</span></span> <span data-ttu-id="252bb-126">可以通过遵循 [Explicit Dependencies Principle](https://deviq.com/explicit-dependencies-principle/)（显式依赖项原则）和使用 [Dependency Injection](/aspnet/core/fundamentals/dependency-injection)（依赖项注入）避免应用程序中的这些依赖项。</span><span class="sxs-lookup"><span data-stu-id="252bb-126">You can avoid these dependencies in your application by following the [Explicit Dependencies Principle](https://deviq.com/explicit-dependencies-principle/) and using [Dependency Injection](/aspnet/core/fundamentals/dependency-injection).</span></span> <span data-ttu-id="252bb-127">还可以将单元测试保留在单独的项目中，与集成测试相分隔。</span><span class="sxs-lookup"><span data-stu-id="252bb-127">You can also keep your unit tests in a separate project from your integration tests.</span></span> <span data-ttu-id="252bb-128">这可确保单元测试项目没有引用或依赖于基础结构包。</span><span class="sxs-lookup"><span data-stu-id="252bb-128">This ensures your unit test project doesn’t have references to or dependencies on infrastructure packages.</span></span>

## <a name="next-steps"></a><span data-ttu-id="252bb-129">后续步骤</span><span class="sxs-lookup"><span data-stu-id="252bb-129">Next steps</span></span>

<span data-ttu-id="252bb-130">有关 .NET Core 项目中的单元测试的详细信息：</span><span class="sxs-lookup"><span data-stu-id="252bb-130">More information on unit testing in .NET Core projects:</span></span>

<span data-ttu-id="252bb-131">.NET Core 单元测试项目支持：</span><span class="sxs-lookup"><span data-stu-id="252bb-131">.NET Core unit test projects are supported for:</span></span>

- [<span data-ttu-id="252bb-132">C#</span><span class="sxs-lookup"><span data-stu-id="252bb-132">C#</span></span>](../../csharp/index.yml)
- [<span data-ttu-id="252bb-133">F#</span><span class="sxs-lookup"><span data-stu-id="252bb-133">F#</span></span>](../../fsharp/index.yml)
- [<span data-ttu-id="252bb-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="252bb-134">Visual Basic</span></span>](../../visual-basic/index.yml)

<span data-ttu-id="252bb-135">还可在多个单元测试框架之间进行选择：</span><span class="sxs-lookup"><span data-stu-id="252bb-135">You can also choose between several unit test frameworks:</span></span>

- [<span data-ttu-id="252bb-136">xUnit</span><span class="sxs-lookup"><span data-stu-id="252bb-136">xUnit</span></span>](https://xunit.net/)
- [<span data-ttu-id="252bb-137">NUnit</span><span class="sxs-lookup"><span data-stu-id="252bb-137">NUnit</span></span>](https://nunit.org)
- [<span data-ttu-id="252bb-138">MSTest</span><span class="sxs-lookup"><span data-stu-id="252bb-138">MSTest</span></span>](https://github.com/Microsoft/testfx-docs)

<span data-ttu-id="252bb-139">可在以下演练中了解详细信息：</span><span class="sxs-lookup"><span data-stu-id="252bb-139">You can learn more in the following walkthroughs:</span></span>

:::zone pivot="mstest"

- <span data-ttu-id="252bb-140">[结合使用 .NET Core CLI 与 MSTest 和 C#](unit-testing-with-mstest.md) 创建单元测试。</span><span class="sxs-lookup"><span data-stu-id="252bb-140">Create unit tests using [*MSTest* and *C#* with the .NET Core CLI](unit-testing-with-mstest.md).</span></span>
- <span data-ttu-id="252bb-141">[结合使用 .NET Core CLI 与 MSTest 和 F#](unit-testing-fsharp-with-mstest.md) 创建单元测试。</span><span class="sxs-lookup"><span data-stu-id="252bb-141">Create unit tests using [*MSTest* and *F#* with the .NET Core CLI](unit-testing-fsharp-with-mstest.md).</span></span>
- <span data-ttu-id="252bb-142">[结合使用 .NET Core CLI 与 MSTest 和 Visual Basic](unit-testing-visual-basic-with-mstest.md) 创建单元测试。</span><span class="sxs-lookup"><span data-stu-id="252bb-142">Create unit tests using [*MSTest* and *Visual Basic* with the .NET Core CLI](unit-testing-visual-basic-with-mstest.md).</span></span>

:::zone-end
:::zone pivot="xunit"

- <span data-ttu-id="252bb-143">[结合使用 .NET Core CLI 与 xUnit 和 C#](unit-testing-with-dotnet-test.md) 创建单元测试。</span><span class="sxs-lookup"><span data-stu-id="252bb-143">Create unit tests using [*xUnit* and *C#* with the .NET Core CLI](unit-testing-with-dotnet-test.md).</span></span>
- <span data-ttu-id="252bb-144">[结合使用 .NET Core CLI 与 xUnit 和 F#](unit-testing-fsharp-with-dotnet-test.md) 创建单元测试。</span><span class="sxs-lookup"><span data-stu-id="252bb-144">Create unit tests using [*xUnit* and *F#* with the .NET Core CLI](unit-testing-fsharp-with-dotnet-test.md).</span></span>
- <span data-ttu-id="252bb-145">[结合使用 .NET Core CLI 与 xUnit 和 Visual Basic](unit-testing-visual-basic-with-dotnet-test.md) 创建单元测试。</span><span class="sxs-lookup"><span data-stu-id="252bb-145">Create unit tests using [*xUnit* and *Visual Basic* with the .NET Core CLI](unit-testing-visual-basic-with-dotnet-test.md).</span></span>

:::zone-end
:::zone pivot="nunit"

- <span data-ttu-id="252bb-146">[结合使用 .NET Core CLI 与 NUnit 和 C#](unit-testing-with-nunit.md) 创建单元测试 。</span><span class="sxs-lookup"><span data-stu-id="252bb-146">Create unit tests using [*NUnit* and *C#* with the .NET Core CLI](unit-testing-with-nunit.md).</span></span>
- <span data-ttu-id="252bb-147">[结合使用 .NET Core CLI 与 NUnit 和 F#](unit-testing-fsharp-with-nunit.md) 创建单元测试 。</span><span class="sxs-lookup"><span data-stu-id="252bb-147">Create unit tests using [*NUnit* and *F#* with the .NET Core CLI](unit-testing-fsharp-with-nunit.md).</span></span>
- <span data-ttu-id="252bb-148">[结合使用 .NET Core CLI 与 NUnit 和 Visual Basic](unit-testing-visual-basic-with-nunit.md) 创建单元测试 。</span><span class="sxs-lookup"><span data-stu-id="252bb-148">Create unit tests using [*NUnit* and *Visual Basic* with the .NET Core CLI](unit-testing-visual-basic-with-nunit.md).</span></span>

:::zone-end

<span data-ttu-id="252bb-149">可在以下文章中了解详细信息：</span><span class="sxs-lookup"><span data-stu-id="252bb-149">You can learn more in the following articles:</span></span>

- <span data-ttu-id="252bb-150">Visual Studio Enterprise 提供用于 .NET Core 的卓越测试工具。</span><span class="sxs-lookup"><span data-stu-id="252bb-150">Visual Studio Enterprise offers great testing tools for .NET Core.</span></span> <span data-ttu-id="252bb-151">有关详细信息，请查看 [Live Unit Testing](/visualstudio/test/live-unit-testing) 或[代码覆盖率](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage)。</span><span class="sxs-lookup"><span data-stu-id="252bb-151">Check out [Live Unit Testing](/visualstudio/test/live-unit-testing) or [code coverage](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage) to learn more.</span></span>
- <span data-ttu-id="252bb-152">有关如何运行选择性单元测试的详细信息，请参阅[运行选择性单元测试](selective-unit-tests.md)或[使用 Visual Studio 添加和排除测试](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods)。</span><span class="sxs-lookup"><span data-stu-id="252bb-152">For more information on how to run selective unit tests, see [Running selective unit tests](selective-unit-tests.md), or [including and excluding tests with Visual Studio](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods).</span></span>
- <span data-ttu-id="252bb-153">[如何通过 .NET Core 和 Visual Studio 使用 xUnit](https://xunit.github.io/docs/getting-started-dotnet-core.html)。</span><span class="sxs-lookup"><span data-stu-id="252bb-153">[How to use xUnit with .NET Core and Visual Studio](https://xunit.github.io/docs/getting-started-dotnet-core.html).</span></span>
