---
title: 测试 ASP.NET Core 服务和 Web 应用
description: 适用于容器化 .NET 应用程序的 .NET 微服务体系结构 | 探索用于在容器中测试 ASP.NET Core 服务和 Web 应用的体系结构。
ms.date: 08/07/2020
ms.openlocfilehash: af1187fb1e2afbb9fa953db5a280c9cc317ab6a8
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2020
ms.locfileid: "91804765"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a><span data-ttu-id="d3909-103">测试 ASP.NET Core 服务和 Web 应用</span><span class="sxs-lookup"><span data-stu-id="d3909-103">Testing ASP.NET Core services and web apps</span></span>

<span data-ttu-id="d3909-104">控制器是 ASP.NET Core API 服务和 ASP.NET MVC Web 应用程序的核心部分。</span><span class="sxs-lookup"><span data-stu-id="d3909-104">Controllers are a central part of any ASP.NET Core API service and ASP.NET MVC Web application.</span></span> <span data-ttu-id="d3909-105">因此，应该对它们会按照应用程序所计划的那样正常运行有信心。</span><span class="sxs-lookup"><span data-stu-id="d3909-105">As such, you should have confidence they behave as intended for your application.</span></span> <span data-ttu-id="d3909-106">自动测试可以给你这种信心，还可在生产前检测错误。</span><span class="sxs-lookup"><span data-stu-id="d3909-106">Automated tests can provide you with this confidence and can detect errors before they reach production.</span></span>

<span data-ttu-id="d3909-107">需要根据有效或无效输入测试控制器的运行状况，并根据其执行的业务操作的结果测试控制器的响应情况。</span><span class="sxs-lookup"><span data-stu-id="d3909-107">You need to test how the controller behaves based on valid or invalid inputs, and test controller responses based on the result of the business operation it performs.</span></span> <span data-ttu-id="d3909-108">但是，应对微服务进行这些类型的测试：</span><span class="sxs-lookup"><span data-stu-id="d3909-108">However, you should have these types of tests for your microservices:</span></span>

- <span data-ttu-id="d3909-109">单元测试。</span><span class="sxs-lookup"><span data-stu-id="d3909-109">Unit tests.</span></span> <span data-ttu-id="d3909-110">这可确保应用程序的各个组件按预期工作。</span><span class="sxs-lookup"><span data-stu-id="d3909-110">These ensure that individual components of the application work as expected.</span></span> <span data-ttu-id="d3909-111">断言测试组件 API。</span><span class="sxs-lookup"><span data-stu-id="d3909-111">Assertions test the component API.</span></span>

- <span data-ttu-id="d3909-112">集成测试。</span><span class="sxs-lookup"><span data-stu-id="d3909-112">Integration tests.</span></span> <span data-ttu-id="d3909-113">这可确保对于数据库等外部项目，组件交互按预期工作。</span><span class="sxs-lookup"><span data-stu-id="d3909-113">These ensure that component interactions work as expected against external artifacts like databases.</span></span> <span data-ttu-id="d3909-114">断言可以测试组件 API、UI 或数据库 I/O、登录等操作的副作用。</span><span class="sxs-lookup"><span data-stu-id="d3909-114">Assertions can test component API, UI, or the side effects of actions like database I/O, logging, etc.</span></span>

- <span data-ttu-id="d3909-115">每个微服务的的功能测试。</span><span class="sxs-lookup"><span data-stu-id="d3909-115">Functional tests for each microservice.</span></span> <span data-ttu-id="d3909-116">这可确保从用户角度，应用程序按预期运行。</span><span class="sxs-lookup"><span data-stu-id="d3909-116">These ensure that the application works as expected from the user's perspective.</span></span>

- <span data-ttu-id="d3909-117">服务测试。</span><span class="sxs-lookup"><span data-stu-id="d3909-117">Service tests.</span></span> <span data-ttu-id="d3909-118">这可确保测试端到端服务用例，包括同时测试多个服务。</span><span class="sxs-lookup"><span data-stu-id="d3909-118">These ensure that end-to-end service use cases, including testing multiple services at the same time, are tested.</span></span> <span data-ttu-id="d3909-119">对于此类型的测试，需要首先准备环境。</span><span class="sxs-lookup"><span data-stu-id="d3909-119">For this type of testing, you need to prepare the environment first.</span></span> <span data-ttu-id="d3909-120">在这种情况下，这意味着启动服务（例如，通过使用 docker-compose up）。</span><span class="sxs-lookup"><span data-stu-id="d3909-120">In this case, it means starting the services (for example, by using docker-compose up).</span></span>

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a><span data-ttu-id="d3909-121">实现 ASP.NET Core Web API 的单元测试</span><span class="sxs-lookup"><span data-stu-id="d3909-121">Implementing unit tests for ASP.NET Core Web APIs</span></span>

