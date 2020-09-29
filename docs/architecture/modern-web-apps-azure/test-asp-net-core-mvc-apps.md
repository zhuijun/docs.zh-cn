---
title: 测试 ASP.NET Core MVC 应用
description: 使用 ASP.NET Core 和 Azure 构建新式 Web 应用程序 | 测试 ASP.NET Core MVC 应用
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: ca86388b9f5dfe5e63ead1b5f84486ba2181af57
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169071"
---
# <a name="test-aspnet-core-mvc-apps"></a><span data-ttu-id="2c7b1-103">测试 ASP.NET Core MVC 应用</span><span class="sxs-lookup"><span data-stu-id="2c7b1-103">Test ASP.NET Core MVC apps</span></span>

> <span data-ttu-id="2c7b1-104">“如果你不喜欢对产品进行单元测试，很可能你的客户也不喜欢这样做。” </span><span class="sxs-lookup"><span data-stu-id="2c7b1-104">*"If you don't like unit testing your product, most likely your customers won't like to test it, either."*</span></span>
 > <span data-ttu-id="2c7b1-105">\_- 匿名-</span><span class="sxs-lookup"><span data-stu-id="2c7b1-105">\_- Anonymous-</span></span>

<span data-ttu-id="2c7b1-106">任何复杂程度的软件在响应更改方面皆可能意外失败。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-106">Software of any complexity can fail in unexpected ways in response to changes.</span></span> <span data-ttu-id="2c7b1-107">因此，更改后，除最普通（或关键性最低）的应用程序外，其他所有应用程序均需测试。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-107">Thus, testing after making changes is required for all but the most trivial (or least critical) applications.</span></span> <span data-ttu-id="2c7b1-108">手动测试是最慢、最不可靠且最昂贵的软件测试方式。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-108">Manual testing is the slowest, least reliable, most expensive way to test software.</span></span> <span data-ttu-id="2c7b1-109">遗憾的是，如果应用程序在设计上不具备可测试性，这可能是唯一可用的方式。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-109">Unfortunately, if applications aren't designed to be testable, it can be the only means available.</span></span> <span data-ttu-id="2c7b1-110">为了遵循[第 4 章](architectural-principles.md)中列出的体系结构原则而编写的应用程序应为单元可测试的。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-110">Applications written to follow the architectural principles laid out in [chapter 4](architectural-principles.md) should be unit testable.</span></span> <span data-ttu-id="2c7b1-111">ASP.NET Core 应用程序支持自动集成和功能测试。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-111">ASP.NET Core applications support automated integration and functional testing.</span></span>

## <a name="kinds-of-automated-tests"></a><span data-ttu-id="2c7b1-112">自动测试类型</span><span class="sxs-lookup"><span data-stu-id="2c7b1-112">Kinds of automated tests</span></span>

<span data-ttu-id="2c7b1-113">软件应用程序自动测试具有多种类型。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-113">There are many kinds of automated tests for software applications.</span></span> <span data-ttu-id="2c7b1-114">最简单最低级别的测试是单元测试。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-114">The simplest, lowest level test is the unit test.</span></span> <span data-ttu-id="2c7b1-115">级别稍高的测试包括集成测试和功能测试。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-115">At a slightly higher level, there are integration tests and functional tests.</span></span> <span data-ttu-id="2c7b1-116">其他类型的测试不在本文讨论范围之内，例如 UI 测试、负载测试、压力测试和版本验收测试。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-116">Other kinds of tests, such as UI tests, load tests, stress tests, and smoke tests, are beyond the scope of this document.</span></span>

### <a name="unit-tests"></a><span data-ttu-id="2c7b1-117">单元测试</span><span class="sxs-lookup"><span data-stu-id="2c7b1-117">Unit tests</span></span>

<span data-ttu-id="2c7b1-118">单元测试可测试应用程序逻辑的单个部分。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-118">A unit test tests a single part of your application's logic.</span></span> <span data-ttu-id="2c7b1-119">可通过否定列举方式对其进行进一步描述。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-119">One can further describe it by listing some of the things that it isn't.</span></span> <span data-ttu-id="2c7b1-120">单元测试并不测试代码如何处理依赖项或基础结构 - 这是集成测试的用途。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-120">A unit test doesn't test how your code works with dependencies or infrastructure – that's what integration tests are for.</span></span> <span data-ttu-id="2c7b1-121">单元测试不测试编写代码所用的框架，你应假定其适用，如果不适用，请报告 bug 并编写代码解决。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-121">A unit test doesn't test the framework your code is written on – you should assume it works or, if you find it doesn't, file a bug and code a workaround.</span></span> <span data-ttu-id="2c7b1-122">单元测试完全在内存或进程中运行。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-122">A unit test runs completely in memory and in process.</span></span> <span data-ttu-id="2c7b1-123">它不会与文件系统、网络或数据库通信。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-123">It doesn't communicate with the file system, the network, or a database.</span></span> <span data-ttu-id="2c7b1-124">单元测试仅测试代码。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-124">Unit tests should only test your code.</span></span>

<span data-ttu-id="2c7b1-125">因为单元测试仅测试单个代码单元，且无外部依赖项，所以执行速度应该非常快。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-125">Unit tests, by virtue of the fact that they test only a single unit of your code, with no external dependencies, should execute extremely quickly.</span></span> <span data-ttu-id="2c7b1-126">因此，可在数秒内运行数百个单元测试的测试套件。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-126">Thus, you should be able to run test suites of hundreds of unit tests in a few seconds.</span></span> <span data-ttu-id="2c7b1-127">请经常运行单元测试，最好是在每次推送到共享源代码管理存储库前运行，当然还要在生成服务器上的每个自动生成时运行它们。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-127">Run them frequently, ideally before every push to a shared source control repository, and certainly with every automated build on your build server.</span></span>

