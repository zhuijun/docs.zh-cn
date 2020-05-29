---
title: dotnet test 命令
description: dotnet test 命令可用于在给定项目中执行单元测试。
ms.date: 04/29/2020
ms.openlocfilehash: 22b27007d26c98cff40733ef8d449ce334f87848
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802682"
---
# <a name="dotnet-test"></a><span data-ttu-id="5f3e3-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="5f3e3-103">dotnet test</span></span>

<span data-ttu-id="5f3e3-104">本文适用于： ✔️ .NET Core 2.1 SDK 及更高版本</span><span class="sxs-lookup"><span data-stu-id="5f3e3-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="5f3e3-105">“属性”</span><span class="sxs-lookup"><span data-stu-id="5f3e3-105">Name</span></span>

<span data-ttu-id="5f3e3-106">`dotnet test` - 用于执行单元测试的 .NET 测试驱动程序。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5f3e3-107">摘要</span><span class="sxs-lookup"><span data-stu-id="5f3e3-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION> | <DIRECTORY> | <DLL>]
    [-a|--test-adapter-path <PATH_TO_ADAPTER>] [--blame]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_FRIENDLY_NAME>]
    [-d|--diag <PATH_TO_DIAGNOSTICS_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER_URI/FRIENDLY_NAME>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <PATH>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a><span data-ttu-id="5f3e3-108">描述</span><span class="sxs-lookup"><span data-stu-id="5f3e3-108">Description</span></span>

<span data-ttu-id="5f3e3-109">`dotnet test` 命令用于在给定的解决方案中执行单元测试。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-109">The `dotnet test` command is used to execute unit tests in a given solution.</span></span> <span data-ttu-id="5f3e3-110">`dotnet test` 命令生成解决方案，并为解决方案中的每个测试项目运行测试主机应用程序。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-110">The `dotnet test` command builds the solution and runs a test host application for each test project in the solution.</span></span> <span data-ttu-id="5f3e3-111">测试主机使用测试框架（例如，MSTest、NUnit 或 xUnit）在给定项目中执行测试，并报告每个测试成功与否。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-111">The test host executes tests in the given project using a test framework, for example: MSTest, NUnit, or xUnit, and reports the success or failure of each test.</span></span> <span data-ttu-id="5f3e3-112">如果所有测试均成功，测试运行程序将返回 0 作为退出代码；否则将返回 1。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span>

<span data-ttu-id="5f3e3-113">对于多目标项目，将为每个目标框架运行测试。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="5f3e3-114">测试主机和单元测试框架打包为 NuGet 包，并还原为项目的普通依赖项。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-114">The test host and the unit test framework are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="5f3e3-115">测试项目使用普通 `<PackageReference>` 元素指定测试运行程序，如下方示例项目文件所示：</span><span class="sxs-lookup"><span data-stu-id="5f3e3-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

<span data-ttu-id="5f3e3-116">如果 `Microsoft.NET.Test.Sdk` 是测试主机，则 `xunit` 是测试框架。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-116">Where `Microsoft.NET.Test.Sdk` is the test host, `xunit` is the test framework.</span></span> <span data-ttu-id="5f3e3-117">另外，`xunit.runner.visualstudio` 是测试适配器，可便于 xUnit 框架与测试主机一起运行。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-117">And `xunit.runner.visualstudio` is a test adapter, which allows the xUnit framework to work with the test host.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="5f3e3-118">隐式还原</span><span class="sxs-lookup"><span data-stu-id="5f3e3-118">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="5f3e3-119">自变量</span><span class="sxs-lookup"><span data-stu-id="5f3e3-119">Arguments</span></span>

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - <span data-ttu-id="5f3e3-120">指向测试项目的路径。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-120">Path to the test project.</span></span>
  - <span data-ttu-id="5f3e3-121">解决方案的路径。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-121">Path to the solution.</span></span>
  - <span data-ttu-id="5f3e3-122">包含项目或解决方案的目录的路径。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-122">Path to a directory that contains a project or a solution.</span></span>
  - <span data-ttu-id="5f3e3-123">测试项目 .dll 文件的路径。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-123">Path to a test project *.dll* file.</span></span>

  <span data-ttu-id="5f3e3-124">如果未指定，则会在当前目录中搜索项目或解决方案。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-124">If not specified, it searches for a project or a solution in the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="5f3e3-125">选项</span><span class="sxs-lookup"><span data-stu-id="5f3e3-125">Options</span></span>

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  <span data-ttu-id="5f3e3-126">要在其中搜索其他测试适配器的目录的路径。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-126">Path to a directory to be searched for additional test adapters.</span></span> <span data-ttu-id="5f3e3-127">只检查后缀为 `.TestAdapter.dll` 的 .dll 文件。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-127">Only *.dll* files with suffix `.TestAdapter.dll` are inspected.</span></span> <span data-ttu-id="5f3e3-128">如果未指定，则会搜索测试 .dll 的目录。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-128">If not specified, the directory of the test *.dll* is searched.</span></span>

- **`--blame`**

  <span data-ttu-id="5f3e3-129">在意见模式中运行测试。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-129">Runs the tests in blame mode.</span></span> <span data-ttu-id="5f3e3-130">此选项有助于隔离导致测试主机出现故障的有问题的测试。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-130">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="5f3e3-131">检测到故障时，它会在 `TestResults/<Guid>/<Guid>_Sequence.xml` 中创建一个序列文件，用于捕获在出现故障之前运行的测试的顺序。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-131">When a crash is detected, it creates an sequence file in `TestResults/<Guid>/<Guid>_Sequence.xml` that captures the order of tests that were run before the crash.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="5f3e3-132">定义生成配置。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-132">Defines the build configuration.</span></span> <span data-ttu-id="5f3e3-133">默认值为 `Debug`，但项目配置可以替代此默认 SDK 设置。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-133">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  <span data-ttu-id="5f3e3-134">为测试运行启用数据收集器。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-134">Enables data collector for the test run.</span></span> <span data-ttu-id="5f3e3-135">有关详细信息，请参阅[监视和分析测试运行](https://aka.ms/vstest-collect)。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-135">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  <span data-ttu-id="5f3e3-136">启用测试平台的诊断模式，并将诊断消息写入到指定文件及其旁边的文件。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-136">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file and to files next to it.</span></span> <span data-ttu-id="5f3e3-137">正在记录消息的进程可确定创建了哪些文件，如测试主机日志的 `*.host_<date>.txt`，以及数据收集器日志的 `*.datacollector_<date>.txt`。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-137">The process that is logging the messages determines which files are created, such as `*.host_<date>.txt` for test host log, and `*.datacollector_<date>.txt` for data collector log.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="5f3e3-138">强制将 `dotnet` 或 .NET Framework 测试主机用于测试二进制文件。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-138">Forces the use of `dotnet` or .NET Framework test host for the test binaries.</span></span> <span data-ttu-id="5f3e3-139">此选项只确定要使用哪种类型的主机。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-139">This option only determines which type of host to use.</span></span> <span data-ttu-id="5f3e3-140">要使用的实际框架版本由测试项目的 runtimeconfig.json 决定。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-140">The actual framework version to be used is determined by the *runtimeconfig.json* of the test project.</span></span> <span data-ttu-id="5f3e3-141">如果未指定，则 [TargetFramework 程序集特性](/dotnet/api/system.runtime.versioning.targetframeworkattribute)用于确定主机的类型。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-141">When not specified, the [TargetFramework assembly attribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) is used to determine the type of host.</span></span> <span data-ttu-id="5f3e3-142">如果已从 .dll 中去除此特性，则使用的是 .NET Framework 主机。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-142">When that attribute is stripped from the *.dll*, the .NET Framework host is used.</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="5f3e3-143">使用给定表达式筛选掉当前项目中的测试。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-143">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="5f3e3-144">有关详细信息，请参阅[筛选选项详细信息](#filter-option-details)部分。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-144">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="5f3e3-145">若要获取使用选择性单元测试筛选的其他信息和示例，请参阅[运行选择性单元测试](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-145">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="5f3e3-146">打印出有关命令的简短帮助。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-146">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="5f3e3-147">允许命令停止并等待用户输入或操作。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-147">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="5f3e3-148">例如，完成身份验证。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-148">For example, to complete authentication.</span></span> <span data-ttu-id="5f3e3-149">自 .NET Core 3.0 SDK 起可用。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-149">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  <span data-ttu-id="5f3e3-150">指定测试结果记录器。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-150">Specifies a logger for test results.</span></span> <span data-ttu-id="5f3e3-151">与 MSBuild 不同，dotnet 测试不接受缩写，应使用 `-l "console;verbosity=detailed"`，而不使用 `-l "console;v=d"`。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-151">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="5f3e3-152">不在运行测试项目之前生成它。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-152">Doesn't build the test project before running it.</span></span> <span data-ttu-id="5f3e3-153">还将隐式设置 - `--no-restore` 标记。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-153">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="5f3e3-154">运行测试，而不显示 Microsoft TestPlatform 横幅。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-154">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="5f3e3-155">自 .NET Core 3.0 SDK 起可用。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-155">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="5f3e3-156">运行此命令时不执行隐式还原。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-156">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="5f3e3-157">查找要运行的二进制文件的目录。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-157">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="5f3e3-158">如果未指定，则默认路径为 `./bin/<configuration>/<framework>/`。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-158">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="5f3e3-159">对于具有多个目标框架的项目（通过 `TargetFrameworks` 属性），在指定此选项时还需要定义 `--framework`。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-159">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="5f3e3-160">`dotnet test` 始终从输出目录运行测试。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-160">`dotnet test` always runs tests from the output directory.</span></span> <span data-ttu-id="5f3e3-161">可以使用 <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> 以使用输出目录中的测试资产。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-161">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <PATH>`**

  <span data-ttu-id="5f3e3-162">用于放置测试结果的目录。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-162">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="5f3e3-163">如果指定的目录不存在，则会创建该目录。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-163">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="5f3e3-164">默认值为包含项目文件的目录中的 `TestResults`。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-164">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="5f3e3-165">要针对其测试的目标运行时。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-165">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="5f3e3-166">`.runsettings` 文件用于运行测试。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-166">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="5f3e3-167">请注意，`TargetPlatform` 元素 (x86|x64) 对 `dotnet test` 不起作用。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-167">Note that the `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="5f3e3-168">若要运行面向 x86 的测试，请安装 .NET Core 的 x86 版本。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-168">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="5f3e3-169">路径上 dotnet.exe 的位数是用于运行测试的内容。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-169">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="5f3e3-170">有关更多信息，请参见以下资源：</span><span class="sxs-lookup"><span data-stu-id="5f3e3-170">For more information, see the following resources:</span></span>

  - [<span data-ttu-id="5f3e3-171">使用 `.runsettings` 文件配置单元测试。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-171">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [<span data-ttu-id="5f3e3-172">配置测试运行</span><span class="sxs-lookup"><span data-stu-id="5f3e3-172">Configure a test run</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  <span data-ttu-id="5f3e3-173">列出当前项目中发现的所有测试。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-173">List all of the discovered tests in the current project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="5f3e3-174">设置命令的详细级别。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-174">Sets the verbosity level of the command.</span></span> <span data-ttu-id="5f3e3-175">允许使用的值为 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-175">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="5f3e3-176">默认值为 `minimal`。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-176">The default is `minimal`.</span></span> <span data-ttu-id="5f3e3-177">有关详细信息，请参阅 <xref:Microsoft.Build.Framework.LoggerVerbosity>。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-177">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="5f3e3-178">`RunSettings` 参数</span><span class="sxs-lookup"><span data-stu-id="5f3e3-178">**`RunSettings`** arguments</span></span>

 <span data-ttu-id="5f3e3-179">内联的 `RunSettings` 作为“-- ”（请注意 -- 后面有空格）后的最后一个命令行参数传递。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-179">Inline `RunSettings` are passed as the last arguments on the command line after "-- " (note the space after --).</span></span> <span data-ttu-id="5f3e3-180">内联的 `RunSettings` 被指定为 `[name]=[value]` 对。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-180">Inline `RunSettings` are specified as `[name]=[value]` pairs.</span></span> <span data-ttu-id="5f3e3-181">空格用于分隔多个 `[name]=[value]` 对。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-181">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="5f3e3-182">示例：`dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="5f3e3-182">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="5f3e3-183">有关详细信息，请参阅[通过命令行传递 RunSettings 参数](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-183">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="5f3e3-184">示例</span><span class="sxs-lookup"><span data-stu-id="5f3e3-184">Examples</span></span>

- <span data-ttu-id="5f3e3-185">运行当前目录所含项目中的测试：</span><span class="sxs-lookup"><span data-stu-id="5f3e3-185">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="5f3e3-186">运行 `test1` 项目中的测试：</span><span class="sxs-lookup"><span data-stu-id="5f3e3-186">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="5f3e3-187">在当前目录运行项目中的测试，并以 trx 格式生成测试结果文件：</span><span class="sxs-lookup"><span data-stu-id="5f3e3-187">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="5f3e3-188">在当前目录中运行项目中的测试，并将详细的测试结果记录到控制台：</span><span class="sxs-lookup"><span data-stu-id="5f3e3-188">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```
  
  - <span data-ttu-id="5f3e3-189">在当前目录下的项目中运行测试，并报告在测试主机发生故障时正在进行的测试：</span><span class="sxs-lookup"><span data-stu-id="5f3e3-189">Run the tests in the project in the current directory, and report tests that were in progress when the test host crashed:</span></span>

  ```dotnetcli
  dotnet test --blame
  ```

## <a name="filter-option-details"></a><span data-ttu-id="5f3e3-190">筛选选项详细信息</span><span class="sxs-lookup"><span data-stu-id="5f3e3-190">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="5f3e3-191">`<Expression>` 格式为 `<property><operator><value>[|&<Expression>]`。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-191">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="5f3e3-192">`<property>` 是 `Test Case` 的特性。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-192">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="5f3e3-193">下面介绍了常用单元测试框架支持的属性：</span><span class="sxs-lookup"><span data-stu-id="5f3e3-193">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="5f3e3-194">测试框架</span><span class="sxs-lookup"><span data-stu-id="5f3e3-194">Test Framework</span></span> | <span data-ttu-id="5f3e3-195">支持的属性</span><span class="sxs-lookup"><span data-stu-id="5f3e3-195">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="5f3e3-196">MSTest</span><span class="sxs-lookup"><span data-stu-id="5f3e3-196">MSTest</span></span>         | <ul><li><span data-ttu-id="5f3e3-197">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="5f3e3-197">FullyQualifiedName</span></span></li><li><span data-ttu-id="5f3e3-198">“属性”</span><span class="sxs-lookup"><span data-stu-id="5f3e3-198">Name</span></span></li><li><span data-ttu-id="5f3e3-199">ClassName</span><span class="sxs-lookup"><span data-stu-id="5f3e3-199">ClassName</span></span></li><li><span data-ttu-id="5f3e3-200">Priority</span><span class="sxs-lookup"><span data-stu-id="5f3e3-200">Priority</span></span></li><li><span data-ttu-id="5f3e3-201">TestCategory</span><span class="sxs-lookup"><span data-stu-id="5f3e3-201">TestCategory</span></span></li></ul> |
| <span data-ttu-id="5f3e3-202">xUnit</span><span class="sxs-lookup"><span data-stu-id="5f3e3-202">xUnit</span></span>          | <ul><li><span data-ttu-id="5f3e3-203">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="5f3e3-203">FullyQualifiedName</span></span></li><li><span data-ttu-id="5f3e3-204">DisplayName</span><span class="sxs-lookup"><span data-stu-id="5f3e3-204">DisplayName</span></span></li><li><span data-ttu-id="5f3e3-205">Traits</span><span class="sxs-lookup"><span data-stu-id="5f3e3-205">Traits</span></span></li></ul>                                   |

<span data-ttu-id="5f3e3-206">`<operator>` 说明了属性和值之间的关系：</span><span class="sxs-lookup"><span data-stu-id="5f3e3-206">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="5f3e3-207">运算符</span><span class="sxs-lookup"><span data-stu-id="5f3e3-207">Operator</span></span> | <span data-ttu-id="5f3e3-208">函数</span><span class="sxs-lookup"><span data-stu-id="5f3e3-208">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="5f3e3-209">完全匹配</span><span class="sxs-lookup"><span data-stu-id="5f3e3-209">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="5f3e3-210">非完全匹配</span><span class="sxs-lookup"><span data-stu-id="5f3e3-210">Not exact match</span></span> |
| `~`      | <span data-ttu-id="5f3e3-211">包含</span><span class="sxs-lookup"><span data-stu-id="5f3e3-211">Contains</span></span>        |
| `!~`     | <span data-ttu-id="5f3e3-212">不包含</span><span class="sxs-lookup"><span data-stu-id="5f3e3-212">Not contains</span></span>    |

<span data-ttu-id="5f3e3-213">`<value>` 是字符串。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-213">`<value>` is a string.</span></span> <span data-ttu-id="5f3e3-214">所有查找都不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-214">All the lookups are case insensitive.</span></span>

<span data-ttu-id="5f3e3-215">不含 `<operator>` 的表达式自动被视为 `FullyQualifiedName` 属性上的 `contains`（例如，`dotnet test --filter xyz` 与 `dotnet test --filter FullyQualifiedName~xyz` 相同）。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-215">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="5f3e3-216">表达式可与条件运算符结合使用：</span><span class="sxs-lookup"><span data-stu-id="5f3e3-216">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="5f3e3-217">运算符</span><span class="sxs-lookup"><span data-stu-id="5f3e3-217">Operator</span></span>            | <span data-ttu-id="5f3e3-218">函数</span><span class="sxs-lookup"><span data-stu-id="5f3e3-218">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="5f3e3-219">或</span><span class="sxs-lookup"><span data-stu-id="5f3e3-219">OR</span></span>       |
| `&`                 | <span data-ttu-id="5f3e3-220">AND</span><span class="sxs-lookup"><span data-stu-id="5f3e3-220">AND</span></span>      |

<span data-ttu-id="5f3e3-221">使用条件运算符时，可以用括号将表达式括起来（例如，`(Name~TestMethod1) | (Name~TestMethod2)`）。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-221">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="5f3e3-222">若要获取使用选择性单元测试筛选的其他信息和示例，请参阅[运行选择性单元测试](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="5f3e3-222">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5f3e3-223">请参阅</span><span class="sxs-lookup"><span data-stu-id="5f3e3-223">See also</span></span>

- [<span data-ttu-id="5f3e3-224">框架和目标</span><span class="sxs-lookup"><span data-stu-id="5f3e3-224">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="5f3e3-225">.NET Core 运行时标识符 (RID) 目录</span><span class="sxs-lookup"><span data-stu-id="5f3e3-225">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="5f3e3-226">通过命令行传递 runsettings 参数</span><span class="sxs-lookup"><span data-stu-id="5f3e3-226">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