<span data-ttu-id="d3909-122">单元测试涉及在测试应用程序部分时，使之与它的基础结构和依赖关系相隔离。</span><span class="sxs-lookup"><span data-stu-id="d3909-122">Unit testing involves testing a part of an application in isolation from its infrastructure and dependencies.</span></span> <span data-ttu-id="d3909-123">单元测试控制器逻辑时，仅测试单个操作或方法的内容，不测试其依赖项或框架自身的行为。</span><span class="sxs-lookup"><span data-stu-id="d3909-123">When you unit test controller logic, only the content of a single action or method is tested, not the behavior of its dependencies or of the framework itself.</span></span> <span data-ttu-id="d3909-124">单位测试不检测部件间交互的问题，这是集成测试的用途。</span><span class="sxs-lookup"><span data-stu-id="d3909-124">Unit tests do not detect issues in the interaction between components—that is the purpose of integration testing.</span></span>

<span data-ttu-id="d3909-125">单元测试控制器操作时，请确保仅关注其行为。</span><span class="sxs-lookup"><span data-stu-id="d3909-125">As you unit test your controller actions, make sure you focus only on their behavior.</span></span> <span data-ttu-id="d3909-126">控制器单元测试可避免筛选器、路由或模型绑定（请求数据到 ViewModel 或 DTO 的映射）等情况。</span><span class="sxs-lookup"><span data-stu-id="d3909-126">A controller unit test avoids things like filters, routing, or model binding (the mapping of request data to a ViewModel or DTO).</span></span> <span data-ttu-id="d3909-127">由于仅专注测试一项内容，单位测试通常编写简单、运行迅速。</span><span class="sxs-lookup"><span data-stu-id="d3909-127">Because they focus on testing just one thing, unit tests are generally simple to write and quick to run.</span></span> <span data-ttu-id="d3909-128">正确编写的单位测试集无需过多开销即可经常运行。</span><span class="sxs-lookup"><span data-stu-id="d3909-128">A well-written set of unit tests can be run frequently without much overhead.</span></span>

<span data-ttu-id="d3909-129">单元测试基于 xUnit.net、MSTest、Moq 或 NUnit 等测试框架实现。</span><span class="sxs-lookup"><span data-stu-id="d3909-129">Unit tests are implemented based on test frameworks like xUnit.net, MSTest, Moq, or NUnit.</span></span> <span data-ttu-id="d3909-130">对于 eShopOnContainers 示例应用程序，我们使用 xUnit。</span><span class="sxs-lookup"><span data-stu-id="d3909-130">For the eShopOnContainers sample application, we are using xUnit.</span></span>

<span data-ttu-id="d3909-131">为 Web API 控制器编写单元测试时，通过使用 C\# 中的新关键字直接实例化控制器类，以便尽快运行测试。</span><span class="sxs-lookup"><span data-stu-id="d3909-131">When you write a unit test for a Web API controller, you instantiate the controller class directly using the new keyword in C\#, so that the test will run as fast as possible.</span></span> <span data-ttu-id="d3909-132">下面的示例演示如何将 [xUnit](https://xunit.github.io/) 作为测试框架执行此操作。</span><span class="sxs-lookup"><span data-stu-id="d3909-132">The following example shows how to do this when using [xUnit](https://xunit.github.io/) as the Test framework.</span></span>

```csharp
[Fact]
public async Task Get_order_detail_success()
{
    //Arrange
    var fakeOrderId = "12";
    var fakeOrder = GetFakeOrder();

    //...

    //Act
    var orderController = new OrderController(
        _orderServiceMock.Object,
        _basketServiceMock.Object,
        _identityParserMock.Object);

    orderController.ControllerContext.HttpContext = _contextMock.Object;
    var actionResult = await orderController.Detail(fakeOrderId);

    //Assert
    var viewResult = Assert.IsType<ViewResult>(actionResult);
    Assert.IsAssignableFrom<Order>(viewResult.ViewData.Model);
}
```

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a><span data-ttu-id="d3909-133">为每个微服务实现集成和功能测试</span><span class="sxs-lookup"><span data-stu-id="d3909-133">Implementing integration and functional tests for each microservice</span></span>