### <a name="integration-tests"></a><span data-ttu-id="2c7b1-128">集成测试</span><span class="sxs-lookup"><span data-stu-id="2c7b1-128">Integration tests</span></span>

<span data-ttu-id="2c7b1-129">尽管建议封装与数据库和文件系统等基础结构交互的代码，但是仍会剩下一些此类代码，你可能需要对其进行测试。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-129">Although it's a good idea to encapsulate your code that interacts with infrastructure like databases and file systems, you will still have some of that code, and you will probably want to test it.</span></span> <span data-ttu-id="2c7b1-130">应用程序依赖项完全解析时，还应验证代码层是否按预期方式交互。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-130">Additionally, you should verify that your code's layers interact as you expect when your application's dependencies are fully resolved.</span></span> <span data-ttu-id="2c7b1-131">这是集成测试的目的。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-131">This is the responsibility of integration tests.</span></span> <span data-ttu-id="2c7b1-132">与单元测试相比，由于集成测试通常依赖外部依赖项和基础结构，因此其设置速度较慢，难度较大。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-132">Integration tests tend to be slower and more difficult to set up than unit tests, because they often depend on external dependencies and infrastructure.</span></span> <span data-ttu-id="2c7b1-133">因此，应避免测试可以通过集成测试中的单元测试进行测试的项。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-133">Thus, you should avoid testing things that could be tested with unit tests in integration tests.</span></span> <span data-ttu-id="2c7b1-134">如果可通过单元测试测试给定方案，请使用单元测试进行测试。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-134">If you can test a given scenario with a unit test, you should test it with a unit test.</span></span> <span data-ttu-id="2c7b1-135">如果不能，再考虑使用集成测试。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-135">If you can't, then consider using an integration test.</span></span>

<span data-ttu-id="2c7b1-136">与单元测试相比，集成测试通常具有更复杂的设置和拆卸过程。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-136">Integration tests will often have more complex setup and teardown procedures than unit tests.</span></span> <span data-ttu-id="2c7b1-137">例如，针对实际数据库运行的集成测试，在每次运行测试前，需要通过一种方式将数据库返回到已知状态。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-137">For example, an integration test that goes against an actual database will need a way to return the database to a known state before each test run.</span></span> <span data-ttu-id="2c7b1-138">随着不断添加新测试以及生产数据库架构不断发展，这些测试脚本的大小和复杂性会逐渐增加。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-138">As new tests are added and the production database schema evolves, these test scripts will tend to grow in size and complexity.</span></span> <span data-ttu-id="2c7b1-139">对于许多大型系统，将签入共享源代码管理更改前，在开发人员工作站上运行一整套集成测试并不实际。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-139">In many large systems, it is impractical to run full suites of integration tests on developer workstations before checking in changes to shared source control.</span></span> <span data-ttu-id="2c7b1-140">这种情况下，可在生成服务器上运行集成测试。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-140">In these cases, integration tests may be run on a build server.</span></span>

### <a name="functional-tests"></a><span data-ttu-id="2c7b1-141">功能测试</span><span class="sxs-lookup"><span data-stu-id="2c7b1-141">Functional tests</span></span>

<span data-ttu-id="2c7b1-142">集成测试从开发者角度编写，用于验证系统的一些组件是否能共同正常运行。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-142">Integration tests are written from the perspective of the developer, to verify that some components of the system work correctly together.</span></span> <span data-ttu-id="2c7b1-143">功能测试从用户角度编写，用于基于其要求验证系统的正确性。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-143">Functional tests are written from the perspective of the user, and verify the correctness of the system based on its requirements.</span></span> <span data-ttu-id="2c7b1-144">下面的节选提供了一个有用的类比，有助于理解功能测试与单元测试的区别：</span><span class="sxs-lookup"><span data-stu-id="2c7b1-144">The following excerpt offers a useful analogy for how to think about functional tests, compared to unit tests:</span></span>

> <span data-ttu-id="2c7b1-145">“很多时候，开发系统类似于修建房屋。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-145">"Many times the development of a system is likened to the building of a house.</span></span> <span data-ttu-id="2c7b1-146">虽然这个类比并不完全准确，但是我们可将其延伸，用以理解单元测试与功能测试的区别。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-146">While this analogy isn't quite correct, we can extend it for the purposes of understanding the difference between unit and functional tests.</span></span> <span data-ttu-id="2c7b1-147">单元测试类似于巡查房屋建筑工地的建筑检查员。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-147">Unit testing is analogous to a building inspector visiting a house's construction site.</span></span> <span data-ttu-id="2c7b1-148">建筑检查员专注于房屋的各种内部系统、地基、框架、电路、管道等。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-148">He is focused on the various internal systems of the house, the foundation, framing, electrical, plumbing, and so on.</span></span> <span data-ttu-id="2c7b1-149">他确保（测试）房屋各部分功能正常且安全，即符合建筑规范。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-149">He ensures (tests) that the parts of the house will work correctly and safely, that is, meet the building code.</span></span> <span data-ttu-id="2c7b1-150">在这种情景下，功能测试类似于出现在同一建筑工地上的房主。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-150">Functional tests in this scenario are analogous to the homeowner visiting this same construction site.</span></span> <span data-ttu-id="2c7b1-151">他假定房屋内部系统一切正常，建筑检查员履行了其检查职责。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-151">He assumes that the internal systems will behave appropriately, that the building inspector is performing his task.</span></span> <span data-ttu-id="2c7b1-152">房主关心的是住在这个房屋里的体验。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-152">The homeowner is focused on what it will be like to live in this house.</span></span> <span data-ttu-id="2c7b1-153">他关心房屋外观如何、每个房间是否大小合适、房屋是否能满足家庭需要，以及窗外是否有好的风景。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-153">He is concerned with how the house looks, are the various rooms a comfortable size, does the house fit the family's needs, are the windows in a good spot to catch the morning sun.</span></span> <span data-ttu-id="2c7b1-154">也就是说，房主对房屋执行功能测试。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-154">The homeowner is performing functional tests on the house.</span></span> <span data-ttu-id="2c7b1-155">他是站在用户角度。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-155">He has the user's perspective.</span></span> <span data-ttu-id="2c7b1-156">建筑检察员则是对房屋进行单元测试。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-156">The building inspector is performing unit tests on the house.</span></span> <span data-ttu-id="2c7b1-157">他站在建筑商角度。”</span><span class="sxs-lookup"><span data-stu-id="2c7b1-157">He has the builder's perspective."</span></span>