<span data-ttu-id="d3909-134">如上所述，集成测试和功能测试具有不同的用途和目标。</span><span class="sxs-lookup"><span data-stu-id="d3909-134">As noted, integration tests and functional tests have different purposes and goals.</span></span> <span data-ttu-id="d3909-135">但是，测试 ASP.NET Core 控制器时实现两者的方式类似，所以在此部分中，我们着重介绍集成测试。</span><span class="sxs-lookup"><span data-stu-id="d3909-135">However, the way you implement both when testing ASP.NET Core controllers is similar, so in this section we concentrate on integration tests.</span></span>

<span data-ttu-id="d3909-136">集成测试可确保应用程序的组件在组装后正常运行。</span><span class="sxs-lookup"><span data-stu-id="d3909-136">Integration testing ensures that an application's components function correctly when assembled.</span></span> <span data-ttu-id="d3909-137">ASP.NET Core 使用单元测试框架和可用于处理请求（无网络费用）的内置测试 web 主机支持集成测试。</span><span class="sxs-lookup"><span data-stu-id="d3909-137">ASP.NET Core supports integration testing using unit test frameworks and a built-in test web host that can be used to handle requests without network overhead.</span></span>

<span data-ttu-id="d3909-138">与单元测试不同，集成测试经常产生应用程序基础结构问题，例如数据库、文件系统、网络资源或 web 请求和响应。</span><span class="sxs-lookup"><span data-stu-id="d3909-138">Unlike unit testing, integration tests frequently involve application infrastructure concerns, such as a database, file system, network resources, or web requests and responses.</span></span> <span data-ttu-id="d3909-139">单元测试使用虚设或 mock 对象解决这些问题。</span><span class="sxs-lookup"><span data-stu-id="d3909-139">Unit tests use fakes or mock objects in place of these concerns.</span></span> <span data-ttu-id="d3909-140">但集成测试的目的是确保系统按预期正常运行，因此对于集成测试，不能使用虚设或 mock 对象。</span><span class="sxs-lookup"><span data-stu-id="d3909-140">But the purpose of integration tests is to confirm that the system works as expected with these systems, so for integration testing you do not use fakes or mock objects.</span></span> <span data-ttu-id="d3909-141">可以改为使用基础结构，如数据库访问或从其他服务中调用服务。</span><span class="sxs-lookup"><span data-stu-id="d3909-141">Instead, you include the infrastructure, like database access or service invocation from other services.</span></span>

<span data-ttu-id="d3909-142">与单元测试相比，集成测试执行较多的代码片段，且集成测试依赖基础结构元素，因此它的速度比单元测试慢几个数量级。</span><span class="sxs-lookup"><span data-stu-id="d3909-142">Because integration tests exercise larger segments of code than unit tests, and because integration tests rely on infrastructure elements, they tend to be orders of magnitude slower than unit tests.</span></span> <span data-ttu-id="d3909-143">因此，最好限制编写和运行的集成测试数量。</span><span class="sxs-lookup"><span data-stu-id="d3909-143">Thus, it is a good idea to limit how many integration tests you write and run.</span></span>

<span data-ttu-id="d3909-144">ASP.NET Core 包括可用于处理 HTTP 请求且无网络费用的内置测试 web 主机，这意味着可比使用真正的 Web 主机时更快地运行这些测试。</span><span class="sxs-lookup"><span data-stu-id="d3909-144">ASP.NET Core includes a built-in test web host that can be used to handle HTTP requests without network overhead, meaning that you can run those tests faster than when using a real web host.</span></span> <span data-ttu-id="d3909-145">NuGet 组件中，测试 web 主机 (TestServer) 作为 Microsoft.AspNetCore.TestHost 提供。</span><span class="sxs-lookup"><span data-stu-id="d3909-145">The test web host (TestServer) is available in a NuGet component as Microsoft.AspNetCore.TestHost.</span></span> <span data-ttu-id="d3909-146">可将其添加到集成测试项目，并用于托管 ASP.NET Core 应用程序。</span><span class="sxs-lookup"><span data-stu-id="d3909-146">It can be added to integration test projects and used to host ASP.NET Core applications.</span></span>

<span data-ttu-id="d3909-147">如以下代码所示，创建 ASP.NET Core 控制器的集成测试时，通过测试主机实例化控制器。</span><span class="sxs-lookup"><span data-stu-id="d3909-147">As you can see in the following code, when you create integration tests for ASP.NET Core controllers, you instantiate the controllers through the test host.</span></span> <span data-ttu-id="d3909-148">这相当于 HTTP 请求，但它的运行速度更快。</span><span class="sxs-lookup"><span data-stu-id="d3909-148">This is comparable to an HTTP request, but it runs faster.</span></span>

```csharp
public class PrimeWebDefaultRequestShould
{
    private readonly TestServer _server;
    private readonly HttpClient _client;

    public PrimeWebDefaultRequestShould()
    {
        // Arrange
        _server = new TestServer(new WebHostBuilder()
           .UseStartup<Startup>());
           _client = _server.CreateClient();
    }

    [Fact]
    public async Task ReturnHelloWorld()
    {
        // Act
        var response = await _client.GetAsync("/");
        response.EnsureSuccessStatusCode();
        var responseString = await response.Content.ReadAsStringAsync();
        // Assert
        Assert.Equal("Hello World!", responseString);
    }
}
```

#### <a name="additional-resources"></a><span data-ttu-id="d3909-149">其他资源</span><span class="sxs-lookup"><span data-stu-id="d3909-149">Additional resources</span></span>