<span data-ttu-id="2c7b1-158">源：[单元测试与功能测试](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span><span class="sxs-lookup"><span data-stu-id="2c7b1-158">Source: [Unit Testing versus Functional Tests](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span></span>

<span data-ttu-id="2c7b1-159">我认为：“作为开发人员，我们的失败可能体现在两方面：我们构建应用的方式错误，或者我们的应用不能满足客户需求。”</span><span class="sxs-lookup"><span data-stu-id="2c7b1-159">I'm fond of saying "As developers, we fail in two ways: we build the thing wrong, or we build the wrong thing."</span></span> <span data-ttu-id="2c7b1-160">单元测试可确保构建应用的方式正确；功能测试可确保我们的应用可满足客户需求。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-160">Unit tests ensure you are building the thing right; functional tests ensure you are building the right thing.</span></span>

<span data-ttu-id="2c7b1-161">由于功能测试在系统级别运行，所以可能需要一定程度的 UI 自动化。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-161">Since functional tests operate at the system level, they may require some degree of UI automation.</span></span> <span data-ttu-id="2c7b1-162">与集成测试一样，它们通常也适用于某种类型的测试基础结构。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-162">Like integration tests, they usually work with some kind of test infrastructure as well.</span></span> <span data-ttu-id="2c7b1-163">这使其比单元测试和集成测试更慢、更易发生故障。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-163">This makes them slower and more brittle than unit and integration tests.</span></span> <span data-ttu-id="2c7b1-164">应仅运行确保系统按用户期望运行所需数量的功能测试。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-164">You should have only as many functional tests as you need to be confident the system is behaving as users expect.</span></span>

### <a name="testing-pyramid"></a><span data-ttu-id="2c7b1-165">测试金字塔</span><span class="sxs-lookup"><span data-stu-id="2c7b1-165">Testing Pyramid</span></span>

<span data-ttu-id="2c7b1-166">Martin Fowler 提出了测试金字塔概念，如图 9-1 所示。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-166">Martin Fowler wrote about the testing pyramid, an example of which is shown in Figure 9-1.</span></span>

![测试金字塔](./media/image9-1.png)

<span data-ttu-id="2c7b1-168">**图 9-1**。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-168">**Figure 9-1**.</span></span> <span data-ttu-id="2c7b1-169">测试金字塔</span><span class="sxs-lookup"><span data-stu-id="2c7b1-169">Testing Pyramid</span></span>

<span data-ttu-id="2c7b1-170">该金字塔的不同层次及其相对大小表示不同的测试类别，以及应为应用程序编写的测试数量。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-170">The different layers of the pyramid, and their relative sizes, represent different kinds of tests and how many you should write for your application.</span></span> <span data-ttu-id="2c7b1-171">如图所示，建议以大量单元测试作为基层，中间以较小的集成测试层作为支持，顶端为更小的功能测试层。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-171">As you can see, the recommendation is to have a large base of unit tests, supported by a smaller layer of integration tests, with an even smaller layer of functional tests.</span></span> <span data-ttu-id="2c7b1-172">理想情况下，每层应仅包含较低层中无法充分执行的测试。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-172">Each layer should ideally only have tests in it that cannot be performed adequately at a lower layer.</span></span> <span data-ttu-id="2c7b1-173">确定特定方案所需的测试类型时，请考虑此测试金字塔。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-173">Keep the testing pyramid in mind when you are trying to decide which kind of test you need for a particular scenario.</span></span>

### <a name="what-to-test"></a><span data-ttu-id="2c7b1-174">要测试的内容</span><span class="sxs-lookup"><span data-stu-id="2c7b1-174">What to test</span></span>

<span data-ttu-id="2c7b1-175">对缺乏编写自动测试经验的开发人员而言，一个经常遇到的问题是确定测试内容。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-175">A common problem for developers who are inexperienced with writing automated tests is coming up with what to test.</span></span> <span data-ttu-id="2c7b1-176">不妨从测试条件逻辑开始。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-176">A good starting point is to test conditional logic.</span></span> <span data-ttu-id="2c7b1-177">如果方法中包含基于条件语句（if-else、switch 等）更改的行为，应能至少编写数个用于在某些条件下确定行为是否正确的测试。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-177">Anywhere you have a method with behavior that changes based on a conditional statement (if-else, switch, and so on), you should be able to come up with at least a couple of tests that confirm the correct behavior for certain conditions.</span></span> <span data-ttu-id="2c7b1-178">如果代码存在错误条件，建议通过代码为“主逻辑”编写至少一个测试（不含任何错误），并为“副逻辑”编写至少一个测试（含错误或非典型结果），以确保应用程序在错误情况下按预期运行。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-178">If your code has error conditions, it's good to write at least one test for the "happy path" through the code (with no errors), and at least one test for the "sad path" (with errors or atypical results) to confirm your application behaves as expected in the face of errors.</span></span> <span data-ttu-id="2c7b1-179">最后，重点测试可能失败的项，而不是关注代码覆盖率等指标。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-179">Finally, try to focus on testing things that can fail, rather than focusing on metrics like code coverage.</span></span> <span data-ttu-id="2c7b1-180">一般而言，高代码覆盖率比低代码覆盖率更好。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-180">More code coverage is better than less, generally.</span></span> <span data-ttu-id="2c7b1-181">但是，与仅仅为了改善测试代码覆盖率指标而编写自动属性测试相比，编写复杂的业务关键型方法的测试更有意义。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-181">However, writing a few more tests of a complex and business-critical method is usually a better use of time than writing tests for auto-properties just to improve test code coverage metrics.</span></span>

## <a name="organizing-test-projects"></a><span data-ttu-id="2c7b1-182">组织测试项目</span><span class="sxs-lookup"><span data-stu-id="2c7b1-182">Organizing test projects</span></span>

<span data-ttu-id="2c7b1-183">可按最适合你的方式组织测试项目。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-183">Test projects can be organized however works best for you.</span></span> <span data-ttu-id="2c7b1-184">最好按照类型（单元测试和集成测试）以及测试内容（按项目和按命名空间）分离测试。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-184">It's a good idea to separate tests by type (unit test, integration test) and by what they are testing (by project, by namespace).</span></span> <span data-ttu-id="2c7b1-185">此分离由单个测试项目内的文件夹构成，还是由多个测试项目构成，这取决于设计决策。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-185">Whether this separation consists of folders within a single test project, or multiple test projects, is a design decision.</span></span> <span data-ttu-id="2c7b1-186">虽然一个项目最为简单，但是对于包含多个测试的大型项目，或者为了更轻松地运行不同测试集，可能需要具有一系列不同的测试项目。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-186">One project is simplest, but for large projects with many tests, or in order to more easily run different sets of tests, you might want to have several different test projects.</span></span> <span data-ttu-id="2c7b1-187">许多团队基于要测试的项目组织测试项目，对于具有很多项目的应用程序而言，这可能导致出现大量测试项目，在根据每个项目中的测试类型进行细分的情况下更是如此。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-187">Many teams organize test projects based on the project they are testing, which for applications with more than a few projects can result in a large number of test projects, especially if you still break these down according to what kind of tests are in each project.</span></span> <span data-ttu-id="2c7b1-188">一种折衷方式是让每个测试类型、每个应用程序具有一个项目，测试项目内的文件夹指示要测试的项目（和类）。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-188">A compromise approach is to have one project per kind of test, per application, with folders inside the test projects to indicate the project (and class) being tested.</span></span>

<span data-ttu-id="2c7b1-189">一种常见方式是在“src”文件夹下组织应用程序项目，在并行的“tests”文件夹下组织应用程序的测试项目。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-189">A common approach is to organize the application projects under a 'src' folder, and the application's test projects under a parallel 'tests' folder.</span></span> <span data-ttu-id="2c7b1-190">如果你认为这种组织方式有用，可以在 Visual Studio 中创建匹配的解决方案文件夹。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-190">You can create matching solution folders in Visual Studio, if you find this organization useful.</span></span>

![解决方案中的测试组织](./media/image9-2.png)

<span data-ttu-id="2c7b1-192">**图 9-2**。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-192">**Figure 9-2**.</span></span> <span data-ttu-id="2c7b1-193">解决方案中的测试组织</span><span class="sxs-lookup"><span data-stu-id="2c7b1-193">Test organization in your solution</span></span>

<span data-ttu-id="2c7b1-194">可使用你喜欢的任何测试框架。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-194">You can use whichever test framework you prefer.</span></span> <span data-ttu-id="2c7b1-195">xUnit 框架有效运行，编写所有 ASP.NET Core 和 EF Core 测试时皆使用此框架。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-195">The xUnit framework works well and is what all of the ASP.NET Core and EF Core tests are written in.</span></span> <span data-ttu-id="2c7b1-196">可使用图 9-3 中所示的模板或从使用 `dotnet new xunit` 的 CLI，在 Visual Studio 中添加 xUnit 测试项目。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-196">You can add an xUnit test project in Visual Studio using the template shown in Figure 9-3, or from the CLI using `dotnet new xunit`.</span></span>

![在 Visual Studio 中添加 xUnit 测试项目](./media/image9-3.png)

<span data-ttu-id="2c7b1-198">**图 9-3**。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-198">**Figure 9-3**.</span></span> <span data-ttu-id="2c7b1-199">在 Visual Studio 中添加 xUnit 测试项目</span><span class="sxs-lookup"><span data-stu-id="2c7b1-199">Add an xUnit Test Project in Visual Studio</span></span>

### <a name="test-naming"></a><span data-ttu-id="2c7b1-200">测试命名</span><span class="sxs-lookup"><span data-stu-id="2c7b1-200">Test naming</span></span>

<span data-ttu-id="2c7b1-201">以一致方式命名测试，名称指示每个测试的功能。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-201">Name your tests in a consistent fashion, with names that indicate what each test does.</span></span> <span data-ttu-id="2c7b1-202">我使用的一种很成功的方式是根据其测试的类和方法命名测试类。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-202">One approach I've had great success with is to name test classes according to the class and method they are testing.</span></span> <span data-ttu-id="2c7b1-203">虽然这会产生许多小测试类，但是可非常清楚地表明每个测试的作用。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-203">This results in many small test classes, but it makes it extremely clear what each test is responsible for.</span></span> <span data-ttu-id="2c7b1-204">在设置测试类名称以标识待测试类和方法后，测试方法名称可用于指定要测试的行为。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-204">With the test class name set up to identify the class and method to be tested, the test method name can be used to specify the behavior being tested.</span></span> <span data-ttu-id="2c7b1-205">这应包括预期行为以及任何应导致该行为的输入或假设。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-205">This should include the expected behavior and any inputs or assumptions that should yield this behavior.</span></span> <span data-ttu-id="2c7b1-206">部分示例测试名称：</span><span class="sxs-lookup"><span data-stu-id="2c7b1-206">Some example test names:</span></span>

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

<span data-ttu-id="2c7b1-207">此方式的一种变体是让每个测试类名称以“Should”结尾，并稍微修改其时态：</span><span class="sxs-lookup"><span data-stu-id="2c7b1-207">A variation of this approach ends each test class name with "Should" and modifies the tense slightly:</span></span>

- <span data-ttu-id="2c7b1-208">`CatalogControllerGetImage`**Should**`.`**Call**`ImageServiceWithId`</span><span class="sxs-lookup"><span data-stu-id="2c7b1-208">`CatalogControllerGetImage`**Should**`.`**Call**`ImageServiceWithId`</span></span>

- <span data-ttu-id="2c7b1-209">`CatalogControllerGetImage`**Should**`.`**Log**`WarningGivenImageMissingException`</span><span class="sxs-lookup"><span data-stu-id="2c7b1-209">`CatalogControllerGetImage`**Should**`.`**Log**`WarningGivenImageMissingException`</span></span>

<span data-ttu-id="2c7b1-210">虽然第二种命名方式略为冗长，但一些团队发现这种命名方式更加清楚。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-210">Some teams find the second naming approach clearer, though slightly more verbose.</span></span> <span data-ttu-id="2c7b1-211">任何情况下，请使用可提供测试行为见解的命名约定，以便一个或多个测试失败时，可通过其名称清楚了解已失败的事例。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-211">In any case, try to use a naming convention that provides insight into test behavior, so that when one or more tests fail, it's obvious from their names what cases have failed.</span></span> <span data-ttu-id="2c7b1-212">避免使用 ControllerTests.Test1 等模糊的测试名称，因为查看测试结果时，此类名称不能提供任何价值。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-212">Avoid naming your tests vaguely, such as ControllerTests.Test1, as these offer no value when you see them in test results.</span></span>

<span data-ttu-id="2c7b1-213">如果使用类似上述会产生众多小测试类的命名约定，建议使用文件夹和命名空间进一步组织测试。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-213">If you follow a naming convention like the one above that produces many small test classes, it's a good idea to further organize your tests using folders and namespaces.</span></span> <span data-ttu-id="2c7b1-214">图 9-4 显示了一种在数个测试项目内按照文件夹组织测试的方式。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-214">Figure 9-4 shows one approach to organizing tests by folder within several test projects.</span></span>

![基于要测试的类按照文件夹组织测试类](./media/image9-4.png)

<span data-ttu-id="2c7b1-216">**图 9-4**。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-216">**Figure 9-4.**</span></span> <span data-ttu-id="2c7b1-217">基于要测试的类按照文件夹组织测试类。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-217">Organizing test classes by folder based on class being tested.</span></span>

<span data-ttu-id="2c7b1-218">如果特定应用程序类具有多个待测试的方法（以及由此产生的众多测试类），最好将其放置于该应用程序类对应的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-218">If a particular application class has many methods being tested (and thus many test classes), it may make sense to place these in a folder corresponding to the application class.</span></span> <span data-ttu-id="2c7b1-219">该组织方式与在其他情况下将文件组织到文件夹并无差别。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-219">This organization is no different than how you might organize files into folders elsewhere.</span></span> <span data-ttu-id="2c7b1-220">如果一个包含许多其他文件的文件夹中具有三个或四个以上相关文件，最好将其移动到它们自己的子文件夹中。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-220">If you have more than three or four related files in a folder containing many other files, it's often helpful to move them into their own subfolder.</span></span>

## <a name="unit-testing-aspnet-core-apps"></a><span data-ttu-id="2c7b1-221">对 ASP.NET Core 应用执行单元测试</span><span class="sxs-lookup"><span data-stu-id="2c7b1-221">Unit testing ASP.NET Core apps</span></span>

<span data-ttu-id="2c7b1-222">在具有出色设计的 ASP.NET Core 应用程序中，大多数复杂性和业务逻辑会封装在业务实体以及各种服务中。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-222">In a well-designed ASP.NET Core application, most of the complexity and business logic will be encapsulated in business entities and a variety of services.</span></span> <span data-ttu-id="2c7b1-223">ASP.NET Core MVC 应用本身及其控制器、筛选器、视图模型和视图需要的单元测试极少。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-223">The ASP.NET Core MVC app itself, with its controllers, filters, viewmodels, and views, should require very few unit tests.</span></span> <span data-ttu-id="2c7b1-224">特定操作的很多功能体现在该操作方法之外。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-224">Much of the functionality of a given action lies outside the action method itself.</span></span> <span data-ttu-id="2c7b1-225">使用单元测试无法有效地测试路由或全局错误处理是否正常工作。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-225">Testing whether routing or global error handling work correctly cannot be done effectively with a unit test.</span></span> <span data-ttu-id="2c7b1-226">同样，无法使用针对控制器的操作方法的测试对任何筛选器（包括模型验证筛选器以及身份验证和授权筛选器）执行单元测试。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-226">Likewise, any filters, including model validation and authentication and authorization filters, cannot be unit tested with a test targeting a controller's action method.</span></span> <span data-ttu-id="2c7b1-227">如果没有这些行为源，大多数操作方法应非常小，这会将其大量工作委托至服务（可独立于使用这些服务的控制器对这些服务执行测试）。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-227">Without these sources of behavior, most action methods should be trivially small, delegating the bulk of their work to services that can be tested independent of the controller that uses them.</span></span>

<span data-ttu-id="2c7b1-228">有时为对代码执行单元测试，需要重构代码。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-228">Sometimes you'll need to refactor your code in order to unit test it.</span></span> <span data-ttu-id="2c7b1-229">通常，这涉及到确定抽象以及使用依赖项注入来访问待测试代码中的抽象，而不是直接针对基础结构编码。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-229">Frequently this involves identifying abstractions and using dependency injection to access the abstraction in the code you'd like to test, rather than coding directly against infrastructure.</span></span> <span data-ttu-id="2c7b1-230">例如，请思考以下用于显示图像的简单操作方法：</span><span class="sxs-lookup"><span data-stu-id="2c7b1-230">For example, consider this simple action method for displaying images:</span></span>

```csharp
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    var contentRoot = _env.ContentRootPath + "//Pics";
    var path = Path.Combine(contentRoot, id + ".png");
    Byte[] b = System.IO.File.ReadAllBytes(path);
    return File(b, "image/png");
}
```

<span data-ttu-id="2c7b1-231">通过 `System.IO.File` 上的直接依赖项难以对此方法执行单元测试。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-231">Unit testing this method is made difficult by its direct dependency on `System.IO.File`, which it uses to read from the file system.</span></span> <span data-ttu-id="2c7b1-232">可测试此行为以确保其按预期方式运行，但对实际文件执行此操作属于集成测试。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-232">You can test this behavior to ensure it works as expected, but doing so with real files is an integration test.</span></span> <span data-ttu-id="2c7b1-233">值得注意的是，无法对此方法的路由进行单元测试，我们很快将讲解如何通过功能测试来进行此操作。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-233">It's worth noting you can't unit test this method's route&mdash;you'll see how to do this with a functional test shortly.</span></span>

<span data-ttu-id="2c7b1-234">如果无法直接对文件系统行为执行单元测试，且无法测试路由，还能测试什么呢？</span><span class="sxs-lookup"><span data-stu-id="2c7b1-234">If you can't unit test the file system behavior directly, and you can't test the route, what is there to test?</span></span> <span data-ttu-id="2c7b1-235">通过重构确保单元测试的可行性后，可能会发现一些测试用例以及缺失行为，例如错误处理。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-235">Well, after refactoring to make unit testing possible, you may discover some test cases and missing behavior, such as error handling.</span></span> <span data-ttu-id="2c7b1-236">如未找到文件，此方法会执行什么操作？</span><span class="sxs-lookup"><span data-stu-id="2c7b1-236">What does the method do when a file isn't found?</span></span> <span data-ttu-id="2c7b1-237">它应执行什么操作？</span><span class="sxs-lookup"><span data-stu-id="2c7b1-237">What should it do?</span></span> <span data-ttu-id="2c7b1-238">本示例中，重构方法如下：</span><span class="sxs-lookup"><span data-stu-id="2c7b1-238">In this example, the refactored method looks like this:</span></span>

```csharp
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    byte[] imageBytes;
    try
    {
        imageBytes = _imageService.GetImageBytesById(id);
    }
    catch (CatalogImageMissingException ex)
    {
        _logger.LogWarning($"No image found for id: {id}");
        return NotFound();
    }
    return File(imageBytes, "image/png");
}
```

<span data-ttu-id="2c7b1-239">`_logger` 和 `_imageService` 都作为依赖项注入。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-239">`_logger` and `_imageService` are both injected as dependencies.</span></span> <span data-ttu-id="2c7b1-240">现在，可测试是否传递到操作方法的相同 ID 被传递到 `_imageService`，以及生成的字节是否作为 FileResult 的一部分返回。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-240">Now you can test that the same ID that is passed to the action method is passed to `_imageService`, and that the resulting bytes are returned as part of the FileResult.</span></span> <span data-ttu-id="2c7b1-241">还可测试错误日志记录是否按预期发生，以及如果映像缺失，是否返回 `NotFound` 结果（假定这是重要的应用程序行为，即不只是开发人员为诊断问题而添加的临时代码）。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-241">You can also test that error logging is happening as expected, and that a `NotFound` result is returned if the image is missing, assuming this is important application behavior (that is, not just temporary code the developer added to diagnose an issue).</span></span> <span data-ttu-id="2c7b1-242">已将实际文件逻辑移动到单独的实现服务，并已将其扩充，以在缺失文件的情况下返回特定于应用程序的异常。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-242">The actual file logic has moved into a separate implementation service, and has been augmented to return an application-specific exception for the case of a missing file.</span></span> <span data-ttu-id="2c7b1-243">可使用集成测试独立测试该实现。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-243">You can test this implementation independently, using an integration test.</span></span>

<span data-ttu-id="2c7b1-244">在大多数情况下，需要在控制器中使用全局异常处理程序，因此它们中的逻辑量应该是最小的，并且可能不值得进行单元测试。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-244">In most cases, you'll want to use global exception handlers in your controllers, so the amount of logic in them should be minimal and probably not worth unit testing.</span></span> <span data-ttu-id="2c7b1-245">使用功能测试和下面介绍的 `TestServer` 类对控制器操作进行大部分测试。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-245">Do most of your testing of controller actions using functional tests and the `TestServer` class described below.</span></span>

## <a name="integration-testing-aspnet-core-apps"></a><span data-ttu-id="2c7b1-246">对 ASP.NET Core 应用执行集成测试</span><span class="sxs-lookup"><span data-stu-id="2c7b1-246">Integration testing ASP.NET Core apps</span></span>

<span data-ttu-id="2c7b1-247">ASP.NET Core 应用中的大多数集成测试应该是测试基础结构项目中定义的服务和其他实现类型。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-247">Most of the integration tests in your ASP.NET Core apps should be testing services and other implementation types defined in your Infrastructure project.</span></span> <span data-ttu-id="2c7b1-248">例如，可以[测试 EF Core 是否已成功更新并检索](/ef/core/miscellaneous/testing/)希望从驻留在基础结构项目中的数据访问类中获得的数据。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-248">For example, you could [test that EF Core was successfully updating and retrieving the data that you expect](/ef/core/miscellaneous/testing/) from your data access classes residing in the Infrastructure project.</span></span> <span data-ttu-id="2c7b1-249">测试 ASP.NET Core MVC 项目是否正常运行的最佳方法是针对在测试主机中运行的应用运行的功能测试。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-249">The best way to test that your ASP.NET Core MVC project is behaving correctly is with functional tests that run against your app running in a test host.</span></span>

## <a name="functional-testing-aspnet-core-apps"></a><span data-ttu-id="2c7b1-250">对 ASP.NET Core 应用执行功能测试</span><span class="sxs-lookup"><span data-stu-id="2c7b1-250">Functional testing ASP.NET Core apps</span></span>

<span data-ttu-id="2c7b1-251">对于 ASP.NET Core 应用程序，`TestServer` 类让功能测试非常易于编写。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-251">For ASP.NET Core applications, the `TestServer` class makes functional tests fairly easy to write.</span></span> <span data-ttu-id="2c7b1-252">可以直接使用 `WebHostBuilder`（或 `HostBuilder`）（针对应用程序的一般操作）或使用 `WebApplicationFactory` 类型（自 2.1 版开始提供）来配置 `TestServer`。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-252">You configure a `TestServer` using a `WebHostBuilder` (or `HostBuilder`) directly (as you normally do for your application), or with the `WebApplicationFactory` type (available since version 2.1).</span></span> <span data-ttu-id="2c7b1-253">尝试将测试主机与生产主机进行尽可能密切的匹配，以便让测试执行与应用将在生产中进行的行为类似的行为。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-253">Try to match your test host to your production host as closely as possible, so your tests exercise behavior similar to what the app will do in production.</span></span> <span data-ttu-id="2c7b1-254">`WebApplicationFactory` 类有助于配置 TestServer 的 ContentRoot，该 ContentRoot 由 ASP.NET Core 用于定位静态资源（例如视图）。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-254">The `WebApplicationFactory` class is helpful for configuring the TestServer's ContentRoot, which is used by ASP.NET Core to locate static resource like Views.</span></span>

<span data-ttu-id="2c7b1-255">可通过创建实现 `IClassFixture\<WebApplicationFactory\<TEntry>>`（其中 `TEntry` 为 Web 应用程序的 `Startup` 类）的测试类来创建简单的功能测试。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-255">You can create simple functional tests by creating a test class that implements `IClassFixture\<WebApplicationFactory\<TEntry>>`, where `TEntry` is your web application's `Startup` class.</span></span> <span data-ttu-id="2c7b1-256">创建完成后，测试固定例程可使用工厂的 `CreateClient` 方法来创建客户端：</span><span class="sxs-lookup"><span data-stu-id="2c7b1-256">With this in place, your test fixture can create a client using the factory's `CreateClient` method:</span></span>

```csharp
public class BasicWebTests : IClassFixture<WebApplicationFactory<Startup>>
{
    protected readonly HttpClient _client;

    public BasicWebTests(WebApplicationFactory<Startup> factory)
    {
        _client = factory.CreateClient();
    }

    // write tests that use _client
}
```

<span data-ttu-id="2c7b1-257">用户常常想要在运行每个测试之前对站点执行一些其他配置，例如将应用程序配置为使用内存中数据存储，然后将测试数据植入应用程序。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-257">Frequently, you'll want to perform some additional configuration of your site before each test runs, such as configuring the application to use an in memory data store and then seeding the application with test data.</span></span> <span data-ttu-id="2c7b1-258">为此，请创建你自己的 `WebApplicationFactory\<TEntry>` 的子类并替代其 `ConfigureWebHost` 方法。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-258">To do this, create your own subclass of `WebApplicationFactory\<TEntry>` and override its `ConfigureWebHost` method.</span></span> <span data-ttu-id="2c7b1-259">以下示例来自 eShopOnWeb FunctionalTests 项目，并用作主要 Web 应用上的测试的一部分。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-259">The example below is from the eShopOnWeb FunctionalTests project and is used as part of the tests on the main web application.</span></span>

```csharp
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Identity;
using Microsoft.AspNetCore.Mvc.Testing;
using Microsoft.EntityFrameworkCore;
using Microsoft.eShopWeb.Infrastructure.Data;
using Microsoft.eShopWeb.Infrastructure.Identity;
using Microsoft.eShopWeb.Web;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Logging;
using System;

namespace Microsoft.eShopWeb.FunctionalTests.Web
{
    public class WebTestFixture : WebApplicationFactory<Startup>
    {
        protected override void ConfigureWebHost(IWebHostBuilder builder)
        {
            builder.UseEnvironment("Testing");

            builder.ConfigureServices(services =>
            {
                 services.AddEntityFrameworkInMemoryDatabase();

                // Create a new service provider.
                var provider = services
                    .AddEntityFrameworkInMemoryDatabase()
                    .BuildServiceProvider();

                // Add a database context (ApplicationDbContext) using an in-memory
                // database for testing.
                services.AddDbContext<CatalogContext>(options =>
                {
                    options.UseInMemoryDatabase("InMemoryDbForTesting");
                    options.UseInternalServiceProvider(provider);
                });

                services.AddDbContext<AppIdentityDbContext>(options =>
                {
                    options.UseInMemoryDatabase("Identity");
                    options.UseInternalServiceProvider(provider);
                });

                // Build the service provider.
                var sp = services.BuildServiceProvider();

                // Create a scope to obtain a reference to the database
                // context (ApplicationDbContext).
                using (var scope = sp.CreateScope())
                {
                    var scopedServices = scope.ServiceProvider;
                    var db = scopedServices.GetRequiredService<CatalogContext>();
                    var loggerFactory = scopedServices.GetRequiredService<ILoggerFactory>();

                    var logger = scopedServices
                        .GetRequiredService<ILogger<WebTestFixture>>();

                    // Ensure the database is created.
                    db.Database.EnsureCreated();

                    try
                    {
                        // Seed the database with test data.
                        CatalogContextSeed.SeedAsync(db, loggerFactory).Wait();

                        // seed sample user data
                        var userManager = scopedServices.GetRequiredService<UserManager<ApplicationUser>>();
                        var roleManager = scopedServices.GetRequiredService<RoleManager<IdentityRole>>();
                        AppIdentityDbContextSeed.SeedAsync(userManager, roleManager).Wait();
                    }
                    catch (Exception ex)
                    {
                        logger.LogError(ex, $"An error occurred seeding the " +
                            "database with test messages. Error: {ex.Message}");
                    }
                }
            });
        }
    }
}
```

<span data-ttu-id="2c7b1-260">测试可以使用此自定义 WebApplicationFactory 来创建客户端，并使用此客户端实例向应用程序作出请求。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-260">Tests can make use of this custom WebApplicationFactory by using it to create a client and then making requests to the application using this client instance.</span></span> <span data-ttu-id="2c7b1-261">该应用程序将具备植入的数据，这些数据可用作测试断言的一部分。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-261">The application will have data seeded that can be used as part of the test's assertions.</span></span> <span data-ttu-id="2c7b1-262">以下测试验证 eShopOnWeb 应用程序的主页是否正确加载并包括已作为种子数据的一部分添加至应用程序的产品列表。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-262">The following test verifies that the home page of the eShopOnWeb application loads correctly and includes a product listing that was added to the application as part of the seed data.</span></span>

```csharp
using Microsoft.eShopWeb.FunctionalTests.Web;
using System.Net.Http;
using System.Threading.Tasks;
using Xunit;

namespace Microsoft.eShopWeb.FunctionalTests.WebRazorPages
{
    [Collection("Sequential")]
    public class HomePageOnGet : IClassFixture<WebTestFixture>
    {
        public HomePageOnGet(WebTestFixture factory)
        {
            Client = factory.CreateClient();
        }

        public HttpClient Client { get; }

        [Fact]
        public async Task ReturnsHomePageWithProductListing()
        {
            // Arrange & Act
            var response = await Client.GetAsync("/");
            response.EnsureSuccessStatusCode();
            var stringResponse = await response.Content.ReadAsStringAsync();

            // Assert
            Assert.Contains(".NET Bot Black Sweatshirt", stringResponse);
        }
    }
}
```

<span data-ttu-id="2c7b1-263">此功能测试会演练完整的 ASP.NET Core MVC/Razor Pages 应用程序堆栈，包括准备就绪的所有中间件、筛选器和绑定器等。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-263">This functional test exercises the full ASP.NET Core MVC / Razor Pages application stack, including all middleware, filters, and binders that may be in place.</span></span> <span data-ttu-id="2c7b1-264">它验证给定的路由 ("/") 是否返回预期的成功状态代码和 HTML 输出。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-264">It verifies that a given route ("/") returns the expected success status code and HTML output.</span></span> <span data-ttu-id="2c7b1-265">它无需设置实际的 Web 服务器即可实现该操作，并且可以避免使用实际 Web 服务器进行测试可能遇到的许多问题（例如防火墙设置问题）。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-265">It does so without setting up a real web server, and avoids much of the brittleness that using a real web server for testing can experience (for example, problems with firewall settings).</span></span> <span data-ttu-id="2c7b1-266">虽然针对 TestServer 运行的功能测试通常比集成测试和单元测试更慢，但是比测试 Web 服务器的网络上运行的测试速度更快。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-266">Functional tests that run against TestServer are usually slower than integration and unit tests, but are much faster than tests that would run over the network to a test web server.</span></span> <span data-ttu-id="2c7b1-267">使用功能测试来确保应用程序的前端堆栈按预期运行。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-267">Use functional tests to ensure your application's front-end stack is working as expected.</span></span> <span data-ttu-id="2c7b1-268">当在控制器或页面中发现了重复内容并通过添加筛选器找到了这些重复内容时，这些测试将尤为有用。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-268">These tests are especially useful when you find duplication in your controllers or pages and you address the duplication by adding filters.</span></span> <span data-ttu-id="2c7b1-269">理想情况下，此重构不会改变应用程序的行为，并且将有一套功能测试来验证确实如此。</span><span class="sxs-lookup"><span data-stu-id="2c7b1-269">Ideally, this refactoring won't change the behavior of the application, and a suite of functional tests will verify this is the case.</span></span>

> ### <a name="references--test-aspnet-core-mvc-apps"></a><span data-ttu-id="2c7b1-270">参考 - 测试 ASP.NET Core MVC 应用</span><span class="sxs-lookup"><span data-stu-id="2c7b1-270">References – Test ASP.NET Core MVC apps</span></span>
>
> - <span data-ttu-id="2c7b1-271">在 ASP.NET Core 中进行测试   </span><span class="sxs-lookup"><span data-stu-id="2c7b1-271">**Testing in ASP.NET Core** </span></span>\
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - <span data-ttu-id="2c7b1-272">单元测试命名约定   </span><span class="sxs-lookup"><span data-stu-id="2c7b1-272">**Unit Test Naming Convention** </span></span>\
>   <https://ardalis.com/unit-test-naming-convention>
> - <span data-ttu-id="2c7b1-273">测试 EF Core   </span><span class="sxs-lookup"><span data-stu-id="2c7b1-273">**Testing EF Core** </span></span>\
>   <https://docs.microsoft.com/ef/core/miscellaneous/testing/>
> - <span data-ttu-id="2c7b1-274">ASP.NET Core 中的集成测试   </span><span class="sxs-lookup"><span data-stu-id="2c7b1-274">**Integration tests in ASP.NET Core** </span></span>\
>   <https://docs.microsoft.com/aspnet/core/test/integration-tests>

>[!div class="step-by-step"]
><span data-ttu-id="2c7b1-275">[上一页](work-with-data-in-asp-net-core-apps.md)
>[下一页](development-process-for-azure.md)</span><span class="sxs-lookup"><span data-stu-id="2c7b1-275">[Previous](work-with-data-in-asp-net-core-apps.md)
[Next](development-process-for-azure.md)</span></span>