- <span data-ttu-id="d3909-150">**Steve Smith.测试控制器** (ASP.NET Core) </span><span class="sxs-lookup"><span data-stu-id="d3909-150">**Steve Smith. Testing controllers** (ASP.NET Core) </span></span>\
    [https://docs.microsoft.com/aspnet/core/mvc/controllers/testing](/aspnet/core/mvc/controllers/testing)

- <span data-ttu-id="d3909-151">**Steve Smith.集成测试** (ASP.NET Core) </span><span class="sxs-lookup"><span data-stu-id="d3909-151">**Steve Smith. Integration testing** (ASP.NET Core) </span></span>\
    [https://docs.microsoft.com/aspnet/core/test/integration-tests](/aspnet/core/test/integration-tests)

- <span data-ttu-id="d3909-152">**在 .NET Core 中使用 dotnet test 的单元测试** </span><span class="sxs-lookup"><span data-stu-id="d3909-152">**Unit testing in .NET Core using dotnet test** </span></span>\
    [https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test](../../../core/testing/unit-testing-with-dotnet-test.md)

- <span data-ttu-id="d3909-153">**xUnit.net**。</span><span class="sxs-lookup"><span data-stu-id="d3909-153">**xUnit.net**.</span></span> <span data-ttu-id="d3909-154">官方网站。</span><span class="sxs-lookup"><span data-stu-id="d3909-154">Official site.</span></span> \
    <https://xunit.github.io/>

- <span data-ttu-id="d3909-155"> 单元测试基本信息。</span><span class="sxs-lookup"><span data-stu-id="d3909-155">**Unit Test Basics.**</span></span> \
    [https://docs.microsoft.com/visualstudio/test/unit-test-basics](/visualstudio/test/unit-test-basics)

- <span data-ttu-id="d3909-156">**Moq**。</span><span class="sxs-lookup"><span data-stu-id="d3909-156">**Moq**.</span></span> <span data-ttu-id="d3909-157">GitHub 存储库。</span><span class="sxs-lookup"><span data-stu-id="d3909-157">GitHub repo.</span></span> \
    <https://github.com/moq/moq>

- <span data-ttu-id="d3909-158">**NUnit**。</span><span class="sxs-lookup"><span data-stu-id="d3909-158">**NUnit**.</span></span> <span data-ttu-id="d3909-159">官方网站。</span><span class="sxs-lookup"><span data-stu-id="d3909-159">Official site.</span></span> \
    <https://nunit.org/>

### <a name="implementing-service-tests-on-a-multi-container-application"></a><span data-ttu-id="d3909-160">在多容器应用程序上实现服务测试</span><span class="sxs-lookup"><span data-stu-id="d3909-160">Implementing service tests on a multi-container application</span></span>

<span data-ttu-id="d3909-161">如前所述，在测试多容器应用程序时，所有微服务需要在 Docker 主机或容器群集内运行。</span><span class="sxs-lookup"><span data-stu-id="d3909-161">As noted earlier, when you test multi-container applications, all the microservices need to be running within the Docker host or container cluster.</span></span> <span data-ttu-id="d3909-162">包含有关一系列微服务的多个操作的端到端服务测试要求通过运行 docker-compose up（如果使用业务流程协调程序，则运行同等机制），在 Docker 主机中部署和启动整个应用程序。</span><span class="sxs-lookup"><span data-stu-id="d3909-162">End-to-end service tests that include multiple operations involving several microservices require you to deploy and start the whole application in the Docker host by running docker-compose up (or a comparable mechanism if you are using an orchestrator).</span></span> <span data-ttu-id="d3909-163">整个应用程序及其所有服务运行后，可以执行端到端集成和功能测试。</span><span class="sxs-lookup"><span data-stu-id="d3909-163">Once the whole application and all its services is running, you can execute end-to-end integration and functional tests.</span></span>

<span data-ttu-id="d3909-164">可以使用多种方法。</span><span class="sxs-lookup"><span data-stu-id="d3909-164">There are a few approaches you can use.</span></span> <span data-ttu-id="d3909-165">在用于部署应用程序的 docker-compose.yml 文件 中，可在解决方案级别扩展入口点，以使用 [dotnet 测试](../../../core/tools/dotnet-test.md)。</span><span class="sxs-lookup"><span data-stu-id="d3909-165">In the docker-compose.yml file that you use to deploy the application at the solution level you can expand the entry point to use [dotnet test](../../../core/tools/dotnet-test.md).</span></span> <span data-ttu-id="d3909-166">还可以使用将在设置为目标的映像中运行测试的其他 compose 文件。</span><span class="sxs-lookup"><span data-stu-id="d3909-166">You can also use another compose file that would run your tests in the image you are targeting.</span></span> <span data-ttu-id="d3909-167">通过使用包括容器上的微服务和数据库的其他集成测试 compose 文件，可确保运行测试前相关数据始终重置为其初始状态。</span><span class="sxs-lookup"><span data-stu-id="d3909-167">By using another compose file for integration tests that includes your microservices and databases on containers, you can make sure that the related data is always reset to its original state before running the tests.</span></span>

<span data-ttu-id="d3909-168">compose 应用程序运行后，如果运行 Visual Studio，可利用断点和异常。</span><span class="sxs-lookup"><span data-stu-id="d3909-168">Once the compose application is up and running, you can take advantage of breakpoints and exceptions if you are running Visual Studio.</span></span> <span data-ttu-id="d3909-169">或者可在 Azure DevOps Services 或支持 Docker 容器的其他任何 CI/CD 系统中的 CI 管道中自动运行集成测试。</span><span class="sxs-lookup"><span data-stu-id="d3909-169">Or you can run the integration tests automatically in your CI pipeline in Azure DevOps Services or any other CI/CD system that supports Docker containers.</span></span>

## <a name="testing-in-eshoponcontainers"></a><span data-ttu-id="d3909-170">在 eShopOnContainers 中进行测试</span><span class="sxs-lookup"><span data-stu-id="d3909-170">Testing in eShopOnContainers</span></span>

<span data-ttu-id="d3909-171">参考应用程序 (eShopOnContainers) 测试最近进行了重构，现在有四种类别：</span><span class="sxs-lookup"><span data-stu-id="d3909-171">The reference application (eShopOnContainers) tests were recently restructured and now there are four categories:</span></span>

1. <span data-ttu-id="d3909-172">单元  测试，只是普通的旧式常规单元测试，包含在 {MicroserviceName}.UnitTests  项目中</span><span class="sxs-lookup"><span data-stu-id="d3909-172">**Unit** tests, just plain old regular unit tests, contained in the **{MicroserviceName}.UnitTests** projects</span></span>

2. <span data-ttu-id="d3909-173">微服务功能/集成测试  ，具有涉及每个微服务的基础结构但相互独立的测试用例，包含在 {MicroserviceName}.FunctionalTests  项目中。</span><span class="sxs-lookup"><span data-stu-id="d3909-173">**Microservice functional/integration tests**, with test cases involving the infrastructure for each microservice but isolated from the others and are contained in the **{MicroserviceName}.FunctionalTests** projects.</span></span>

3. <span data-ttu-id="d3909-174">**应用程序功能/集成测试**，侧重于微服务集成，具有执行多个微服务的测试用例。</span><span class="sxs-lookup"><span data-stu-id="d3909-174">**Application functional/integration tests**, which focus on microservices integration, with test cases that exert several microservices.</span></span> <span data-ttu-id="d3909-175">这些测试位于项目 Application.FunctionalTests  中。</span><span class="sxs-lookup"><span data-stu-id="d3909-175">These tests are located in project **Application.FunctionalTests**.</span></span>

<span data-ttu-id="d3909-176">单元测试和集成测试在微服务项目中的测试文件夹中进行组织，而应用程序和负载测试是在根文件夹下单独管理的，如图 6-25 所示。</span><span class="sxs-lookup"><span data-stu-id="d3909-176">While unit and integration tests are organized in a test folder within the microservice project, application and load tests are managed separately under the root folder, as shown in Figure 6-25.</span></span>

![VS 指出解决方案中某些测试项目的屏幕截图。](./media/test-aspnet-core-services-web-apps/eshoponcontainers-test-folder-structure.png)

<span data-ttu-id="d3909-178">**图 6-25**。</span><span class="sxs-lookup"><span data-stu-id="d3909-178">**Figure 6-25**.</span></span> <span data-ttu-id="d3909-179">eShopOnContainers 中的测试文件夹结构</span><span class="sxs-lookup"><span data-stu-id="d3909-179">Test folder structure in eShopOnContainers</span></span>

<span data-ttu-id="d3909-180">微服务和应用程序功能/集成测试使用常规测试运行程序从 Visual Studio 运行，但首先需要启动所需基础结构服务（通过一组包含在解决方案测试文件夹中的 docker-compose 文件）：</span><span class="sxs-lookup"><span data-stu-id="d3909-180">Microservice and Application functional/integration tests are run from Visual Studio, using the regular tests runner, but first you need to start the required infrastructure services, by means of a set of docker-compose files contained in the solution test folder:</span></span>

<span data-ttu-id="d3909-181">docker-compose-test.yml </span><span class="sxs-lookup"><span data-stu-id="d3909-181">**docker-compose-test.yml**</span></span>

```yml
version: '3.4'

services:
  redis.data:
    image: redis:alpine
  rabbitmq:
    image: rabbitmq:3-management-alpine
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
  nosqldata:
    image: mongo
```

<span data-ttu-id="d3909-182">docker-compose-test.override.yml </span><span class="sxs-lookup"><span data-stu-id="d3909-182">**docker-compose-test.override.yml**</span></span>

```yml
version: '3.4'

services:
  redis.data:
    ports:
      - "6379:6379"
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"
  sqldata:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosqldata:
    ports:
      - "27017:27017"
```

<span data-ttu-id="d3909-183">因此，若要运行功能/集成测试，必须首先从解决方案测试文件夹运行此命令：</span><span class="sxs-lookup"><span data-stu-id="d3909-183">So, to run the functional/integration tests you must first run this command, from the solution test folder:</span></span>

```console
docker-compose -f docker-compose-test.yml -f docker-compose-test.override.yml up
```

<span data-ttu-id="d3909-184">正如你所见，这些 docker-compose 文件仅启动 Redis、RabbitMQ、SQL Server 和 MongoDB 微服务。</span><span class="sxs-lookup"><span data-stu-id="d3909-184">As you can see, these docker-compose files only start the Redis, RabbitMQ, SQL Server and MongoDB microservices.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d3909-185">其他资源</span><span class="sxs-lookup"><span data-stu-id="d3909-185">Additional resources</span></span>

- <span data-ttu-id="d3909-186">eShopOnContainers 上的单元和集成测试 </span><span class="sxs-lookup"><span data-stu-id="d3909-186">**Unit & Integration testing** on the eShopOnContainers </span></span>\
    <https://github.com/dotnet-architecture/eShopOnContainers/wiki/Unit-and-integration-testing>

- <span data-ttu-id="d3909-187">eShopOnContainers  上的负载测试 </span><span class="sxs-lookup"><span data-stu-id="d3909-187">**Load testing** on the eShopOnContainers </span></span>\
    <https://github.com/dotnet-architecture/eShopOnContainers/wiki/Load-testing>

> [!div class="step-by-step"]
> <span data-ttu-id="d3909-188">[上一页](subscribe-events.md)
> [下一页](background-tasks-with-ihostedservice.md)</span><span class="sxs-lookup"><span data-stu-id="d3909-188">[Previous](subscribe-events.md)
[Next](background-tasks-with-ihostedservice.md)</span></span>
